## AIM:
To Show Image file sending data from one activity to another activity and Display the output for arithmetic operations using android studio.

## EQUIPMENTS REQUIRED:
Android Studio(Min. required Artic Fox)

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “workshop 2″ and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

stpe 6: Insert the image in drawable file

Step 7: Then select another empty activty.

Step 8: open google page using Implicit Intents and display factorial number using Explicit Intents in MainActivity file.

Step 9: Save and run the application.

## PROGRAM:
``` java

### activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">


    <Button
        android:id="@+id/send"
        android:layout_width="254dp"
        android:layout_height="36dp"
        android:text="send image to another activity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.579" />

    <ImageView
        android:id="@+id/img"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintBottom_toTopOf="@+id/send"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/th" />


</androidx.constraintlayout.widget.ConstraintLayout>



### MainActivity.java

package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button Send = (Button) findViewById(R.id.send);

        Send.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // add the image in putExtra
                // and send the data in next activity
                Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                String name;
                intent.putExtra( name="myimage", R.drawable.th);
                startActivity(intent);
            }
        });
    }
}




###activity_main2.xml


<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <ImageView
        android:id="@+id/img_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="This is my second acitvity"
        android:textColor="#000000"
        tools:layout_editor_absoluteX="125dp"
        tools:layout_editor_absoluteY="192dp" />


</androidx.constraintlayout.widget.ConstraintLayout>



### MainActivity2.java


package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.ImageView;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        ImageView ImageView = (ImageView) findViewById(R.id.img_second);

        // check if any value sent from previous activity
        Bundle bundle = getIntent().getExtras();

        // if bundle is not null then get the image value
        if (bundle != null) {
            int res_image = bundle.getInt("myimage");
            ImageView.setImageResource(res_image);
        }

    }
}
```
## OUTPUT:
![2](https://user-images.githubusercontent.com/78194419/165574725-02eddf45-3b9f-4157-9792-832ff863253a.jpeg)
![1](https://user-images.githubusercontent.com/78194419/165574856-0857be60-14bc-4d43-9a1c-23d590b055e6.jpeg)
