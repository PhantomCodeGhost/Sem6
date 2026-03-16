# Android Lab Solutions — Slip 15

---

# Q1: Add a Border to an Android Layout Using a Drawable Shape

## border.xml (`res/drawable/border.xml`)

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Drawable shape used as a border background for the layout -->
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">

    <!-- Stroke defines the border width and color -->
    <stroke
        android:width="28dp"
        android:color="#000000"/>

    <!-- Solid fill color inside the border -->
    <solid
        android:color="#FFFFFF"/>

    <!-- Rounded corners -->
    <corners android:radius="6dp"/>

    <!-- Inner padding for content inside the shape -->
    <padding
        android:left="8dp"
        android:top="8dp"
        android:right="8dp"
        android:bottom="8dp"/>

</shape>
```

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- ConstraintLayout with border drawable applied as background -->
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/border"
    tools:context=".MainActivity">

    <!-- Centered TextView displayed inside the bordered layout -->
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Fahhhhhhhhhhhh!!"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```

## MainActivity.java

```java
package com.phantom.mytesting;

import android.os.Bundle;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        // Apply system bar insets so content is not obscured
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
    }
}
```

---

# Q2: Simple Login Screen (No Database)

## activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Centered login form layout using TableLayout for aligned fields -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="16dp">

    <!-- Table holding Username and Password rows -->
    <TableLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:stretchColumns="1">

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Username : "
                android:textSize="18sp" />

            <!-- Username input field -->
            <EditText
                android:id="@+id/username"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Username" />
        </TableRow>

        <TableRow>

            <TextView
                android:padding="8dp"
                android:text="Password: "
                android:textSize="18sp" />

            <!-- Password input field -->
            <EditText
                android:id="@+id/password"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Password" />

        </TableRow>
    </TableLayout>

    <!-- Login button -->
    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dp"
        android:text="Button"
        />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Click To Login"
        android:gravity="center"/>
</LinearLayout>
```

## MainActivity.java

```java
package com.phantom.labsolutions;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText user, pass;
    Button button;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        // Bind input fields and button from layout
        user = findViewById(R.id.username);
        pass = findViewById(R.id.password);
        button = findViewById(R.id.btn);

        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                String usr = user.getText().toString();
                String pas = pass.getText().toString();

                // Validate hardcoded credentials (no database used)
                if (usr.equals("admin") && pas.equals("1234")) {
                    Toast.makeText(MainActivity.this, "Login Successful!", Toast.LENGTH_SHORT).show();
                } else {
                    Toast.makeText(MainActivity.this, "Invalid Credentials!", Toast.LENGTH_SHORT).show();
                }

            }
        });
    }
}
```
