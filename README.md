
# bottom-navigation-bar
Repository untuk memberikan tutorial bagaimana cara membuat bottom navigation bar
### Ikutin langkah-langkah di bawah untuk membuat bottom navigation bar Android Studio dengan Kotlin:

1. Buka Android Studio dan buat proyek kosong baru.
2. Tambahkan resource drawable vector sebagai ikon untuk bottom navigation bar: Klik kanan pada direktori `drawable`, pilih `New`, pilih `Vector Asset`, lalu cari ikon pertama (beri nama **home**), ikon kedua (**person**), dan ikon ketiga (**box**).
3. Enable viewBinding dengan menambahkan kode berikut pada file `build.gradle` dan sinkronisasi proyek:

 ```gradle
    android {
        ...
        viewBinding {
            enabled = true
        }
    }
 ``` 
4. Buat resource menu: Klik kanan pada direktori `res`, pilih `New` -> `Android Resource Directory`, pilih `menu` sebagai resource type, dan beri nama `menu`.
5. Buat file menu dengan nama `bottom_nav.xml` dan isinya seperti di bawah:

 ```xml
 <menu xmlns:android="http://schemas.android.com/apk/res/android">
        <item android:id="@+id/home"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:title="Home"
            android:icon="@drawable/home" />
        <item android:id="@+id/profile"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:title="Profile"
            android:icon="@drawable/person" />
        <item android:id="@+id/settings"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:title="Settings"
            android:icon="@drawable/box" />
    </menu>
  ``` 
6. Buat fragment untuk setiap menu: Klik kanan pada direktori `app`, pilih `New` -> `Fragment` -> `Fragment (Blank)`, dan beri nama masing-masing fragment **Home**, **Profile**, dan **Settings**.
7. Isi file XML untuk setiap fragment:

 - **Fragment Home:**
 ```xml
     <!-- home_fragment.xml -->
     <FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
         xmlns:tools="http://schemas.android.com/tools"
         android:layout_width="match_parent"
         android:layout_height="match_parent"
         android:background="#00BCD4"
         tools:context=".Home">
     
         <TextView
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:text="Home Fragment"
             android:textSize="20dp"
             android:layout_gravity="center"/>
     </FrameLayout>
     ``` 
 - **Fragment Profile:**
 ```xml
     <!-- profile_fragment.xml -->
     <FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
         xmlns:tools="http://schemas.android.com/tools"
         android:layout_width="match_parent"
         android:layout_height="match_parent"
         android:background="#FFC107"
         tools:context=".Profile">
     
         <TextView
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:text="Profile Fragment"
             android:textSize="20dp"
             android:layout_gravity="center"/>
     </FrameLayout>
     ``` 
 - **Fragment Settings:**
 ```xml
     <!-- settings_fragment.xml -->
     <FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
         xmlns:tools="http://schemas.android.com/tools"
         android:layout_width="match_parent"
         android:layout_height="match_parent"
         android:background="#FF9800"
         tools:context=".Settings">
     
         <TextView
             android:layout_width="wrap_content"
             android:layout_height="wrap_content"
             android:text="Settings Fragment"
             android:textSize="20dp"
             android:layout_gravity="center"/>
     </FrameLayout>
  ``` 
8. Lakukan pemrograman pada MainActivity. Ikuti kode di bawah ini:

   ```kotlin
   import androidx.appcompat.app.AppCompatActivity
   import android.os.Bundle
   import androidx.fragment.app.Fragment
   import com.example.bottomnavigation.databinding.ActivityMainBinding
   
   class MainActivity : AppCompatActivity() {
       private lateinit var binding: ActivityMainBinding
   
       override fun onCreate(savedInstanceState: Bundle?) {
           super.onCreate(savedInstanceState)
           binding = ActivityMainBinding.inflate(layoutInflater)
           setContentView(binding.root)
           replaceFragment(Home())
   
           binding.bottomNavigationView.setOnItemSelectedListener {
               when (it.itemId) {
                   R.id.home -> replaceFragment(Home())
                   R.id.profile -> replaceFragment(Profile())
                   R.id.settings -> replaceFragment(Settings())
               }
               true
           }
       }
   
       private fun replaceFragment(fragment: Fragment) {
           val fragmentManager = supportFragmentManager
           val fragmentTransaction = fragmentManager.beginTransaction()
           fragmentTransaction.replace(R.id.frame_layout, fragment)
           fragmentTransaction.commit()
       }
   }`` 

9.  Jalankan aplikasi bottom navigation bar pada perangkat masing-masing.

**Gambar Hasil**

![Home Fragment](https://raw.githubusercontent.com/rahmathidayat1203/bottom-navigation-bar/main/hasil%20akhir/home.jpg?token=GHSAT0AAAAAACKKJKAWPYISQHRLSH2HWWZAZLKDFVQ)
