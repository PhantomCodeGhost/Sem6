# Android Lab Solutions — Slip 12

---

# Q1: Send a Message from One Activity to Another Using Intent

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Single-button layout to trigger Intent-based navigation -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <!-- Button that sends a message to SecondActivity -->
    <Button
        android:id="@+id/buttonSend"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send Hello" />

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;


import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        Button buttonSend = findViewById(R.id.buttonSend);

        buttonSend.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

// Create an Intent to start SecondActivity
                Intent intent = new Intent(MainActivity.this, SecondActivity.class);

// Add a message to the Intent
                intent.putExtra("message", "Hello, This is the Second Page");

// Start SecondActivity
                startActivity(intent);

            }
        });

    }
}
```

## activity_second.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Layout for second screen; displays message received from MainActivity -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <!-- TextView to show the message passed via Intent -->
    <TextView
        android:id="@+id/textViewMessage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Message will appear here"
        android:textSize="18dp" />

</LinearLayout>
```

## SecondActivity.java

```java
package com.phantom.labsolutions;

import android.os.Bundle;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);

// Get the Intent that started this activity
        String message = getIntent().getStringExtra("message");

// Display the message in a TextView
        TextView textViewMessage = findViewById(R.id.textViewMessage);
        textViewMessage.setText(message);

    }
}
```

---

# Q2: Date and Time Picker Demo

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Layout with separate buttons and labels for Date and Time pickers -->
<LinearLayout
 xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:orientation="vertical"
 android:gravity="center"
 android:padding="20dp">

 <!-- Button to open DatePickerDialog -->
 <Button
 android:id="@+id/btnDate"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:text="Select Date" />

 <!-- Displays selected date -->
 <TextView
 android:id="@+id/txtDate"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:text="No Date Selected"
 android:textSize="18sp"
 android:layout_marginTop="10dp"/>

 <!-- Button to open TimePickerDialog -->
 <Button
 android:id="@+id/btnTime"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:text="Select Time"
 android:layout_marginTop="20dp"/>

 <!-- Displays selected time -->
 <TextView
 android:id="@+id/txtTime"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:text="No Time Selected"
 android:textSize="18sp"
 android:layout_marginTop="10dp"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.app.DatePickerDialog;
import android.app.TimePickerDialog;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

import java.util.Calendar;

public class MainActivity extends AppCompatActivity {

    Button btnDate, btnTime;
    TextView txtDate, txtTime;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        btnDate = findViewById(R.id.btnDate);
        btnTime = findViewById(R.id.btnTime);
        txtDate = findViewById(R.id.txtDate);
        txtTime = findViewById(R.id.txtTime);

        Calendar calendar = Calendar.getInstance();

        // DATE BUTTON
        btnDate.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                // Get current date as default values
                int year = calendar.get(Calendar.YEAR);
                int month = calendar.get(Calendar.MONTH);
                int day = calendar.get(Calendar.DAY_OF_MONTH);

                // Show DatePickerDialog and update TextView on selection
                DatePickerDialog datePickerDialog =
                        new DatePickerDialog(MainActivity.this,
                                (view, year1, month1, dayOfMonth) ->
                                        txtDate.setText(dayOfMonth + "/" + (month1 + 1) + "/" + year1),
                                year, month, day);

                datePickerDialog.show();
            }
        });

        // TIME BUTTON
        btnTime.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                // Get current time as default values
                int hour = calendar.get(Calendar.HOUR_OF_DAY);
                int minute = calendar.get(Calendar.MINUTE);

                // Show TimePickerDialog (24-hour format) and update TextView on selection
                TimePickerDialog timePickerDialog =
                        new TimePickerDialog(MainActivity.this,
                                (view, hourOfDay, minute1) ->
                                        txtTime.setText(hourOfDay + ":" + minute1),
                                hour, minute, true);

                timePickerDialog.show();
            }
        });
    }
}
```
