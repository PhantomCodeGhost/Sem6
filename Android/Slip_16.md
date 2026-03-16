# Android Lab Solutions — Slip 16

---

# Q1: Student Details Form — Display in Table on Second Activity

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Scrollable form collecting student details with text fields, radio buttons, and checkboxes -->
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:layout_marginTop="50dp"
        android:layout_marginLeft="10dp">

        <!-- Name input -->
        <EditText
            android:id="@+id/name"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Name"/>

        <!-- Surname input -->
        <EditText
            android:id="@+id/surname"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Surname "/>

        <!-- Class input -->
        <EditText
            android:id="@+id/className"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Class"/>

        <!-- Gender -->
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

        <!-- Hobbies -->
        <CheckBox
            android:id="@+id/sports"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Sports"/>

        <CheckBox
            android:id="@+id/music"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Music"/>

        <!-- Marks input -->
        <EditText
            android:id="@+id/marks"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Marks"/>

        <!-- Submit button to pass data to SecondActivity -->
        <Button
            android:id="@+id/submit"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Submit"/>

    </LinearLayout>
</ScrollView>
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.RadioGroup;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare all form input views
    EditText name, surname, className, marks;
    RadioGroup genderGroup;
    CheckBox sports, music;
    Button submit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind all views from layout
        name = findViewById(R.id.name);
        surname = findViewById(R.id.surname);
        className = findViewById(R.id.className);
        marks = findViewById(R.id.marks);
        genderGroup = findViewById(R.id.genderGroup);
        sports = findViewById(R.id.sports);
        music = findViewById(R.id.music);
        submit = findViewById(R.id.submit);

        submit.setOnClickListener(v -> {

            // Read text field values
            String n = name.getText().toString();
            String s = surname.getText().toString();
            String c = className.getText().toString();
            String m = marks.getText().toString();

            // Resolve selected gender from RadioGroup
            int id = genderGroup.getCheckedRadioButtonId();
            RadioButton r = findViewById(id);
            String gender = r.getText().toString();

            // Build hobbies string from checked checkboxes
            String hobbies = "";
            if (sports.isChecked()) hobbies += "Sports ";
            if (music.isChecked()) hobbies += "Music ";

            // Pack all data into an Intent and launch SecondActivity
            Intent intent = new Intent(MainActivity.this, SecondActivity.class);

            intent.putExtra("name", n);
            intent.putExtra("surname", s);
            intent.putExtra("class", c);
            intent.putExtra("gender", gender);
            intent.putExtra("hobbies", hobbies);
            intent.putExtra("marks", m);

            startActivity(intent);
        });
    }
}
```

## activity_second.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- TableLayout to display received student details in a structured two-column format -->
<TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="20dp">

    <!-- Each row: label column + value column -->
    <TableRow>
        <TextView android:text="Name"/>
        <TextView android:id="@+id/dName"/>
    </TableRow>

    <TableRow>
        <TextView android:text="Surname"/>
        <TextView android:id="@+id/dSurname"/>
    </TableRow>

    <TableRow>
        <TextView android:text="Class"/>
        <TextView android:id="@+id/dClass"/>
    </TableRow>

    <TableRow>
        <TextView android:text="Gender"/>
        <TextView android:id="@+id/dGender"/>
    </TableRow>

    <TableRow>
        <TextView android:text="Hobbies"/>
        <TextView android:id="@+id/dHobbies"/>
    </TableRow>

    <TableRow>
        <TextView android:text="Marks"/>
        <TextView android:id="@+id/dMarks"/>
    </TableRow>

</TableLayout>
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

        // Bind display TextViews from the table layout
        TextView name = findViewById(R.id.dName);
        TextView surname = findViewById(R.id.dSurname);
        TextView className = findViewById(R.id.dClass);
        TextView gender = findViewById(R.id.dGender);
        TextView hobbies = findViewById(R.id.dHobbies);
        TextView marks = findViewById(R.id.dMarks);

        // Populate each cell with data received via Intent
        name.setText(getIntent().getStringExtra("name"));
        surname.setText(getIntent().getStringExtra("surname"));
        className.setText(getIntent().getStringExtra("class"));
        gender.setText(getIntent().getStringExtra("gender"));
        hobbies.setText(getIntent().getStringExtra("hobbies"));
        marks.setText(getIntent().getStringExtra("marks"));
    }
}
```

---

# Q2: TimePicker Dialog — Display Selected Time on TextView

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
package com.phantom.mytesting;

import android.app.TimePickerDialog;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

import java.util.Calendar;

public class MainActivity extends AppCompatActivity {

    Button  btnTime;
    TextView  txtTime;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        btnTime = findViewById(R.id.btnTime);
        txtTime = findViewById(R.id.txtTime);

        Calendar calendar = Calendar.getInstance();

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
