# Android Lab Solutions — Slip 06

---

# Q1: Send "Hello!" Message from One Activity to Another Using Intent

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Centered layout with a button to send a message via Intent -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/listView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_marginTop="20dp"
    android:gravity="center"
    >

    <!-- Button to trigger Intent and pass message to SecondActivity -->
    <Button
        android:id="@+id/submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send Message"
        />
</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Button submit;

    protected void onCreate(Bundle b) {
        super.onCreate(b);
        setContentView(R.layout.activity_main);

        // Bind button from layout
        submit = findViewById(R.id.submit);

        submit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                // Send message
                intent.putExtra("msg", "Hello!");
                startActivity(intent);
            }
        });

    }
}
```

## activity_second.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Centered layout to display the received message -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/listView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_marginTop="20dp"
    android:gravity="center"
    >

    <!-- TextView to display the message received via Intent -->
    <TextView
        android:id="@+id/tv"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="40sp"
        />
</LinearLayout>
```

## SecondActivity.java

```java
package com.phantom.mytesting;

import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        TextView tv = findViewById(R.id.tv);

        // Receive message
        String message = getIntent().getStringExtra("msg");
        tv.setText(message);
    }
}
```

---

# Q2: ListView with OnClick Toast Demo

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
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    protected void onCreate(Bundle b) {
        super.onCreate(b);
        setContentView(R.layout.activity_main);

        // Bind ListView from layout
        ListView lv = findViewById(R.id.listView);

        // Data source for the list
        String[] fruits = {"Mango", "Grapes", "Banana", "Kiwi", "Strawberry"};

        // Attach ArrayAdapter using built-in simple list item layout
        lv.setAdapter(new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, fruits));

        // On Item Click — show a Toast with the selected fruit name
        lv.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {

                String selectedItem = fruits[position];

                Toast.makeText(MainActivity.this, "You selected: " + selectedItem, Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```
