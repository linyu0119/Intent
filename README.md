  Mainactivity.java
  
    package com.example.example5;
    import android.content.Intent;
    import android.net.Uri;
    import android.support.v7.app.AppCompatActivity;
    import android.os.Bundle;
    import android.view.View;
    import android.webkit.WebView;
    import android.webkit.WebViewClient;
    import android.widget.Button;
    import android.widget.EditText;
    import android.widget.TextView;
    public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button btn = (Button)findViewById(R.id.button);//获取按钮
        btn.setOnClickListener(new View.OnClickListener() {       //设置按钮单击事件
            @Override
            public void onClick(View v) {
                EditText et = (EditText)findViewById(R.id.editText);//获取edittext组件
                String cn = et.getText().toString();//获取edittext中填写的内容
                Intent intent = new Intent();
                intent.setAction("android.intent.action.VIEW");
                Bundle bundle = new Bundle();
                bundle.putString("address",cn);
                intent.putExtras(bundle);
                Intent chooser = Intent.createChooser(intent, "请选择以下应用打开");
                if (intent.resolveActivity(getPackageManager()) != null) {
                    startActivity(intent);
                }
            }
        });
    }
    }
  
  activity_main.xml
  
    <?xml version="1.0" encoding="utf-8"?>
    <android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <EditText
        android:id="@+id/editText"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginTop="8dp"
        android:layout_marginBottom="8dp"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.435"
        tools:layout_editor_absoluteX="0dp" />
    <Button
        android:id="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_marginBottom="392dp"
        android:text="浏览该网页"
        app:layout_constraintBottom_toBottomOf="parent"
        tools:layout_editor_absoluteX="0dp" />
    </android.support.constraint.ConstraintLayout>
  
  结果截图：https://github.com/linyu0119/Intent/blob/master/app/images/1.png
  https://github.com/linyu0119/Intent/blob/master/app/images/2.png
  https://github.com/linyu0119/Intent/blob/master/app/images/3.png

