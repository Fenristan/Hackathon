package com.example.ona.myapplication;

import android.content.Context;
import android.graphics.Bitmap;
import android.graphics.BitmapFactory;
import android.graphics.Color;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import java.io.File;

import static java.lang.Math.max;
import static java.lang.Math.min;


public class Main extends AppCompatActivity
{

    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void fotka(View v)       //funkce pro zjištění RGB hodnot pixelů mapy
    {
        int MapOut;

        EditText e1 = (EditText)findViewById(R.id.editText);
        EditText e2 = (EditText)findViewById(R.id.editText2);

        if(e1.getText().toString().length() == 0 || e2.getText().toString().length() == 0)  //ošetří hodnoty mimo betmapu
            Toast.makeText(this, "povinné", Toast.LENGTH_SHORT).show();
        else {

            float x = Float.parseFloat(e1.getText().toString());
            float y = Float.parseFloat(e2.getText().toString());

            Bitmap bitmap;

            bitmap = BitmapFactory.decodeResource(getResources(), R.drawable.heatmap);

            x -= 48.55181f;
            x /= 2.503897f;

            y -= 12.09081f;
            y /= 6.768442f;
            y = 1 - y;

            if (x < 0 || x > 1 || y < 0 || y > 1) {
                Toast.makeText(this, "Mimo oblast ČR", Toast.LENGTH_SHORT).show();  //ošetří místa na mapě mimo čr

            } else {

                //TextView t1 = (TextView) findViewById(R.id.txt);

                int color = bitmap.getPixel((int) (x * bitmap.getWidth()), (int) (y * bitmap.getHeight()));  //vzorec pro scaling

                int red = Color.red(color);//(color & 0x00ff0000) >> 16;
                int green = Color.green(color);//(color & 0x0000ff00) >> 8;
                int blue = Color.blue(color);//color & 0x000000ff;


                if (red >= 250 && red <= 255 && blue >= 250 && blue <= 255 && green >= 250 && green <= 255)  //nalezne barvu na heatmapě
                {
                    Toast.makeText(this, "Mimo oblast ČR", Toast.LENGTH_SHORT).show();

                } else {
                    if (red >= 170 && red <= 180 && green >= 0 && green <= 5) {
                        MapOut = 1300;
                    } else if (red >= 195 && red <= 205 && green >= 0 && green <= 5) {
                        MapOut = 1220;
                    } else if (red >= 235 && red <= 245 && green >= 95 && green <= 103) {
                        MapOut = 1184;
                    } else if (red >= 250 && red <= 255 && green >= 135 && green <= 145) {
                        MapOut = 1156;
                    } else if (red >= 250 && red <= 255 && green >= 175 && green <= 183) {
                        MapOut = 1128;
                    } else if (red >= 250 && red <= 255 && green >= 198 && green <= 205) {
                        MapOut = 1100;
                    } else {
                        MapOut = 1070;
                    }
                    //t1.setText(Integer.toString((MapOut)));
                }
            }
        }

    }
}
