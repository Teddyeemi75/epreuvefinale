# Recherche
===============================
On constate qu par défaut, au moment de l'affichage du contenu, le texte du “Button” se transforme en majuscule (Uppercase), il faut définir android:textAllCaps="false", cela afin de s'assurer que le contenu soit affiché exactement comme dans l'original.

## Button
=================================
<Button
    android:id="@+id/button3"
    android:text="Alarm"
    android:drawableLeft="@drawable/icon_alarm"
    android:textAllCaps="false"
    ... />

1- Ici l'attribut android:gravity est utilisé afin définir quelle est la position d'affichage du texte d'un Button. Sa valeur combine des valeurs comme “Gravity.LEFT, Gravity.RIGHT, Gravity.RIGHT, Gravity.BOTTOM”

<Button
    android:id="@+id/button"
    android:gravity="center_horizontal|top"
    android:text="Text"
    ... />

2- Avec Android pouvins 4 icônes dans un Button par le biais des attributs comme android:drawableLef, android:drawableTop, android:drawableRight, android:drawableBottom, android:drawableStart, android:drawableEnd

<Button
    android:id="@+id/button"
    android:gravity="center_horizontal|top"
    android:text="Text"
    ... />

3- On définit alors le nom de la méthode qui sera convoquée lorsque l'utilisateur effectuera un clique sur "Button" avec l'attribut android.onClick.

<Button
    android:id="@+id/button"
    android:drawableLeft="@drawable/icon_bus"
    android:drawableTop="@drawable/icon_railway"
    android:drawableRight="@drawable/icon_car"
    android:drawableBottom="@drawable/icon_boat"
    android:text="Text"
    ...  />

4- On définit alors le nom de la méthode qui sera convoquée lorsque l'utilisateur effectuera un clique sur "Button" avec l'attribut android.onClick.

<Button
    android:id="@+id/button_clickMe"
    android:onClick="onClickHandler"
    android:text="Click Me"
    ... />

=======================================
5- On definit alors un fichier activity_main.xm

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout>
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:layout_marginRight="16dp"
        android:text="Number 1"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/editText_number1"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:layout_marginRight="16dp"
        android:ems="10"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:layout_marginRight="16dp"
        android:text="Number 2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText_number1" />

    <EditText
        android:id="@+id/editText_number2"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp"
        android:layout_marginRight="16dp"
        android:ems="10"
        android:inputType="number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <Button
        android:id="@+id/button_add"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp"
        android:text="Add"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editText_number2" />

<androidx.constraintlayout.widget.ConstraintLayout />

==========================================
6- En parallele en definit un fichier MainActivity.java

package org.o7planning.buttonexample;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.view.ViewConfiguration;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private EditText editTextNumber1;
    private EditText editTextNumber2;
    private Button buttonAdd;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        this.editTextNumber1 = (EditText) this.findViewById(R.id.editText_number1);
        this.editTextNumber2 = (EditText) this.findViewById(R.id.editText_number2);

        this.buttonAdd = (Button) this.findViewById(R.id.button_add);

        this.buttonAdd.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                add2Number();
            }
        });
    }

    private void add2Number()  {
        String str1 = this.editTextNumber1.getText().toString();
        String str2 = this.editTextNumber2.getText().toString();
        try {
            double value1 = Double.parseDouble(str1);
            double value2 = Double.parseDouble(str2);

            double result = value1 + value2;

            Toast.makeText(this, "Result: " + result, Toast.LENGTH_SHORT).show();
        } catch(Exception e)  {
            Toast.makeText(this, "Error: "+ e, Toast.LENGTH_SHORT).show();
        }
    }

