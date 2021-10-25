# 创建自定义布局的AlertDialog
### • 创建如图所示的自定义对话框  
• 请创建一个如图所示的布局，   
• 调 用 AlertDialog.Builder 对 象 上 的 setView() 将 布 局 添 加 到AlertDialog。
## MainActivity.java
package com.example.test3_2;

import android.app.Dialog;  
import android.content.Context;  
import android.graphics.Point;  
import android.os.Bundle;  
import android.view.Display;  
import android.view.WindowManager;  
import androidx.annotation.NonNull;  
import androidx.appcompat.app.AppCompatActivity;  
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        AlertDialog alertDialog = new AlertDialog(MainActivity.this);
        alertDialog.show();
    }
}
class AlertDialog extends Dialog {
    public AlertDialog(@NonNull Context context) {
        super(context);
    }
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        setContentView(R.layout.activity_main);

        WindowManager windowManager = getWindow().getWindowManager();
        Display display = windowManager.getDefaultDisplay();
        WindowManager.LayoutParams p = getWindow().getAttributes();
        Point size = new Point();
        display.getSize(size);
        p.width = size.x;
        getWindow().setAttributes(p);
    }
}


## activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <TextView
        android:id="@+id/title"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="ANDROID APP"
        android:textSize="40dp"
        android:gravity="center"
        android:padding="10dp"
        android:textColor="@android:color/white"
        android:background="@android:color/holo_orange_light"
        app:layout_constraintTop_toTopOf="parent"
        />

    <EditText
        android:id="@+id/userName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint=" Username"
        app:layout_constraintTop_toBottomOf="@id/title"
        android:textSize="25dp"/>

    <EditText
        android:id="@+id/password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint=" Password"
        android:textSize="25dp"
        android:inputType="textPassword"
        app:layout_constraintTop_toBottomOf="@id/userName" />

    <Button
        android:id="@+id/cancel_button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Cancel"
        android:textColor="#000000"
        android:textSize="25dp"
        android:background="@android:color/white"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toLeftOf="@id/confirm_button"
        app:layout_constraintTop_toBottomOf="@id/password" />

    <Button
        android:id="@+id/confirm_button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Sign in"
        android:textColor="#000000"
        android:textSize="25dp"
        android:background="@android:color/white"
        app:layout_constraintTop_toBottomOf="@id/password"
        app:layout_constraintLeft_toRightOf="@id/cancel_button"
        app:layout_constraintRight_toRightOf="parent"/>
</androidx.constraintlayout.widget.ConstraintLayout>
