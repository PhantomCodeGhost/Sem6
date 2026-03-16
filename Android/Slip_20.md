# Android Lab Solutions — Slip 20

---

# Q1: Change Image on Screen Using Toggle Button (Bulb ON/OFF)

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Centered layout with an ImageView and ToggleButton to switch bulb images -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- Displays bulb_off by default; changes to bulb_on when toggled -->
    <ImageView
        android:id="@+id/bulbImage"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:src="@drawable/bulb_off"
        />

    <!-- ToggleButton controls which bulb drawable is shown -->
    <ToggleButton
        android:id="@+id/toggleBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textOn="BulB On"
        android:textOff="BulB Off"
        />
</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.os.Bundle;
import android.widget.CompoundButton;
import android.widget.ImageView;
import android.widget.ToggleButton;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    ImageView bulbImage;
    ToggleButton toggleButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind ImageView and ToggleButton from layout
        bulbImage = findViewById(R.id.bulbImage);
        toggleButton = findViewById(R.id.toggleBtn);

        // Switch image resource based on toggle checked state
        toggleButton.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(@NonNull CompoundButton buttonView, boolean isChecked) {
                if (isChecked) {
                    bulbImage.setImageResource(R.drawable.bulb_on);
                } else {
                    bulbImage.setImageResource(R.drawable.bulb_off);
                }
            }
        });

    }
}
```

---

# Q2: ArrayAdapter with ListView — Countries List

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Full-screen ListView as root view -->
<ListView xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/listView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_marginTop="20dp"
    />
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    protected void onCreate(Bundle b) {
        super.onCreate(b);
        setContentView(R.layout.activity_main);

        // Bind ListView from layout
        ListView lv = findViewById(R.id.listView);

        // Data source for the list
        String[] countries = {"US","IND","AUS","BAN","NWZ"};

        // Attach ArrayAdapter using built-in simple list item layout
        lv.setAdapter(new ArrayAdapter<>(
                this,
                android.R.layout.simple_list_item_1,
                countries
        ));
    }
}
```
