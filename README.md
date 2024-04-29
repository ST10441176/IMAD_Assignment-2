package com.example.imad_assignment2

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import androidx.appcompat.app.AppCompatActivity
import com.example.imad_assignment2.R.id.nextButton

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val next = findViewById<Button>(R.id.nextButton)
        next.setOnClickListener {
            intent = Intent(this, MainActivity3::class.java)
            startActivity(intent)
        }
    }
}

package com.example.assignment2_imadsapril

import android.os.Bundle
import android.view.animation.AlphaAnimation
import android.widget.Button
import android.widget.EditText
import android.widget.ImageView
import androidx.appcompat.app.AppCompatActivity

class Second_Page : AppCompatActivity() {

    private var petHunger = 100
    private var petCleanliness = 50
    private var petHealth = 50

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main2)

        // Get the buttons and text views
        val feedButton = findViewById<Button>(R.id.feedButton)
        val cleanButton = findViewById<Button>(R.id.washButton)
        val healthButton = findViewById<Button>(R.id.healthButton)
        val txtHunger = findViewById<EditText>(R.id.txt_hunger_value)
        val txtClean = findViewById<EditText>(R.id.txt_clean_value)
        val txtHappy = findViewById<EditText>(R.id.txt_happy)
        val petImage = findViewById<ImageView>(R.id.pet_image)

        // Set the initial text values
        txtHunger.setText(petHunger.toString())
        txtClean.setText(petCleanliness.toString())
        txtHappy.setText(petHealth.toString())

        // Handle button clicks
        feedButton.setOnClickListener {
            petHunger -= 10
            petHealth += 10
            petHunger += 5
            txtHunger.setText(petHunger.toString())
            animateImageChange(petImage, R.drawable.dog2)
        }

        cleanButton.setOnClickListener {
            petCleanliness += 10
            petHealth += 10

            txtClean.setText(petCleanliness.toString())
            animateImageChange(petImage, R.drawable.dog3)
        }

        healthButton.setText(petHealth.toString())
            petHealth += 10
            petHunger += 5
            petCleanliness -= 5
            txtHappy.setText(petHealth.toString())
            animateImageChange(petImage, R.drawable.dog4)

    }
}

    private fun animateImageChange(imageView: ImageView, newImageResource: Int) {
        val animation = AlphaAnimation(0.0f, 1.0f)
        animation.duration = 500
        animation.fillAfter = true
        imageView.startAnimation(animation)
        imageView.setImageResource(newImageResource)
    }
