DatabaseManager_For_Android
===========================

Managing Android apps' SQLite databases is tough while developing. You cannot view the tables, you don't know what is getting inserted into the tables and you can't update the data and see how your application responds to it.

What if you had a database manager like oracle sqldevelopr, mysql work bench for your application's SQLite database? This library gives you that.

With this library you can manage the database of your android app from the app itself. 

You can view, insert, delete, update the tables of your app's SQLite database from your app.

This library is a fork of https://github.com/sanathp/DatabaseManager_For_Android . It tries to make integration into your project a little bit more standard.


Setup with gradle (as submodule):
=================================

Add the library as a submodule:

```bash
$ git submodule add  https://github.com/kkalass/DatabaseManager_For_Android libraries/DatabaseManager_For_Android
```

Next, add it to your _settings.gradle_
```
include ':libraries:DatabaseManager_For_Android'
```

Then, add it to your _build.gradle_
```
dependencies {
    compile project(':libraries:DatabaseManager_For_Android')
}
```

Now you can create your own Activity as a subclass:
```java
package com.example;

import android.database.sqlite.SQLiteOpenHelper;

import de.kalass.android.databasemanager.AndroidDatabaseManager;

/**
 * Created by klas on 19.05.15.
 */
public class ExampleDatabaseManagerActivity extends AndroidDatabaseManager {
    @Override
    protected SQLiteOpenHelper newSQLiteOpenHelper() {
        // FIXME: change this to the SQLiteOpenHelper used in your app
        return new YourOpenHelper(this);
    }
}

```

After creating your own Activity class, you need to register it in your _AndroidManifest.xml_:
```
<activity android:name="com.example.ExampleDatabaseManagerActivity" 
          android:theme="@style/Theme.AppCompat.Light"/>
```

The last step of course is calling your activity. You are free to integrate this as you wish - and you are done!
 

(From original README:) You can do this anyway you wish,Below 3 are the simple ways
   to start the activity choose anyone as per your convenience.
   
(i)  add OnClickListener to a TextView. You can use the textview which is already present in your layout or add a TextView element to your xml.

```java	
    TextView tv =(TextView)findViewById(R.id.yourtextviewid);
	    	
    tv.setOnClickListener(new OnClickListener() {
        public void onClick(View v) {	
            Intent dbmanager = new Intent(getActivity(), ExampleDatabaseManagerActivity.class);
            startActivity(dbmanager);
	}
    });
```
			
(ii) add OnClickListener to a Button. You can use the button which is already present in your layout or add a 			Button element to your xml.

```    	
    Button button =(Button)findViewByID(R.id.yourbuttonid);
    button.setOnClickListener(new OnClickListener() {
        public void onClick(View v) {
            Intent dbmanager = new Intent(getActivity(), ExampleDatabaseManagerActivity.class.class);
            startActivity(dbmanager);
	}
    });
```
	
(iii) If you are using an action bar add an item  to the action bar and start activity when action bar item is 			       clicked.
	 
That's it. Now you can manage your application database directly from your app.

When app development is done remove the activity and publish your app.

With this library you can do all these :

	1) View all your tables data in tabular format
	2) Insert rows to your tables
	3) Update rows
	4) Delete rows
	5) Delete tables
	6) Drop tables
	7) Write your own custom queries and view the results. (Create statements, joins, etc)
	8) Change data in the tables and see how you application responds

In a nut shell, you can manage your app database easily.
