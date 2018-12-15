# Unnnn
DBMS

ANDROID STUDIO

MAIN ACTIVITY

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">


    <Button
        android:id="@+id/login"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:text="login" />

    <Button
        android:id="@+id/register"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="154dp"
        android:text="Account Register" />

    <EditText
        android:id="@+id/editpass"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginTop="138dp"
        android:ems="10"
        android:hint="Enetr user Password"
        android:inputType="textPersonName|textPassword" />

    <EditText
        android:id="@+id/editname"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginTop="54dp"
        android:ems="10"
        android:hint="Enter User Name"
        android:inputType="textPersonName" />
</RelativeLayout>




List


<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".ListActivity">

    <ListView
        android:id="@+id/list"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
</RelativeLayout>




Register


<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".RegActivity">

    <EditText
        android:id="@+id/editregname"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginTop="63dp"
        android:ems="10"
        android:hint="Enter User User Name"
        android:inputType="textPersonName" />

    <EditText
        android:id="@+id/editregemail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginTop="133dp"
        android:ems="10"
        android:hint="Enter Your Email"
        android:inputType="textPersonName" />

    <EditText
        android:id="@+id/editregpass"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginTop="209dp"
        android:ems="10"
        android:hint="Enter your Password"
        android:inputType="textPassword" />

    <Button
        android:id="@+id/regbutton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_centerHorizontal="true"
        android:layout_marginBottom="174dp"
        android:text="Regester" />

    <EditText
        android:id="@+id/phone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_centerVertical="true"
        android:ems="10"
        android:hint="Enter Phone Number"
        android:inputType="textPersonName" />
</RelativeLayout>




MAIN ACTIVITY

package com.example.shank.gmailforexam;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    EditText editname,editpass;
    Button login,register;

    DatabaseHelper Db;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editname=(EditText)findViewById(R.id.editname);
        editpass=(EditText)findViewById(R.id.editpass);
        login=(Button)findViewById(R.id.login);
        register=(Button)findViewById(R.id.register);

        Db=new DatabaseHelper(this);



        logmethod();
        regmethod();
    }

    public void logmethod()
    {
        login.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String name2=editname.getText().toString();
                String pass2=editpass.getText().toString();


                boolean cheecked=Db.check(name2,pass2);
                if(cheecked==true)
                {
                    Intent i=new Intent(getApplicationContext(),ListActivity.class);
                    startActivity(i);

                    Toast.makeText(MainActivity.this, "Log In", Toast.LENGTH_SHORT).show();


                }
                else
                {
                    Toast.makeText(MainActivity.this, "Log In Failed", Toast.LENGTH_SHORT).show();
                }
            }
        });
    }

    public void regmethod()
    {
        register.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent i=new Intent(getApplicationContext(),RegActivity.class);
                startActivity(i);
            }
        });
    }
}





LIST ACTIVITY


package com.example.shank.gmailforexam;

import android.database.Cursor;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.ListAdapter;
import android.widget.ListView;

import java.util.ArrayList;

public class ListActivity extends AppCompatActivity {
    ListView list;
    DatabaseHelper db;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_list);

        list=(ListView)findViewById(R.id.list);
        db=new DatabaseHelper(this);

        ArrayList<String> thelist=new ArrayList<>();
        Cursor res=db.getAllData();

        while ((res.moveToNext()))
        {
            thelist.add(res.getString(0)+"\n"+res.getString(1)+"\n"+res.getString(2)+"\n"+res.getString(3)+"\n"+res.getString(4));
            ListAdapter listAdapter=new ArrayAdapter<String>(this,android.R.layout.simple_list_item_1,thelist);
            list.setAdapter(listAdapter);
        }
    }
}



DATA BASE


package com.example.shank.gmailforexam;

