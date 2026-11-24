# Ex.No: 6 - Develop an Android Application to Add Animations to ImageView

## AIM:
To develop an Android application to add animations to an ImageView using Android Studio. The animations include Move, Blink, Fade, Clockwise, Zoom, and Slide operations.

## EQUIPMENTS REQUIRED:
- Android Studio (Latest Version)
- Java
- XML
- Android Emulator or Android Device

## ALGORITHM:

**Step 1:** Open Android Studio and click on **File → New → New Project**.

**Step 2:** Enter the application name and click Next.

**Step 3:** Select the Minimum SDK version and click Next.

**Step 4:** Select **Empty Views Activity** and click Finish.

**Step 5:** Design the user interface in the `activity_main.xml` file by adding an ImageView and buttons for different animation operations.

**Step 6:** Add the required image to the drawable folder.

**Step 7:** Implement the animation functionalities in the `MainActivity.java` file.

**Step 8:** Create and perform the following animations:
- Move Animation
- Blink Animation
- Fade Animation
- Clockwise Rotation Animation
- Zoom Animation
- Slide Animation

**Step 9:** Set click listeners for each button to perform the corresponding animation on the ImageView.

**Step 10:** Save and run the application using an Android Emulator or physical Android device.

## PROGRAM:

Program to develop an Android application to perform different animations on an ImageView using Android Studio with Java and XML.

## ANIMATIONS PERFORMED:

1. Move Animation
2. Blink Animation
3. Fade Animation
4. Clockwise Rotation Animation
5. Zoom Animation
6. Slide Animation

## TECHNOLOGIES USED:
- Android Studio
- Java
- XML

## PROGRAM
```
/*
Developed by: IYYAPPAN S
Registeration Number : 212225230108
*/
```
<hr>
<br>

Activity_main.XML
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:src="@mipmap/ic_launcher"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:layout_marginBottom="20dp" />

    <Button
        android:id="@+id/blinkBtn"
        android:text="Blink Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/rotateBtn"
        android:text="Rotate Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/fadeBtn"
        android:text="Fade Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/moveBtn"
        android:text="Move Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/zoomBtn"
        android:text="Zoom Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

    <Button
        android:id="@+id/stopBtn"
        android:text="Stop Animation"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dp" />

</LinearLayout>
```

MainActivity.java
```
package com.example.animation;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;

import com.example.animation.R;

public class MainActivity extends AppCompatActivity {

    ImageView imageView;
    Button blinkBtn, rotateBtn, fadeBtn, moveBtn, zoomBtn, stopBtn;
    Animation animation;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        imageView = findViewById(R.id.imageView);
        blinkBtn = findViewById(R.id.blinkBtn);
        rotateBtn = findViewById(R.id.rotateBtn);
        fadeBtn = findViewById(R.id.fadeBtn);
        moveBtn = findViewById(R.id.moveBtn);
        zoomBtn = findViewById(R.id.zoomBtn);
        stopBtn = findViewById(R.id.stopBtn);

        blinkBtn.setOnClickListener(v -> startAnim(R.anim.blink));
        rotateBtn.setOnClickListener(v -> startAnim(R.anim.rotate));
        fadeBtn.setOnClickListener(v -> startAnim(R.anim.fade));
        moveBtn.setOnClickListener(v -> startAnim(R.anim.move));
        zoomBtn.setOnClickListener(v -> startAnim(R.anim.zoom));

        stopBtn.setOnClickListener(v -> {
            if (animation != null) {
                imageView.clearAnimation(); // Stop animation
            }
        });
    }

    private void startAnim(int animRes) {
        animation = AnimationUtils.loadAnimation(getApplicationContext(), animRes);
        imageView.startAnimation(animation);
    }
}

```

AndroidMainfest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Animation">

        <!-- Add android:exported="true" -->
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```

Blink.xml
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="0.0"
    android:toAlpha="1.0"
    android:duration="500"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```

Rotate.xml
```
<?xml version="1.0" encoding="utf-8"?>
<rotate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromDegrees="0"
    android:toDegrees="360"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatCount="infinite" />
```
Fade.xml
```
<?xml version="1.0" encoding="utf-8"?>
<alpha xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromAlpha="1.0"
    android:toAlpha="0.0"
    android:duration="2000"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />
```
Move.xml
```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXDelta="0"
    android:toXDelta="200"
    android:fromYDelta="0"
    android:toYDelta="200"
    android:duration="1500"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```
Zoom.xml
```
<?xml version="1.0" encoding="utf-8"?>
<scale xmlns:android="http://schemas.android.com/apk/res/android"
    android:fromXScale="1.0"
    android:toXScale="1.5"
    android:fromYScale="1.0"
    android:toYScale="1.5"
    android:pivotX="50%"
    android:pivotY="50%"
    android:duration="1000"
    android:repeatMode="reverse"
    android:repeatCount="infinite" />

```

# OUTPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f118a7bd-4a6f-4cf4-9cfa-c83c204434f7" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/64d6a831-c545-4fc1-a99f-e943f3a9f1f4" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f3e109ec-cb87-44d4-aa25-62aa78abb19b" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cf4de652-85a2-4137-9200-af7185dbde90" />
<img width="1280" height="683" alt="image" src="https://github.com/user-attachments/assets/478dce26-8599-4b7a-8775-bd65e763209b" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c63995fc-969b-4119-bffa-a1e43d9e0165" />

## RESULT:
Thus, the Android application was successfully developed and executed to perform Move, Blink, Fade, Clockwise, Zoom, and Slide animations on an ImageView.
