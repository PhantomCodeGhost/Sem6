# Android Lab Solutions — Slip 13

---

# Q1: Vertical ScrollView Demo

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- ScrollView enables vertical scrolling for content taller than the screen -->
<ScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- LinearLayout holds all scrollable child views -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Button 1"/>
        
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Button 2"/>
        <!-- Add more Button-->
        
    </LinearLayout>

</ScrollView>
```

---

# Q2: Search a Location on Google Maps Using Intent

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Layout with an input field and button to search a location on Maps -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- User enters the location name here -->
    <EditText
        android:id="@+id/location"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Location"/>

    <!-- Triggers the map search Intent -->
    <Button
        android:id="@+id/searchBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Search Location"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.example.mapsearch;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText location;
    Button searchBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        location = findViewById(R.id.location);
        searchBtn = findViewById(R.id.searchBtn);

        searchBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                // Read location input and build a geo URI
                String loc = location.getText().toString();
                Uri uri = Uri.parse("geo:0,0?q=" + loc);

                // Create an implicit Intent targeting Google Maps
                Intent intent = new Intent(Intent.ACTION_VIEW, uri);
                intent.setPackage("com.google.android.apps.maps");

                startActivity(intent);
            }
        });
    }
}
```
