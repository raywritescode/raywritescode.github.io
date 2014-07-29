---
layout: post
title: A Study of startActivityForResult(Intent, int) 
permalink: study-of-startactivity-2
comments: True
---

## Overview

This second *A Study Of* exercise focused on passing data between two activities using startActivityForResult(Intent, int) and its associated methods.

Unlike with my previous study of startActivity(Intent), I decided to approach this study in a slightly formal manner by first creating screen mock-ups of the application and defining the UI layout formats before writing any code.

As with the previous study, I intentionally coded the UI by hand instead of using the Android GUI Layout Manager. This will be my preferred UI coding method going forward.

In the end the completed application looked very close to the application I conceptualized. A video demonstration of the completed application is available near the end of this post.

If you’re interested in following along and creating this application from scratch, all code is provided in the body of this post. Also, all source code for this study is available on [GitHub](https://github.com/raywritescode/area-51-android/tree/master/StartActivityForResultStudy).

## Requirements Phase

Before writing a line of code I’ll first define what the application will do. The screen mock-ups**[1]** shown below help you see what I have in mind.

![startActivityForResult01](/images/startActivityForResult01.png)

The application launches to a MainActivity screen that asks the user what their favorite exercise is. Also displayed is an enabled Choices button and a disabled Reset button. When the user clicks the Choices button the application opens the ExerciseActivity screen.

![startActivityForResult02](/images/startActivityForResult02.png)

In the ExerciseActivity screen the user selects one of the three exercise choices and clicks the OK button. Information about the selected exercise is returned to MainActivity.

The MainActivity screen displays the user’s favorite exercise. It also disables the Choices button and enables the Reset button.

When the user clicks the Reset button the MainActivity screen is reset to the state displayed on initial startup.

## Design Phase

The screen mock-ups are referenced to identify the attributes to use in the XML layout files for the MainActivity and ExerciseActivity screens. The layout file design diagrams**[1]** shown below will help make coding the XML layout files easier during the Implementation or Coding phase.

### MainActivity

![MainActivityDesign](/images/MainActivityDesign.png)

The layout file for MainActivity consists of a LinearLayout that fills the screen area. Centered on top of the LinearLayout is a TextView that will display either the exercise question or the exercise answer. Centered below the TextView is the Choices button followed by the Reset button.

### ExerciseActivity

![ExerciseActivity](/images/ExerciseActivity.png)

The layout file for ExerciseActivity consists of a LinearLayout that fills the screen area. Centered on the LinearLayout is a RadioGroup that contains three RadioButtons for Running, Biking, and Swimming. Centered below the RadioGroup is the OK button.

## Implementation (Coding) Phase – Create the Baseline Project Files

The first eight steps of this phase creates the StartActivityForResultsStudy project, defines the string variables used by the application, creates the XML layout files for MainActivity and ExerciseActivity, edits the auto-generated code created for MainActivity.java to a base state to prepare it for new code, creates a baseline ExerciseActivity.java file, and adds ExerciseActivity to the Android manifest file.

The project files created in these first eight steps serve as the project’s baseline state. The project’s baseline files will be uploaded to [GitHub](https://github.com/raywritescode/area-51-android/tree/master/StartActivityForResultStudy) so updates to the baseline code can easily be tracked.

### 1. Create the New StartActivityForResultStudy Project
Use the Eclipse ADT to create a new Android Application Project named StartActivityForResultStudy**[2]**.

### 2. Edit res/values/strings.xml
Add the string variables and their values that will be used by the application. String variables are used instead of hard-coding text to individual components because string variable give us the ability easily modify the application’s language text if the application will be used internationally.

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<resources>
  <string name="app_name">StartActivityForResultStudy</string>
  <string name="text_exercise_question">What is your favorite exercise?</string>
  <string name="text_favorite_exercise">Your favorite exercise is</string>
  <string name="button_choices">Choices</string>
  <string name="button_reset">Reset</string>
  <string name="button_ok">OK</string>
  <string name="radio_running">Running</string>
  <string name="radio_biking">Biking</string>
  <string name="radio_swimming">Swimming</string>
</resources>
{% endhighlight %}

### 3. Edit res/layout/activity_main.xml
Using its layout file design diagram from the Design phase as a reference, code the screen layout, text display area, and buttons for the MainActivity screen.

{% highlight xml %}
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:orientation="vertical"
  android:gravity="center" >

  <TextView
    android:id="@+id/textExerciseMessage"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/text_exercise_question"
    android:padding="24dp" />

  <Button
    android:id="@+id/buttonChoices"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/button_choices" />

  <Button
    android:id="@+id/buttonReset"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="@string/button_reset" />

</LinearLayout>
{% endhighlight %}

### 4. Add new res/layout/activity_exercise.xml file

![newActivityExercises](/images/newActivityExercises.png)

Right-click on res/layout and select New > Android XML File from the pop-up menu. In the New Android XML File wizard name the new XML file activity_exercises and click the Finish button.

### 5. Edit the res/layout/activity_exercise.xml

Using its layout file design diagram from the Design phase as a reference, create and define the screen layout, RadioGroup with Radio buttons, and the OK button for the ExerciseActivity screen.

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:orientation="vertical" 
  android:gravity="center" >

  <RadioGroup 
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
     android:orientation="vertical"
     android:padding="24dp">

     <RadioButton 
        android:id="@+id/radioRunning"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/radio_running"
        android:onClick="onRadioRunningClicked" />

     <RadioButton 
        android:id="@+id/radioBiking"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/radio_biking"
        android:onClick="onRadioBikingClicked" />

    <RadioButton 
        android:id="@+id/radioSwimming"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/radio_swimming"
        android:onClick="onRadioSwimmingClicked" />        
  </RadioGroup>

  <Button
     android:id="@+id/buttonOK"
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
     android:text="@string/button_ok" />

</LinearLayout>
{% endhighlight %}

### 6. Edit src/<package>/MainActivity.java to a baseline coding state

Clean up the auto-generated MainActivity.java file by editing it to look like the following.

{% highlight java %}
package com.raywritescode.startactivityforresultstudy;

import android.os.Bundle;
import android.app.Activity;

public class MainActivity extends Activity {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_main);
  }
}
{% endhighlight %}

