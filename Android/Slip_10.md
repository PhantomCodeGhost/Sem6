# Android Lab Solutions — Slip 10

---

# Q1: Switch and Toggle Button Demo

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Vertically centered layout with Switch and ToggleButton -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <!-- Switch widget labelled "WiFi" -->
    <Switch
        android:id="@+id/switch1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="WiFi"/>

    <!-- ToggleButton with ON/OFF labels -->
    <ToggleButton
        android:id="@+id/toggleButton1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textOn="ON"
        android:textOff="OFF"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.example.switchtoggle;

import android.os.Bundle;
import android.widget.Switch;
import android.widget.ToggleButton;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Switch s1;
    ToggleButton t1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind Switch and ToggleButton from layout
        s1 = findViewById(R.id.switch1);
        t1 = findViewById(R.id.toggleButton1);

        // Show Toast when Switch state changes
        s1.setOnCheckedChangeListener((buttonView, isChecked) -> {
            if (isChecked)
                Toast.makeText(this,"Switch ON",Toast.LENGTH_SHORT).show();
            else
                Toast.makeText(this,"Switch OFF",Toast.LENGTH_SHORT).show();
        });

        // Show Toast when ToggleButton state changes
        t1.setOnCheckedChangeListener((buttonView, isChecked) -> {
            if (isChecked)
                Toast.makeText(this,"Toggle ON",Toast.LENGTH_SHORT).show();
            else
                Toast.makeText(this,"Toggle OFF",Toast.LENGTH_SHORT).show();
        });
    }
}
```

---

# Q2: ArrayAdapter with ListView — Fruits List

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
        String[] fruits = {"Mango","Grapes","Banana","Kiwi","Strawberry"};

        // Attach ArrayAdapter using built-in simple list item layout
        lv.setAdapter(new ArrayAdapter<>(
                this,
                android.R.layout.simple_list_item_1,
                fruits
        ));
    }
}
```
