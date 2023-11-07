### UTSPemogramanMobileDoniiPerdanaSiringoringo

### Fibonacci 

Link youtube [penjelasan dari kodingan fibonaci](https://youtu.be/26vyjMCOEV0?si=o5P9LZVZHuheEj_k)

* Nama: Doni Perdana Siringoringo
* NIM: 312210687
* Kelas:TI.22.B1
  
### Fibonacci Sequence (Deret angka Fibonacci) adalah deret angka yang diperoleh dengan menjumlahkan dua angka sebelumnya:

1, 1, 2, ...
1 + 2 = 3 à 1, 1, 2, 3, ...
2 + 3 = 5 à 1, 1, 2, 3, 5, ...
3 + 5 = 8 à 1, 1, 2, 3, 5, 8, ...
Begitu seterusnya,

Berikut kodingan dari tugas berikut
Activity.main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
   -- xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/numberInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Masukkan jumlah Fibonacci"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp"
        tools:ignore="HardcodedText" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hitung Fibonacci"
        android:layout_below="@+id/numberInput"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="50dp"
        android:onClick="calculateFibonacci"
        tools:ignore="HardcodedText" />

    <Button
        android:id="@+id/btnToast"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/numberInput"
        android:layout_marginTop="50dp"
        android:layout_marginLeft="300dp"
        android:onClick="calculateFibonacci"
        android:text="Toast"
        tools:ignore="HardcodedText" />

    <TextView
        android:id="@+id/resultText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/numberInput"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="32dp" />

</RelativeLayout>

Main Activity.Java
package com.example.myapplication;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Button btnToast;
    private EditText numberInput;
    private TextView resultText;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        btnToast = findViewById(R.id.btnToast);

        numberInput = findViewById(R.id.numberInput);
        resultText = findViewById(R.id.resultText);

        btnToast.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(MainActivity.this, "Hello Toast", Toast.LENGTH_SHORT).show();

            }
        });

    }--

    --@SuppressLint("SetTextI18n")
    public void calculateFibonacci(View view) {
        String input = numberInput.getText().toString();
        if (!input.isEmpty()) {
            int n = Integer.parseInt(input);
            if (n >= 0) {
                long[] fibonacciNumbers = new long[n + 1];
                fibonacciNumbers[0] = 0;
                if (n > 0) {
                    fibonacciNumbers[1] = 1;
                }
                for (int i = 2; i <= n; i++) {
                    fibonacciNumbers[i] = fibonacciNumbers[i - 1] + fibonacciNumbers[i - 2];
                }
                resultText.setText("Deret Fibonacci pertama " + n + " bilangan adalah:\n" + arrayToString(fibonacciNumbers));
            } else {
                resultText.setText("Masukkan bilangan bulat positif.");
            }
        } else {
            resultText.setText("Masukkan jumlah bilangan Fibonacci.");
        }
    }

    private String arrayToString(long[] arr) {
        StringBuilder sb = new StringBuilder();
        for (long num : arr) {
            sb.append(num).append(", ");
        }
        sb.setLength(sb.length() - 2); // Hapus koma dan spasi terakhir
        return sb.toString();
    }
}--



