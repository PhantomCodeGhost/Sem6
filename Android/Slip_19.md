# Android Lab Solutions — Slip 19

---

# Q1: Bulb ON/OFF Using Toggle Button

## activity_main.xml

```xml
<!-- Vertically centered layout with a color-box "bulb" and a ToggleButton -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <!-- Simulates a bulb: gray = OFF, yellow = ON -->
    <TextView
        android:id="@+id/txt"
        android:layout_width="150dp"
        android:layout_height="150dp"
        android:gravity="center"
        android:text="OFF"
        android:background="#808080"/>

    <!-- Toggle controls the bulb state -->
    <ToggleButton
        android:id="@+id/toggle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.graphics.Color;
import android.os.Bundle;
import android.widget.TextView;
import android.widget.ToggleButton;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    protected void onCreate(Bundle b) {
        super.onCreate(b);
        setContentView(R.layout.activity_main);

        // Bind the bulb view and toggle button
        TextView t = findViewById(R.id.txt);
        ToggleButton tg = findViewById(R.id.toggle);

        // Change background color based on toggle state: yellow = ON, gray = OFF
        tg.setOnCheckedChangeListener((v,s) ->
                t.setBackgroundColor(s ? Color.YELLOW : Color.GRAY));
    }
}
```

---

# Q2: Membership Form Using TableLayout — Pass Data to Second Activity

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Scrollable form using TableLayout for membership registration -->
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TableLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="20dp">

        <!-- Form title row -->
        <TableRow>
            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="Membership Form"
                android:textSize="22sp"
                android:textStyle="bold"
                android:gravity="center"
                android:layout_span="2"/>
        </TableRow>

        <!-- Full Name input -->
        <TableRow>
            <EditText
                android:id="@+id/etName"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_span="2"
                android:hint="Full Name"/>
        </TableRow>

        <!-- Gender label row -->
        <TableRow>
            <TextView
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="Gender"/>
        </TableRow>

        <!-- Gender RadioGroup with three options -->
        <TableRow>
            <RadioGroup
                android:id="@+id/radioGroup"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:orientation="horizontal">

                <RadioButton
                    android:id="@+id/rbMale"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="M"/>

                <RadioButton
                    android:id="@+id/rbFemale"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="F"/>

                <RadioButton
                    android:id="@+id/rbOther"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:text="Other"/>

            </RadioGroup>
        </TableRow>

        <!-- Current Weight and Height in the same row -->
        <TableRow>
            <EditText
                android:id="@+id/etWeight"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:hint="Current Weight"/>

            <EditText
                android:id="@+id/etHeight"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:hint="Height"/>
        </TableRow>

        <!-- Goal Weight and Age in the same row -->
        <TableRow>
            <EditText
                android:id="@+id/etGoal"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:hint="Goal Weight"/>

            <EditText
                android:id="@+id/etAge"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_weight="1"
                android:hint="Age"/>
        </TableRow>

        <!-- Phone number input spanning both columns -->
        <TableRow>
            <EditText
                android:id="@+id/etPhone"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_span="2"
                android:hint="Phone"/>
        </TableRow>

        <!-- Address input spanning both columns -->
        <TableRow>
            <EditText
                android:id="@+id/etAddress"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:layout_span="2"
                android:hint="Address"/>
        </TableRow>

        <!-- Membership rules acceptance checkbox -->
        <TableRow>
            <CheckBox
                android:id="@+id/checkBox"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="I accept membership rules"/>
        </TableRow>

        <!-- Submit button to proceed to the second activity -->
        <TableRow>
            <Button
                android:id="@+id/btnSubmit"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="SUBMIT"/>
        </TableRow>

    </TableLayout>
</ScrollView>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.content.Intent;
import android.os.Bundle;
import android.widget.*;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare all form input fields
    EditText etName, etWeight, etHeight, etGoal, etAge, etPhone, etAddress;
    RadioGroup radioGroup;
    CheckBox checkBox;
    Button btnSubmit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Bind all views from layout
        etName = findViewById(R.id.etName);
        etWeight = findViewById(R.id.etWeight);
        etHeight = findViewById(R.id.etHeight);
        etGoal = findViewById(R.id.etGoal);
        etAge = findViewById(R.id.etAge);
        etPhone = findViewById(R.id.etPhone);
        etAddress = findViewById(R.id.etAddress);

        radioGroup = findViewById(R.id.radioGroup);
        checkBox = findViewById(R.id.checkBox);
        btnSubmit = findViewById(R.id.btnSubmit);

        btnSubmit.setOnClickListener(v -> {

            // Read all input values
            String name = etName.getText().toString();
            String weight = etWeight.getText().toString();
            String height = etHeight.getText().toString();
            String goal = etGoal.getText().toString();
            String age = etAge.getText().toString();
            String phone = etPhone.getText().toString();
            String address = etAddress.getText().toString();

            // Resolve selected gender from RadioGroup
            int selectedId = radioGroup.getCheckedRadioButtonId();
            String gender = "Not selected";

            if(selectedId != -1){
                RadioButton rb = findViewById(selectedId);
                gender = rb.getText().toString();
            }

            // Pack all values into an Intent and launch ActivitySecond
            Intent intent = new Intent(MainActivity.this, ActivitySecond.class);

            intent.putExtra("name", name);
            intent.putExtra("gender", gender);
            intent.putExtra("weight", weight);
            intent.putExtra("height", height);
            intent.putExtra("goal", goal);
            intent.putExtra("age", age);
            intent.putExtra("phone", phone);
            intent.putExtra("address", address);

            startActivity(intent);

        });

    }
}
```

## activity_second.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Scrollable result screen displaying all membership details -->
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!-- Single TextView to display all received form data -->
    <TextView
        android:id="@+id/tvResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="20dp"
        android:textSize="18sp"/>

</ScrollView>
```

## ActivitySecond.java

```java
package com.phantom.labsolutions;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class ActivitySecond extends AppCompatActivity {

    TextView tvResult;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        tvResult = findViewById(R.id.tvResult);

        // Retrieve all extras from the Intent and format as a readable summary
        String data =
                "Name: " + getIntent().getStringExtra("name") + "\n\n" +
                        "Gender: " + getIntent().getStringExtra("gender") + "\n\n" +
                        "Weight: " + getIntent().getStringExtra("weight") + "\n\n" +
                        "Height: " + getIntent().getStringExtra("height") + "\n\n" +
                        "Goal: " + getIntent().getStringExtra("goal") + "\n\n" +
                        "Age: " + getIntent().getStringExtra("age") + "\n\n" +
                        "Phone: " + getIntent().getStringExtra("phone") + "\n\n" +
                        "Address: " + getIntent().getStringExtra("address");

        tvResult.setText(data);

    }
}
```
