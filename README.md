# UTS_Fibonacci

Nama        : Zahra Nurhaliza

NIM         : 312210364

Kelas       : TI.22.A4

Mata Kuliah : Premograman Mobile 1

Dosen       : Donny Maulana, S.Kom., M.M.S.I


## MainActivity.java

### ~ Package
```java
package com.hello;
```
Gunakan kode dengan hati-hati. Pelajari lebih lanjut
Package adalah cara untuk mengelompokkan kelas-kelas Java yang terkait. Dalam kasus ini, kelas `MainActivity` berada dalam `package com.hello`.


### ~ Import
```java
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.content.ContextCompat;

import android.os.Bundle;
import android.widget.TextView;
import android.view.View;
import android.widget.Toast;
import android.widget.EditText;
```
Import digunakan untuk menyertakan kelas-kelas dari package lain ke dalam program Anda. Dalam kasus ini, kelas `MainActivity` mengimport beberapa kelas dari Android SDK, yang diperlukan untuk membangun aplikasi Android.


### ~ Class
```java
public class MainActivity extends AppCompatActivity {
```
Class adalah unit dasar dari program Java. Kelas mendefinisikan apa yang bisa dilakukan oleh program Anda dan bagaimana melakukannya. Dalam kasus ini, kelas `MainActivity` mewarisi kelas `AppCompatActivity`, yang merupakan kelas dasar untuk semua aktivitas di aplikasi Android.


### ~ Variabel
```java
private long fibMinus1 = 0;
private long fibMinus2 = 1;
private long currentFib = 0;
private TextView mShowFibonacci;
private long i = 0;

private long n = 0;
private long limit = 0; // Menyimpan batas Fibonacci yang diinginkan

private EditText mLimitInput;
```
Variabel digunakan untuk menyimpan data dalam program Anda. Dalam kasus ini, kelas `MainActivity` memiliki beberapa variabel untuk menyimpan informasi tentang deret Fibonacci, batas deret Fibonacci, dan input pengguna.


### ~ Method
```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_toast);
    mShowFibonacci = (TextView) findViewById(R.id.show_count);
    mLimitInput = (EditText) findViewById(R.id.limit_input);
    updateFibonacciDisplay();
}

public void countUp(View view) {
    if (mLimitInput.getText().toString().isEmpty()) {
        Toast.makeText(this, "Enter the limit first", Toast.LENGTH_SHORT).show();
        return;
    }

    limit = Long.parseLong(mLimitInput.getText().toString());

    if (n >= limit) {
        Toast.makeText(this, "Fibonacci limit reached", Toast.LENGTH_SHORT).show();
        return; // Hentikan perhitungan jika jumlah baris Fibonacci mencapai batas
    }

    long newFib = fibMinus1 + fibMinus2;
    fibMinus2 = fibMinus1;
    fibMinus1 = newFib;
    currentFib = newFib;
    n++; // Inkrementasi jumlah baris Fibonacci

    updateFibonacciDisplay();
}

public void showFibonacci(View view) {
    Toast toast = Toast.makeText(this, R.string.fibonacci_message, Toast.LENGTH_SHORT);
    toast.show();
}

public void reset(View view) {
    currentFib = 0;
    fibMinus2 = 1;
    fibMinus1 = 0;
    limit = 0;
    n = 0;
    mLimitInput.setText(""); // Mengosongkan input
    updateFibonacciDisplay();
}

private void updateFibonacciDisplay() {
    if (mShowFibonacci != null) {
        mShowFibonacci.setText(Long.toString(currentFib));
        mShowFibonacci.setTextColor(getFibonacciColor());
    }
}

private int getFibonacciColor() {
    // Gantilah warna berdasarkan nilai Fibonacci
    i++;
    if (i % 2 == 0) {
        return ContextCompat.getColor(this, R.color.colorFibonaccipink);
    } else {
        return ContextCompat.getColor(this, R.color.colorFibonacciblue);
    }
}
```
Method adalah fungsi yang dapat dipanggil untuk melakukan tugas tertentu. Dalam kasus ini, kelas `MainActivity` memiliki beberapa method untuk menghitung deret Fibonacci, menampilkan deret


## Activity_Toast.xml

`xmlns:android="http://schemas.android.com/apk/res/android"`
`xmlns:app="http://schemas.android.com/apk/res-auto"`
`xmlns:tools="http://schemas.android.com/tools"`

Baris-baris ini mendefinisikan namespace yang akan digunakan dalam kode XML.


`android:layout_width="match_parent"`
`android:layout_height="match_parent"`

Baris-baris ini mengatur lebar dan tinggi layout menjadi sama dengan lebar dan tinggi induknya.


`tools:context=".MainActivity"`

Baris ini memberi tahu Android Studio untuk menggunakan kelas MainActivity untuk mengontrol layout ini.


1. Activity_Toast (Button_Fibonacci)
```xml
    <Button
        android:id="@+id/button_fibonacci"
        android:layout_width="190dp"
        android:layout_height="48dp"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:background="@color/colorPrimary"
        android:onClick="showFibonacci"
        android:text="@string/button_label_fibonacci"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="OnClick" />
```


2. Activity_Toast (EditText_LimitInput)
```xml
    <EditText
        android:id="@+id/limit_input"
        android:layout_width="190dp"
        android:layout_height="48dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:background="@color/colorPrimary"
        android:textAlignment="center"
        android:textColor="@color/white"
        android:hint="Enter limit"
        android:textColorHint="@color/white"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
```


3. Activity_Toast (Button_Count)
```xml
<Button
        android:id="@+id/button_count"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="4dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent" />
```


4. Activity_Toast (Button_Reset)
```xml
    <Button
        android:id="@+id/button_reset"
        android:layout_width="190dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="4dp"
        android:background="@color/colorPrimary"
        android:onClick="reset"
        android:text="Reset"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="OnClick" />
```


5. Activity_Toast (TextView_ShowCount)
```xml
    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="0"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button_fibonacci"
        app:layout_constraintVertical_bias="0.0"
        tools:ignore="RtlCompat" />
```

```xml
</androidx.constraintlayout.widget.ConstraintLayout>
```
Code di atas menunjukkan bahwa ConstraintLayout telah selesai didefinisikan.


## AndroidManifest
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.HelloAppTI22A4"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
Code untuk mendeklarasikan aktivitas utama, yaitu `MainActivity`.


## Genymotion
Ini adalah hasil RUN

- Disini saya memberi enter limit nya 8 

![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.1.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.2.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.3.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.4.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.5.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.6.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.7.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.8.png)


![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.9.png)


- Dan di saat saya pencet count lagi tidak bisa, karna enter limit hanya sampai 8

![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.10.png)


- Setelah di reset akan kembali ke awal lagi, yaitu angka 0

![image](https://github.com/ZahraNurhaliza/UTS_Fibonacci/blob/main/screenshot/ss.11.png)


# SELESAI