### 7. Create the src/<package>ExerciseActivity.java file

In the project’s src folder right-click on the package name and select New > Class from the pop-up menu to launch the New Java Class wizard. 

Name the new class ExerciseActivity and click the Finish button to close the wizard. 

### 8. Add ExerciseActivity to the Android manifest file

In the res folder edit the AndroidManifest.xml file to add the new ExerciseActivity class to the project. The added code are lines 24 through 27 in the code listing below.

On line 25 `android:name=".ExerciseActivity"` tells us that the ExerciseActivity class is located in the package identified by the `package=` attribute shown on line 3.

{% highlight xml linenos %}
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
  package="com.raywritescode.startactivityforresultstudy"
  android:versionCode="1"
  android:versionName="1.0" >

  <uses-sdk
    android:minSdkVersion="8"
    android:targetSdkVersion="19" />

  <application
    android:allowBackup="true"
    android:icon="@drawable/ic_launcher"
    android:label="@string/app_name"
    android:theme="@style/AppTheme" >
      <activity
        android:name="com.raywritescode.startactivityforresultstudy.MainActivity"
        android:label="@string/app_name" >
        <intent-filter>
          <action android:name="android.intent.action.MAIN" />
          <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
      </activity>
      <activity
        android:name=".ExerciseActivity"
        android:label="@string/app_name" >
      </activity>
  </application>
</manifest>
{% endhighlight %}

