# Android Lab Solutions — Slip 19

---

# Q1: Bulb ON/OFF Using Toggle Button (ImageView)

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Centered layout with an ImageView bulb and a ToggleButton -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="20dp">

    <!-- ImageView displays bulb_off or bulb_on drawable based on toggle state -->
    <ImageView
        android:id="@+id/bulbImage"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:src="@drawable/bulb_off"
        />

    <!-- ToggleButton controls the bulb image state -->
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

        // Swap bulb drawable based on toggle checked state
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

# Q2: Membership Form Using TableLayout — Pass Data to Second Activity

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Scrollable membership registration form using TableLayout -->
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

        <!-- Full Name input spanning both columns -->
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

        <!-- Current Weight and Height side by side -->
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

        <!-- Goal Weight and Age side by side -->
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

        <!-- Phone input spanning both columns -->
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

        <!-- Submit button to launch ActivitySecond -->
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
