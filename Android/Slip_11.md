# Android Lab Solutions — Slip 11

---

# Q1: Change Font Size, Color and Font Family of a String

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Vertically centered layout with a styled TextView and a Button -->
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:gravity="center"
android:orientation="vertical">

    <!-- College Name -->
    <TextView
        android:id="@+id/tvCollege"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="HVDESAI College"
        android:textSize="20sp"
        android:textStyle="normal"
        android:textColor="#000000"
        android:layout_marginBottom="20dp"/>

    <!-- Push Button -->
    <Button
        android:id="@+id/btnChange"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Change Style"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.graphics.Color;
import android.graphics.Typeface;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    TextView tvCollege;
    Button btnChange;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind views from layout
        tvCollege = findViewById(R.id.tvCollege);
        btnChange = findViewById(R.id.btnChange);

        // Apply font changes when button is clicked
        btnChange.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                // Change Text Color
                tvCollege.setTextColor(Color.RED);

                // Change Text Size
                tvCollege.setTextSize(30);

                // Change Font Style
                tvCollege.setTypeface(null, Typeface.BOLD_ITALIC);
            }
        });
    }
}
```

---

# Q2: Student Details Form — Pass Data to Second Activity via Intent

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Input form with TableLayout for structured label-field rows -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="15dp"
    android:gravity="top"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Student Details"
        android:textAlignment="center"
        android:textSize="30dp" />

    <!-- Table holding all input fields -->
    <TableLayout

        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="180dp"
        android:stretchColumns="1">

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="First Name"
                android:textSize="18sp" />

            <EditText
                android:id="@+id/etFname"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter First Name" />

        </TableRow>

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Middle Name"
                android:textSize="18sp" />

            <EditText
                android:id="@+id/etMname"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Middle Name" />
        </TableRow>

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Last Name"
                android:textSize="18sp" />

            <EditText
                android:id="@+id/etLname"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Last Name" />
        </TableRow>

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Date Of Birth :"
                android:textSize="18sp" />

            <EditText
                android:id="@+id/Dob"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter DOB" />
        </TableRow>

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Address :"
                android:textSize="18sp" />

            <EditText
                android:id="@+id/etAddress"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Address" />
        </TableRow>

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Email-Id :"
                android:textSize="18sp" />

            <EditText
                android:id="@+id/Email"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Email" />

        </TableRow>

    </TableLayout>

    <!-- Submit button to navigate to SecondActivity -->
    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="30dp"
        android:layout_gravity="center"
        android:text="Submit"
        android:textSize="18dp" />

</LinearLayout>
```

## MainActivity.java

```java
public class MainActivity extends AppCompatActivity {

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        // Declare and bind all input fields
        EditText etFname, etMname, etLname, etAddress, etEmail, etDob;
        Button button;

        etFname = findViewById(R.id.etFname);
        etMname = findViewById(R.id.etMname);
        etLname = findViewById(R.id.etLname);
        etAddress = findViewById(R.id.etAddress);
        etEmail = findViewById(R.id.Email);
        etDob = findViewById(R.id.Dob);

        button = findViewById(R.id.btn);

        // On Submit: pack all field values into an Intent and start SecondActivity
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("fname",etFname.getText().toString());
                intent.putExtra("mname", etMname.getText().toString());
                intent.putExtra("lname", etLname.getText().toString());
                intent.putExtra("dob", etDob.getText().toString());
                intent.putExtra("address", etAddress.getText().toString());
                intent.putExtra("email", etEmail.getText().toString());

                startActivity(intent);
            }
        });

    }
}
```

## activity_second.xml

```xml
<!-- Display layout for the second screen -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp"
    android:gravity="center">

    <!-- Shows the student details received via Intent -->
    <TextView
        android:id="@+id/tvDisplay"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Details will appear here"
        android:textSize="18sp"
        android:layout_marginBottom="20dp"/>

    <!-- Button to trigger display of received data -->
    <Button
        android:id="@+id/btn2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Display"/>
</LinearLayout>
```

## SecondActivity.java

```java
public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);

        TextView displayText;
        displayText = findViewById(R.id.tvDisplay);
        Button button2 = findViewById(R.id.btn2);

        // Retrieve all extras passed from MainActivity
        Intent intent = getIntent();
        String fname = intent.getStringExtra("fname");
        String mname = intent.getStringExtra("mname");
        String lname = intent.getStringExtra("lname");
        String dob = intent.getStringExtra("dob");
        String email = intent.getStringExtra("email");
        String address = intent.getStringExtra("address");

        // Display all received details when Display button is clicked
        button2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                displayText.setText("First Name: " + fname + "\nMiddle Name: " + mname + "\nLast Name : " + lname + "\nDOB : " + dob + "\nAddress : " + address + "\nEmail : " + email);

            }
        });
    }
}
```
