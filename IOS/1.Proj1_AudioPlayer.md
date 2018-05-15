# # Audio Player



### # Overall flow

```Swift
0. Locate img, music files in assets folder
1. Add elements(button,slider,label) to storyboard
2. After create  @IBOutlet and @IBAction, connect by connecting lines
```



### # Whole codes and comments

```Swift
import UIKit			// for UIkit
import AVFoundation		// for Player


class ViewController: UIViewController, AVAudioPlayerDelegate{
    									//extends needed
    
    //MARK:- Properties
    var player: AVAudioPlayer!
    var timer: Timer!
    
    //MARK: IBOutlets
    @IBOutlet var playPauseButton: UIButton!
    @IBOutlet var timeLabel: UILabel!
    @IBOutlet var progressSlider: UISlider!
    
    
    //MARK:- Methods
    //MARK: Custom Method
    func initializePlayer(){
        
    // open music file, used guard-else for safe coding
        guard let soundAsset: NSDataAsset = NSDataAsset(name: "sound") else{
            print("can not play a file")
            return
        }
     
     // call music file data
        do{
            try self.player = AVAudioPlayer(data: soundAsset.data)
            self.player.delegate = self
            
        }catch let error as NSError{
            print("failed to initialize")
            print("code : \(error.code), message : \(error.localizedDescription)")
        }
        
    //arrange Slider's range from 0 to duration of music    
        self.progressSlider.maximumValue = Float(self.player.duration)
        self.progressSlider.minimumValue = 0
        self.progressSlider.value = Float(self.player.currentTime)
    }
    
    // MARK: Life Cycle
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view, typically from a nib.
        // Called after the view has been loaded.
        self.initializePlayer()
        
    }
    
    //    override func didReceiveMemoryWarning() {
    //        super.didReceiveMemoryWarning()
    //        // Dispose of any resources that can be recreated.
    //    }
    
    // MARK: IBActions
    @IBAction func touchUpPlayButton(_ sender: UIButton){
        sender.isSelected = !sender.isSelected
        	// BOOL x; 
        	// BOOL y; 
			// y = !x; // place in y the "not" of the value in x
        
        // isSelected(stopped,||)
        if sender.isSelected{
            self.player?.play()
            // var player: AVAudioPlayer!(defined above)
            // play : predefined method
        } else {
            self.player?.pause()
        }
        
        if sender.isSelected{
            //replay
            self.makeAndFireTimer()
        } else{
            //stop
            self.invalidateTimer()
        }
    }
    
    func makeAndFireTimer() {
        //  var timer: Timer!(defined above)
        self.timer = Timer.scheduledTimer(withTimeInterval: 0.01, repeats: true, block: { [unowned self] (timer: Timer) in
            
            if self.progressSlider.isTracking { return }
            
            self.updateTimeLabelText(time: self.player.currentTime)
            self.progressSlider.value = Float(self.player.currentTime)
        })
        self.timer.fire()
    }
    
    func invalidateTimer(){
        self.timer.invalidate()
        self.timer = nil
        
    }
    
    func updateTimeLabelText(time: TimeInterval) {
        let minute: Int = Int(time / 60)
        let second: Int = Int(time.truncatingRemainder(dividingBy: 60))
        let milisecond: Int = Int(time.truncatingRemainder(dividingBy: 1) * 100)
        
        let timeText: String = String(format: "%02ld:%02ld:%02ld", minute, second, milisecond)
        
        self.timeLabel.text = timeText
    }
    
    @IBAction func sliderValueChanged(_ sender: UISlider) {
        //        self.updateTimeLabelText(time: TimeInterval(sender.value))
        if sender.isTracking { return }
        self.player.currentTime = TimeInterval(sender.value)
    }
    
    
    
    //MARK AVAudioPlayerDelegate
    func audioPlayerDecodeErrorDidOccur(_ player: AVAudioPlayer, error: Error?){
        guard let error: Error = error else{
            print("audio player decode error")
            return
        }
        
        let message: String
        message = "audio player error \(error.localizedDescription)"
        
        let alert: UIAlertController = UIAlertController(title: "alert", message: message, preferredStyle: UIAlertControllerStyle.alert)
        let okAction: UIAlertAction = UIAlertAction(title: "ok", style: UIAlertActionStyle.default) { (action: UIAlertAction) -> Void in
            self.dismiss(animated: true, completion: nil)
        }
        alert.addAction(okAction)
        self.present(alert, animated: true, completion: nil)
        
        
    }
    
    func audioPlayerDidFinishPlaying(_ player: AVAudioPlayer, successfully flag: Bool) {
        self.playPauseButton.isSelected = false
        self.progressSlider.value = 0
        self.updateTimeLabelText(time: 0)
        self.invalidateTimer()
    }
    
}

```

