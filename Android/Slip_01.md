# Android Lab Solutions — Slip 01

---

# Q1: Activity Lifecycle Demo

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Root vertical layout centered on screen -->
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <!-- Displays the current lifecycle state -->
    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Activity Lifecycle Demo"
        android:textSize="24sp"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.os.Bundle;
import android.util.Log;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    TextView textView;
    String TAG = "ActivityLifecycle";   // Tag used for Logcat filtering

    // Called when the activity is first created
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        textView = findViewById(R.id.textView);
        textView.setText("onCreate() called");

        Log.d(TAG, "onCreate()");
    }

    // Called when the activity becomes visible to the user
    @Override
    protected void onStart() {
        super.onStart();
        textView.setText("onStart() called");
        Log.d(TAG, "onStart()");
    }

    // Called when the activity starts interacting with the user
    @Override
    protected void onResume() {
        super.onResume();
        textView.setText("onResume() called");
        Log.d(TAG, "onResume()");
    }

    // Called when the activity loses focus but is still visible
    @Override
    protected void onPause() {
        super.onPause();
        Log.d(TAG, "onPause()");
    }

    // Called when the activity is no longer visible
    @Override
    protected void onStop() {
        super.onStop();
        Log.d(TAG, "onStop()");
    }

    // Called when the activity is restarted after being stopped
    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d(TAG, "onRestart()");
    }

    // Called before the activity is destroyed
    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d(TAG, "onDestroy()");
    }
}
```

---

# Q2: DatePicker and DatePickerDialog Demo

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Vertically centered layout with date picker UI -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="20dp">

    <!-- Displays the user-selected date -->
    <TextView
        android:id="@+id/tvDate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Selected Date: "
        android:textSize="18sp"
        android:textStyle="bold"
        android:padding="10dp" />

    <!-- Opens the DatePickerDialog on click -->
    <Button
        android:id="@+id/btnPickDate"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Pick Date" />

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.app.DatePickerDialog;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.DatePicker;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

import java.util.Calendar;

public class MainActivity extends AppCompatActivity {

    private TextView tvDate;
    private Button btnPickDate;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        tvDate = findViewById(R.id.tvDate);
        btnPickDate = findViewById(R.id.btnPickDate);

        // Open DatePickerDialog when button is clicked
        btnPickDate.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showDatePickerDialog();
            }
        });
    }

    private void showDatePickerDialog() {

        // Get current date as default selection
        Calendar calendar = Calendar.getInstance();
        int year = calendar.get(Calendar.YEAR);
        int month = calendar.get(Calendar.MONTH);
        int day = calendar.get(Calendar.DAY_OF_MONTH);

        // Build and display the DatePickerDialog
        DatePickerDialog datePickerDialog = new DatePickerDialog(
                this,
                new DatePickerDialog.OnDateSetListener() {
                    @Override
                    public void onDateSet(DatePicker view, int year, int month, int dayOfMonth) {
                        // Format and display the selected date (month is 0-indexed)
                        String selectedDate = dayOfMonth + "/" + (month + 1) + "/" + year;
                        tvDate.setText("Selected Date: " + selectedDate);
                    }
                },
                year, month, day);

        datePickerDialog.show();
    }
}
```