import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {

    public static final String DARABASE_NAME="login.db";
    public static final String TABLE_NAME="login_table";
    public static final String COL_1="id";
    public static final String COL_2="name";
    public static final String COL_3="email";
    public static final String COL_4="pass";
    public static final String COL_5="phone";

    public DatabaseHelper(Context context) {
        super(context, DARABASE_NAME, null,1);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {

        db.execSQL("create table "+TABLE_NAME+"(id integer primary key autoincrement,name text,email text,pass text,phone text)");

    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {

    }

    public boolean insertData(String name,String email,String pass,String phone)
    {
        SQLiteDatabase db =this.getWritableDatabase();
        ContentValues obj=new ContentValues();
        obj.put(COL_2,name);
        obj.put(COL_3,email);
        obj.put(COL_4,pass);
        obj.put(COL_5,phone);

        db.insert(TABLE_NAME,null,obj);
        return  true;
    }

    public boolean check(String name,String pass)
    {
        SQLiteDatabase db =this.getReadableDatabase();
        Cursor cur = db.rawQuery("select * from login_table where name=? and pass=?",new String[]{name,pass});
        if(cur.getCount()>=1)
        {
            return  true;
        }
        else
        {
            return  false;
        }
    }

    public Cursor getAllData() {
        SQLiteDatabase db=this.getWritableDatabase();
        Cursor res=db.rawQuery("select * from "+TABLE_NAME,null);
        return res;
    }
}




REGISTER ACTIVITy


package com.example.shank.gmailforexam;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class RegActivity extends AppCompatActivity {
    EditText editregname,editregemail,editregpass,phone;
    Button regbutton;

    DatabaseHelper myDb;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_reg);

        editregemail=(EditText)findViewById(R.id.editregemail);
        editregname=(EditText)findViewById(R.id.editregname);
        editregpass=(EditText)findViewById(R.id.editregpass);
        phone=(EditText)findViewById(R.id.phone);
        regbutton=(Button)findViewById(R.id.regbutton);

        myDb=new DatabaseHelper(this);

        registerMethod();
    }

    public void registerMethod()
    {
        regbutton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String name1=editregname.getText().toString();
                String email1=editregemail.getText().toString();
                String pass1=editregpass.getText().toString();
                String phone1=phone.getText().toString();

                editregname.getText().clear();
                editregemail.getText().clear();
                editregpass.getText().clear();
                phone.getText().clear();

                boolean data=myDb.insertData(name1,email1,pass1,phone1);

                if(data==true)
                {
                    Toast.makeText(RegActivity.this, "User Registered", Toast.LENGTH_SHORT).show();
                }
                else
                {
                    Toast.makeText(RegActivity.this, "User Not Registered", Toast.LENGTH_SHORT).show();


                }
            }
        });
    }
}



DBMS SQL QUORIES


                                                                                   TOAD

Step 1:TO CREATE DATABASE

create Database Shankardb;


Step 2:TO DELETE DATABASE

drop Database Shankardb;


Step 3:TO CREATE DATABASE TABLE

create Table Shankartb(
id int(10) not null AUTO_INCREMENT,
name varchar(10) not null,
phone bigint(20) not null,
primary key(id)
);


Step 4:TO INSERT DATA

insert into shankartb(id,name,phone)values(1,'Shankar','111111111');
insert into shankartb(id,name,phone)values(2,'Ajeet','2222222222');
insert into shankartb(id,name,phone)values(3,'Abinay','33333333');
insert into shankartb(id,name,phone)values(4,'Akash','444444444');
insert into shankartb(id,name,phone)values(5,'Nischay','555555555');

STATEMENTS

# 1:TO READ DATA

select * from shankartb where id=4;


# 2:AND STATEMENT

select * from shankartb where name='Akash' and id=4;

# 3:OR STATEMENT

select * from shankartb where name='Akash' or id=1;

# 4:UPDATE STATEMENT

update shankartb set name='Akash',phone=444444444 where id=5;

# 5:DELETE STATEMENT

delete from shankartb where id=4;

# 6:NOT STATEMENT

select * from shankartb where not name="Shankar";

# 7:ORDER BY STATEMENT(In Ascending Order)

select * from shankartb order by name

select * from shankartb order by id

# 8:LIMIT STATEMENT

select * from shankartb limit 2;

# 9:BETWEEN STATEMENT

select * from shankartb where id between 1 and 3;

# 10:DISTINCT STATEMENT

select distinct name from shankartb;

select distinct id from shankartb;

select distinct phone from shankartb;


# 11:ALIAS STATEMENT

select id as myid,name as student from shankartb;

# 12:ALTER STATEMENT

alter TABLE shankartb add age int(10);

# 13:CHANGE DATA TYPE

alter TABLE shankartb modify column age varchar(10);

# 14:DROP STATEMENT

alter TABLE shankartb drop column age;

# 15:IN STATEMENT

select * from shankartb where name in("Akash","Abinay");

# 16:LIKE STATEMENT

select * from shankartb where name like 'bas%';

# 17:COUNT STATEMENT

select COUNT(id) from shankartb;

# 18:MAX STATEMENT

select max(id) from shankartb;

# 19:MIN STATEMENT

select min(id) from shankartb;

# 20:AVERAGE STATEMENT

select avg(id) from shankartb;

# 21.ORDER STATEMENT

select * from shankartb order by age desc;

# 22.FOREIGN KEY

1.create Table onetb(
 uid int(10) not null AUTO_INCREMENT,
 name varchar(10) not null,
 age int(10) not null,
 primary key(uid)
 );

2.create Table twotb(
 cid int(10) not null,
 city varchar(10) not null,
 uid int(10) not null,
 foreign KEY(uid) REFERENCES onetb(uid),
 primary key(cid)
 );


# 23.JOINS

1.create Table emp(
 id int(10) not null,
 name varchar(10) not null,
 phone bigint(20) not null,
 deptno int(10) not null,
 primary key(id)
 );

2.create Table dept(
 deptno int(10) not null,
 dept_name varchar(10) not null,
 deptlocation varchar(20) not null,
 primary key(deptno)
 );

3.select * from emp inner join dept on emp.deptno =dept.deptno;  