### These eight steps in the Coding phase complete creating the project’s baseline files.
At this point I’ve uploaded the project’s baseline files to [GitHub](https://github.com/raywritescode/area-51-android/tree/master/StartActivityForResultStudy).

## Implementation (Coding) Phase – MainActivity.java

In this section, code is added to MainActivity.java to connect it the appropriate user interface (UI) components defined in its associated activity_main.xml layout file. 

Code is also added to launch the ExerciseActivity screen via the startActivityForResult() method. Finally, more code is added to handle activity result info received via the onActivityResult() method.

The code specific to the startActivityForResult() tasks are lines 56 through 60 and lines 64 to 69.

{% highlight java linenos %}
package com.raywritescode.startactivityforresultstudy;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.app.Activity;
import android.content.Intent;

public class MainActivity extends Activity {

  // The results code to pass using startActivityForResult()	
  static private final int GET_EXERCISE_REQUEST_CODE = 1;   

  // Create the object references
  private TextView exerciseText;
  private TextView favoriteExercise;
  private Button buttonChoices;
  private Button buttonReset;

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    // Connect object references to their XML layout components
    exerciseText = (TextView) findViewById(R.id.textExerciseMessage);
    favoriteExercise = (TextView) findViewById(R.id.textFavoriteExercise);
    buttonChoices = (Button) findViewById(R.id.buttonChoices);
    buttonReset = (Button) findViewById(R.id.buttonReset);        

    // Set initial values of object references
    exerciseText.setText(R.string.text_exercise_question);
    buttonReset.setEnabled(false);

    // Action to do when the Choices button is clicked
    buttonChoices.setOnClickListener(new View.OnClickListener() {

      @Override
      public void onClick(View v) {
	startExerciseActivity();
      }
    });

    // Action to do when the Reset button is clicked
    buttonReset.setOnClickListener(new View.OnClickListener() {

      @Override
      public void onClick(View v) {
	resetMainActivity();
      }
    });
  } // end onCreate()

  // Starts the ExerciseActivity
  private void startExerciseActivity() {
    Intent startExerciseActivityIntent = new Intent(this, ExerciseActivity.class);
    startActivityForResult(startExerciseActivityIntent,
      GET_EXERCISE_REQUEST_CODE);        	
  }

  // Action to do when activity result info is received
  @Override
  protected void onActivityResult(int requestCode, int resultCode, Intent data) {

    if (resultCode == RESULT_OK && requestCode == GET_EXERCISE_REQUEST_CODE) {

      // gets the returned exercise name
      String userExercise = (String) data.getStringExtra("EXERCISE"); 

      //update the MainActivity screen with the received information
      exerciseText.setText(R.string.text_favorite_exercise);

      if (userExercise.isEmpty()) {  // if user didn't select a favorite exercise
        favoriteExercise.setText(R.string.no_exercise);  // they must eat ice cream.
      } else favoriteExercise.setText(userExercise);

      buttonChoices.setEnabled(false);
      buttonReset.setEnabled(true);
    }
  }

  // Reset the MainActivity screen
  private void resetMainActivity() {
    exerciseText.setText(R.string.text_exercise_question);
    favoriteExercise.setText("");
    buttonChoices.setEnabled(true);
    buttonReset.setEnabled(false);
  }
}
{% endhighlight %}

## Implementation (Coding) Phase – ExerciseActivity.java

In this section, code is added to ExerciseActivity.java to connect it the appropriate user interface (UI) components defined in its associated activity_exercise.xml layout file. 

Code is also added to determine which exercise the user selected. It also handles the case when an exercise is not selected. 

Finally, more code is added to send the user’s exercise selection back to MainActivity.

The code specific to the startActivityForResult() tasks are lines 37 through 49 below.

{% highlight java linenos %}
package com.raywritescode.startactivityforresultstudy;

import android.app.Activity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.RadioButton;
import android.widget.RadioGroup;

public class ExerciseActivity extends Activity {

  // Create the object references
  private RadioGroup radioExerciseGroup;
  private RadioButton radioRunningButton;
  private RadioButton radioBikingButton;
  private RadioButton radioSwimmingButton;
  private Button buttonOK;

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_exercises);

    // Connect object references to their XML layout components
    radioExerciseGroup = (RadioGroup) findViewById(R.id.radioExercises);
    radioRunningButton = (RadioButton) findViewById(R.id.radioRunning);
    radioBikingButton = (RadioButton) findViewById(R.id.radioBiking);
    radioSwimmingButton = (RadioButton) findViewById(R.id.radioSwimming);
    buttonOK = (Button) findViewById(R.id.buttonOK);  

    // Action to do when the OK button is clicked
    buttonOK.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {

          // Get the user-selected exercise
          String userExercise = returnRadioGroupChoice();
          userExercise.toString();

          // Create the intent to return to MainActivity
          Intent returnedUserExerciseIntent = new Intent();
          returnedUserExerciseIntent.putExtra("EXERCISE", userExercise);

          // Set the Activity's user-selected exercise with result code of RESULT_OK
          setResult(RESULT_OK, returnedUserExerciseIntent);

          // Finish the Activity
          finish();
        }
    });

  } // end onCreate()

  // Process the Radio Group choice
  private String returnRadioGroupChoice() {

    // Get the exercise selected by the user
    switch (radioExerciseGroup.getCheckedRadioButtonId()) {
      case R.id.radioRunning:
        return radioRunningButton.getText().toString();
      case R.id.radioBiking:
        return radioBikingButton.getText().toString();
      case R.id.radioSwimming:
        return radioSwimmingButton.getText().toString();
      default:
        return "";
    }
  }
}
{% endhighlight %}

