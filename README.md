# Campsite-Commander
package com.example.campsitecommander

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {

    // Global arrays to store your gear data
    companion object {
        val itemArray = ArrayList<String>()
        val categoryArray = ArrayList<String>()
        val quantityArray = ArrayList<Int>()
        val commentsArray = ArrayList<String>()
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.mainactivity)

        // Find the "Enter" button by its correct ID
        val btnEnter = findViewById<Button>(R.id.btnEnter)

        btnEnter.setOnClickListener {
            // Transition to the activity_detailed_view_screen.xml when the button is clicked
            val intent = Intent(this, DetailedViewScreen::class.java)
            startActivity(intent)
        }

        btnEnter.setOnClickListener {
            // Transition to DetailedViewScreen when the button is clicked
            val intent = Intent(this, MainScreen::class.java)
            startActivity(intent)
        }

        // Apply window insets to the root layout for edge-to-edge support
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main_root)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }
    }
}
