# Android Lab Solutions — Slip 07

---

# Q1: Radio Button Demo — Gender and Preference Selection

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Vertical layout with two RadioGroups and a Submit button -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- Gender -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Select Gender"/>

    <!-- RadioGroup ensures only one gender can be selected at a time -->
    <RadioGroup
        android:id="@+id/genderGroup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">

        <RadioButton
            android:id="@+id/male"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Male"/>

        <RadioButton
            android:id="@+id/female"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Female"/>

    </RadioGroup>

    <!-- Yes / No -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Do you like Android?"/>

    <!-- RadioGroup ensures only one answer can be selected at a time -->
    <RadioGroup
        android:id="@+id/yesNoGroup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">

        <RadioButton
            android:id="@+id/yes"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Yes"/>

        <RadioButton
            android:id="@+id/no"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="No"/>

    </RadioGroup>

    <!-- Submit button to display the selected values as a Toast -->
    <Button
        android:id="@+id/btnSubmit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Submit"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.os.Bundle;
import android.widget.Button;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    RadioGroup genderGroup, yesNoGroup;
    Button btnSubmit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind RadioGroups and button from layout
        genderGroup = findViewById(R.id.genderGroup);
        yesNoGroup = findViewById(R.id.yesNoGroup);
        btnSubmit = findViewById(R.id.btnSubmit);

        btnSubmit.setOnClickListener(v -> {

            // Resolve selected gender RadioButton
            int gId = genderGroup.getCheckedRadioButtonId();
            RadioButton gender = findViewById(gId);

            // Resolve selected Yes/No RadioButton
            int yId = yesNoGroup.getCheckedRadioButtonId();
            RadioButton answer = findViewById(yId);

            // Build result string and display as Toast
            String result = "Gender: " + gender.getText() + "\nAnswer: " + answer.getText();

            Toast.makeText(this, result, Toast.LENGTH_LONG).show();
        });
    }
}
```

---

# Q2: Phone Call Using Implicit Intent

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Centered layout with a phone number input and call button -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- Accepts phone number input from the user -->
    <EditText
        android:id="@+id/phone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Phone Number"
        android:inputType="phone"/>

    <!-- Triggers the dial Intent -->
    <Button
        android:id="@+id/btnCall"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Call"
        android:layout_marginTop="20dp"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText phone;
    Button btnCall;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        phone = findViewById(R.id.phone);
        btnCall = findViewById(R.id.btnCall);

        btnCall.setOnClickListener(v -> {

            // Read the phone number and build a tel: URI
            String number = phone.getText().toString();

            // ACTION_DIAL opens the dialer without requiring CALL_PHONE permission
            Intent intent = new Intent(Intent.ACTION_DIAL);
            intent.setData(Uri.parse("tel:" + number));

            startActivity(intent);
        });
    }
}
```
