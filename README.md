# AndSes12Ass2
MainActivity.java
package me.rk.andses12ass2;

import android.os.StrictMode;
import android.support.v4.app.FragmentManager;
import android.support.v4.app.FragmentTransaction;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private TextView displayTextView;
    private EditText enteredEditText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        displayTextView=(TextView)findViewById(R.id.displayText);
        enteredEditText=(EditText)findViewById(R.id.enterText);

        findViewById(R.id.submitButton).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String str=enteredEditText.getText().toString();
                Fragment_TextView fragment_textView=new Fragment_TextView(str);

                FragmentManager fragmentManager=MainActivity.this.getSupportFragmentManager();
                FragmentTransaction fragmentTransaction=fragmentManager.beginTransaction();

                fragmentTransaction.replace(R.id.tableLayout, fragment_textView);
                fragmentTransaction.commit();
            }
        });
    }

}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="me.rk.andses12ass2.MainActivity">

    <EditText
        android:id="@+id/enterText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter here !!!"
        android:textColor="@android:color/holo_orange_dark"/>

    <Button
        android:id="@+id/submitButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/enterText"
        android:text="Submit"/>

    <FrameLayout
        android:id="@+id/tableLayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_below="@id/submitButton">
    </FrameLayout>
</RelativeLayout>

