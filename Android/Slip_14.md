# Android Lab Solutions — Slip 14

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

    <!-- Displays the current lifecycle callback name -->
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

# Q2: Spinner with Custom Text Size Using Styles

## activity_main.xml

```xml
<!-- Root vertical layout with a label and a styled Spinner -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp"
    >

    <!-- Label above the spinner -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Coffee?"
        android:textSize="16sp"
        android:layout_marginBottom="8dp"
        />

    <!-- Spinner using dropdown mode; adapter set programmatically -->
    <Spinner
        android:id="@+id/spinnerCoffee"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:spinnerMode="dropdown"
        />
</LinearLayout>
```

## spinneritem.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Custom TextView for the selected (collapsed) spinner item -->
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="10dp"
    android:textSize="20sp"
    android:textColor="#000000">

</TextView>
```

## spinner_dropdown_item.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Custom TextView for each item shown in the dropdown list -->
<TextView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="12dp"
    android:textSize="18sp"
    android:textColor="#000000">

</TextView>
```

## MainActivity.java

```java
package com.phantom.myslips;

import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.Spinner;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Spinner spinnerCoffee;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        // Bind Spinner from layout
        spinnerCoffee = findViewById(R.id.spinnerCoffee);

        // Data source for spinner items
        String[] coffeeList = {
                "Filter",
                "Americano",
                "Latte",
                "Espresso",
                "Cappuccino",
                "Mocha",
                "Skinny Latte",
                "Espresso Corretto"
        };

        // ArrayAdapter using custom spinner item layout
        ArrayAdapter<String>adapter = new ArrayAdapter<>(
                this, R.layout.spinneritem, coffeeList
        );

        // Set custom layout for the dropdown list
        adapter.setDropDownViewResource(R.layout.spinner_dropdown_item);
        spinnerCoffee.setAdapter(adapter);
    }
}
```
