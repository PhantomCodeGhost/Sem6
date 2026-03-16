# Android Lab Solutions — Slip 17

---

# Q1: Phone Call Using Intent

## AndroidManifest.xml (Permission)

```xml
<!-- Required permission to initiate phone calls -->
<uses-permission android:name="android.permission.CALL_PHONE"/>
```

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

---

# Q2: Spinner Demo

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Vertically centered layout with Spinner and a label for selected item -->
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- Spinner populated with programming language items -->
    <Spinner
        android:id="@+id/spinner"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

    <!-- Displays the currently selected item -->
    <TextView
        android:id="@+id/txtSelected"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Selected Item: "
        android:textSize="18sp"
        android:layout_marginTop="20dp"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;


import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.Spinner;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Spinner spinner;
    TextView txtSelected;

    // Data source for spinner
    String[] items = {"Java", "Python", "C++", "Android", "Kotlin"};

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        spinner = findViewById(R.id.spinner);
        txtSelected = findViewById(R.id.txtSelected);

        // Adapter
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_spinner_item, items);

        // Set built-in dropdown item layout
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);

        spinner.setAdapter(adapter);

        // Listener
        spinner.setOnItemSelectedListener(new AdapterView.OnItemSelectedListener() {

            // Update label whenever a new item is selected
            @Override
            public void onItemSelected(AdapterView<?> parent, View view, int position, long id) {

                String selectedItem = items[position];
                txtSelected.setText("Selected Item: " + selectedItem);

            }

            @Override
            public void onNothingSelected(AdapterView<?> parent) {

            }
        });
    }
}
```