## Implementation (Coding) Phase – Updates to strings.xml

As expected, minor updates to the conceptualized application needed to be made. The first set of updates were made to strings.xml. These were discovered while coding the MainActivity and ExerciseActivity class files.

{% highlight xml linenos %}
<?xml version="1.0" encoding="utf-8"?>
<resources>

  <string name="app_name">StartActivityForResultStudy</string>
  <string name="text_exercise_question">What is your favorite exercise?</string>
  <string name="text_favorite_exercise">Your favorite exercise is...</string>
  <string name="button_choices">Choices</string>
  <string name="button_reset">Reset</string>
  <string name="button_ok">OK</string>
  <string name="radio_running">Running</string>
  <string name="radio_biking">Biking</string>
  <string name="radio_swimming">Swimming</string>
  <string name="no_exercise">Eating ice cream</string>

</resources>
{% endhighlight %}

On line 6 I changed the message “Your favorite exercise is” to “Your favorite exercise is…” because of a slight design change that now displays the user’s favorite exercise on a separate line below the message instead of after the message.

On line 13 I added a new string for the text displayed when the user does not select a favorite exercise.

## Implementation (Coding) Phase – Updates to activity_main.xml

While coding MainActivity.java to display the user’s selected exercise I learned that Android doesn’t allow (as far as I could investigate) concatenation of string resource files and String variables. 

{% highlight xml linenos %}
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" 
    android:gravity="center" > 

    <TextView
        android:id="@+id/textExerciseMessage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/text_exercise_question" />

    <TextView
        android:id="@+id/textFavoriteExercise"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:paddingBottom="16dp" />

    <Button
        android:id="@+id/buttonChoices"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/button_choices" />

     <Button
        android:id="@+id/buttonReset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/button_reset" />

</LinearLayout>
{% endhighlight %}

I decided to modify the original UI layout by displaying the user’s favorite exercise on its own line. This meant adding a new TextView component shown on lines 14 through 18.

## Implementation (Coding) Phase – Updates to activity_exercises.xml

Each of the three RadioButton components were originally coded with an `android:onClick` attribute. 

{% highlight xml linenos %}
   <RadioButton 
     android:id="@+id/radioRunning"
     android:layout_width="wrap_content"
     android:layout_height="wrap_content"
     android:text="@string/radio_running"
     android:onClick="onRadioRunningClicked" />
{% endhighlight %}

I ended up not needing the attribute so I deleted `android:onClick="onRadioRunningClicked"` (on line 6) from all the RadioButton components.

## The Completed Application in Action

This one-minute video demonstrates selecting each of the three exercise choices and what gets displayed when the user doesn’t select an exercise. Also demonstrated is resetting the MainActivity screen to its default state after the user’s exercise is displayed.

<iframe width="640" height="360" src="//www.youtube.com/embed/pLPz4OP9TFU?feature=player_embedded" frameborder="0" allowfullscreen></iframe>

If the embedded video screen is too small for you then click the Full Screen icon located at the lower-right corner of video area.

# Conclusion

This exercise gave me a much better understanding of how to use startActivityForResult() and its supporting methods to pass data between two activities. 

I also learned how to write the code needed to define RadioGroup and RadioButton layout components and how to manipulate their objects programmatically.

Creating screen mock-ups of the application and designing the UI layout files before starting the coding process helped make this project easy to build from scratch.

I’m aware that my Requirements and Design examples are loose adaptions. In a future Android study exercise I might spend extra time creating formal Requirements or Design documents.

The completed application differs slightly from what I originally conceptualized. However, the differences are minor and perhaps negligible.

-----

### Notes

1. The screen mock-ups and XML layout file design diagrams were created using Pencil Project Portable, an open source prototyping and diagramming tool. You can download the tool from [portableapps.com](http://portableapps.com/apps/graphics_pictures/pencil-project-portable).

2. Steps to create the StartActivityForResultStudy project using the New Android Application wizard.

     ![newProject01](/images/newProject01.png)

     ![newProject02](/images/newProject02.png)

     ![newProject03](/images/newProject03.png)

     ![newProject04](/images/newProject04.png)

3. My Android development environment consists of ADT (Android Developer Tools) IDE Build v22.3.0. Android platform is 4.3 using Google API level 18. Java version is 1.7.0_07.

4. The application is run on an emulated Android device configured as shown below.

     ![area51-avd](/images/area51-avd.png)
