# # Fragment Static / Dynamic

- Static: stay the same position  --> just type XML

  - Activity, Fragment have own lifecycles -> occurs problems

- dynamic : using java code(click --> appear)

  

### 1. main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
  ~ Copyright (C) 2017 Google Inc.
  ~
  ~ Licensed under the Apache License, Version 2.0 (the "License");
  ~ you may not use this file except in compliance with the License.
  ~ You may obtain a copy of the License at
  ~
  ~     http://www.apache.org/licenses/LICENSE-2.0
  ~
  ~ Unless required by applicable law or agreed to in writing, software
  ~ distributed under the License is distributed on an "AS IS" BASIS,
  ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  ~ See the License for the specific language governing permissions and
  ~ limitations under the License.
  -->

<android.support.constraint.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.example.android.fragmentexample.MainActivity">



    <ImageView
        android:id="@+id/imageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="@dimen/image_left_margin"
        android:layout_marginStart="@dimen/image_left_margin"
        android:layout_marginTop="@dimen/body_top_margin"
        android:scaleType="centerCrop"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/beatles_anthology_box"/>

    <TextView
        android:id="@+id/title"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginEnd="@dimen/margin_wide"
        android:layout_marginLeft="@dimen/margin_wide"
        android:layout_marginRight="@dimen/margin_wide"
        android:layout_marginStart="@dimen/margin_wide"
        android:text="@string/title1"
        android:textAppearance="@style/Base.TextAppearance.AppCompat.Medium"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintLeft_toRightOf="@+id/imageView"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="@+id/imageView"/>

    <ScrollView
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginRight="@dimen/standard_margin"
        android:layout_marginEnd="@dimen/standard_margin"
        app:layout_constraintRight_toRightOf="parent"
        android:layout_marginTop="@dimen/standard_margin"
        app:layout_constraintTop_toBottomOf="@+id/title"
        android:layout_marginLeft="0dp"
        android:layout_marginStart="0dp"
        app:layout_constraintLeft_toLeftOf="@+id/title"
        app:layout_constraintBottom_toBottomOf="parent"
        android:layout_marginBottom="@dimen/standard_margin">

        <TextView
            android:id="@+id/article"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="@string/article1"
            tools:layout_editor_absoluteX="8dp"
            tools:layout_editor_absoluteY="288dp"/>
    </ScrollView>


    <FrameLayout
        android:id="@+id/fragment_container"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        tools:layout="@layout/fragment_simple"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        >


    </FrameLayout>

    <Button
        android:id="@+id/openButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="8dp"
        android:layout_marginLeft="16dp"
        android:layout_marginStart="16dp"
        android:layout_marginTop="8dp"
        android:text="open"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView"
        app:layout_constraintVertical_bias="0.096" />

    <!--it was for static fragment-->
    <!--<fragment-->
        <!--android:id="@+id/fragment"-->
        <!--android:name="com.example.android.fragmentexample.SimpleFragment"-->
        <!--tools:layout="@layout/fragment_simple"-->
        <!--android:layout_width="0dp"-->
        <!--android:layout_height="wrap_content"-->
        <!--app:layout_constraintLeft_toLeftOf="parent"-->
        <!--app:layout_constraintRight_toRightOf="parent"-->
        <!--/>-->

</android.support.constraint.ConstraintLayout>
```

### 2. fragment.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    tools:context=".SimpleFragment"
    android:orientation="horizontal"
    android:background="@color/colorPrimary">


    <TextView
        android:id="@+id/fragment_header"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Like the article"
        android:padding="10dp"
        android:textAppearance="@style/Base.TextAppearance.AppCompat.Medium"/>

    <RadioGroup
        android:id="@+id/radioGroup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <RadioButton
            android:text="yes"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

        <RadioButton
            android:layout_marginLeft="20dp"
            android:text="no"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

    </RadioGroup>

</LinearLayout>
```

### 3. main.java

```java


import android.support.v4.app.FragmentManager;
import android.support.v4.app.FragmentTransaction;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {
    private Button mButton;
    private boolean isFragmentDisplayed = false;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        mButton= findViewById(R.id.openButton);
        mButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                if(!isFragmentDisplayed){
                    //display the fragment, add
                    displayFragment();
                }else{
                    //close fragment
                    closeFragment();
                }
            }
        });
    }

    private void displayFragment() {
        // 1. get fragment object
        SimpleFragment simpleFragment = SimpleFragment.newInstance();
        // 2. get Fragment manager  and start a transaction(add, remove)
        FragmentManager fragmentManager = getSupportFragmentManager();
        FragmentTransaction fragmentTransaction = fragmentManager.beginTransaction();
        // 3. add fragment
        // frame layout
        fragmentTransaction
                .add(R.id.fragment_container,simpleFragment)
                //add transaction to a stack that activity manages
                .addToBackStack(null)
                //do it
                .commit();
        //4. update button text
        mButton.setText("CLOSE");
        //5. set the boolean isFragmentDisplayed = true to indicate fragment is open
        isFragmentDisplayed = true;
    }
    private void closeFragment() {
        FragmentManager fragmentManager = getSupportFragmentManager();
        SimpleFragment simpleFragment = (SimpleFragment)fragmentManager.findFragmentById(R.id.fragment_container);
        if(simpleFragment !=null){
            FragmentTransaction fragmentTransaction = fragmentManager.beginTransaction();
            fragmentTransaction.remove(simpleFragment).commit();
        }
        mButton.setText("OPEN");
        isFragmentDisplayed = false;

    }
}
```

### 4. fragment.java

```java

import android.support.v4.app.Fragment;
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.TextView;


/**
 * A simple {@link Fragment} subclass.
 */
public class SimpleFragment extends Fragment {
    private static final int YES = 0;
    private static final int NO = 1;
    private static String name;

    public static SimpleFragment newInstance(){
        //Factory method
        return new SimpleFragment();
    }

    public SimpleFragment() {
        // Required empty public constructor
    }


    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        final View rootView =inflater.inflate(R.layout.fragment_simple, container, false);
       final RadioGroup radioGroup = rootView.findViewById(R.id.radioGroup);
        radioGroup.setOnCheckedChangeListener(new RadioGroup.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(RadioGroup radioGroup, int checkedId) {
//                checkedId : id of radiobutton
             RadioButton radio = radioGroup.findViewById(checkedId);
             int index = radioGroup.indexOfChild(radio);
             TextView textView = rootView.findViewById(R.id.fragment_header);

             switch (index){
                 case YES: // user chose YES
                     //update text
                     textView.setText("like!");
                     break;
                 case NO:
                     textView.setText("Thanks");
                     break;
                 default:
                     //do nothhing
                     break;
             }
            }
        });

        return rootView;
    }

}
```

