# Connecting PHP to MySQL Databases

### Pre-Requisites
1. You'll be required to have some basic knowledge of PHP if you want to follow some examples here.
2. You'll also want to get yourself familiarised with SQL to follow along.

### Contents

* **[Fundamentals](https://github.com/ForeseTech/HowWhatWhy/blob/master/PHPToMySQLConnections.md#fundamentals)** - If you want a basic understanding of how websites function, read this.
* **[Moving To PHP](https://github.com/ForeseTech/HowWhatWhy/blob/master/PHPToMySQLConnections.md#moving-to-php)** - If you're an impatient little shit and just want to get things done, go to this section.
* **[Fixing Errors In Your Code](https://github.com/ForeseTech/HowWhatWhy/blob/master/PHPToMySQLConnections.md#fixing-errors-in-your-code)** - If you're stuck with a stupid error.
* **[Helpful Reference Links](https://github.com/ForeseTech/HowWhatWhy/blob/master/PHPToMySQLConnections.md#helpful-reference-links)** - If this wasn't that helpful, you could always refer these links to understand better.

<br>

## Fundamentals

### What do you mean by 'front-end' and 'back-end'?

Any web-application comprises of two main 'divisions'; the front-end and the back-end.

* The front-end is what is seen and used by a user.
* The back-end is all the work that is being done in the background that is hidden from the user.
* **For example**; On the Google website, all the links and pictures and whatever you can see is the front-end. The back-end is whatever that goes on in the background, such as Google getting all the information from a database and displaying them onto the webpage.

### What are the languages used for building the front-end and back-end of a webpage?

The languages used for building a webpage are mainly HTML, CSS and JavaScript. The languages used for building the back-end are mainly PHP, Ruby, Python and several others. JavaScript is a bit special because it allows developers to build both using itself.

### When is a website said to be 'Dynamic'?

*Dynamic* is a term that is used for websites that have information that constantly changes. 

  **For example,** Facebook is a dynamic website because information displayed on the site not only varies from user to user, but also from time to time. On the other hand, my website (www.arjunaravind.in) is static because whoever you are and whenever you see the site, the information remains the same.

Now, let's take Facebook as an example throughout this course so that it's easier for beginners to understand.

### What exactly does a back-end do?

Back-ends are what enable a website to be dynamic. They get information from the database an display it onto the website. 

**For example,** Facebook's back-end enables it to get your profile picture, about information, recent posts, etc and display it in HTML whenever you go to your Facebook profile. All these data are stored in the database, which is usually built using SQL.

### How will the back-end help in our Aptitude Test Software?

* When a user logs in to the software, his/her information will be stored in the database by the back-end. 
* When a user is attempting the test, the back-end is what will retrieve questions, based on a user's department and set number (set 1, set 2, etc) and their respective options stored in the database and display these onto the user's screen.
* When a user presses 'submit', the back-end is what will store these answers and the user's score into the database for future use.

Hopefully, you've gotten an idea of what the back-end does for our site. Here's a [link](https://careerfoundry.com/en/blog/web-development/whats-the-difference-between-frontend-and-backend/) if you want to understand it better.

<br><br>

## Moving to PHP

### Technically speaking, what will PHP do in this Aptitude Test Software?

* PHP will 'insert' data into the database (For the login process).
* PHP will 'retrieve' specific data from the database and display it on the user's screen (For the MCQs).
* PHP will 'insert' data into the database again (For storing the results).

### Wow, that's so simple, right?

No, that's the thing, PHP can't do this alone.

It's like Batman, it needs a Robin.
PHP's Robin is MySQL. And their Batmobile is XAMPP.

### What is MySQL?

SQL stands for Structured Query Language. It is a language which we use to insert, retrieve and update data in databases. It has various implementations and one of these implementations is MySQL. Think of SQL like Tamil; you have Chennai Tamil, Madurai Tamil and so many other dialects of the same language. Each of these are very similar but have slight modifications. Similarly, MySQL is a *dialect* of SQL and one of the most popular.

All data is stored in a database in the form of tables. If you're not familiar with SQL, please go learn.

### So, how do make them work together?

Sometimes, Batman and Robin don't get along and you need Alfred to come and sort things between them. In the same way, PHP and MySQL don't just somehow work together magically, you need to use something called PDO to make them seamlessly work with each other.

### Okay, fine. What is PDO and how does it work?

PDO stands for PHP Data Object. It's some pre-written PHP code which is used for connecting PHP and MySQL. There's no need to install it or whatever, it comes pre-installed with PHP when you install XAMPP.

I'll explain using a series of steps. We'll then look at each of these steps individually later on.

<br>

1. **Forming A Connection** - We need to first form a connection between the PHP and the MySQL Database. For this, we need to provide the IP address of the SQL server, our database username and database password for that username. We also need to provide the name of the database which we want to use.

```
$server_address="localhost";
$username="root";
$password="";
$dbname="MOCKS";

$Conn=new PDO("mysql:host=$servername;dbname=$dbname",$user,$pass);
$Conn->setAttribute(PDO::ATTR_ERRMODE,PDO::ERRMODE_EXCEPTION);
```

Almost always, the default username and password on XAMPP are ```root``` and ```""``` (no password). The default IP address is also ```localhost``` because the PHP file and the MySQL database are located on the same server. The database name is a sample name, you'll have to create a database on XAMPP and set the ```$dbname``` to the name of your database.

As for the last two lines, just go ahead and copy and paste into your code. It'll take a long time for me to explain that.

This connections is done so that the PDO knows where to find the MySQL databases (using the IP address), tells the MySQL database that it is authorised to use it (using the username and password) and then confirms using the name of the database.

<br>

2. **Writing SQL Statements (Queries)** - We learnt that SQL is a language used for manipulating data in database tables, right? So, in SQL, statements which are used to 'retrieve', 'insert' and 'update' data in databases are called *queries*. 

Here are a few sample MySQL queries. If you don't understand, I suggest you go back and learn SQL and then learn this section.

```

/* For retrieving data from a table. */

Select USER_NAME, USER_DATEOFBIRTH, USER_PROFILEPICTURE, USER_POSTS from FACEBOOK_DATABASE
Select EMPLOYEE_ID, EMPLOYEE_NAME, EMPLOYEE_SALARY from EMPLOYEE_DATABASE

/* For inserting data into a table. */

Insert into FACEBOOK_DATABASE values ("Arjun Aravind", "10.01.1998", "profile.jpg", "heyyyyy...blah blah")
Insert into EMPLOYEE_DATABASE values (1234, "Aravind Balakrishnan", 1000000000)

/* For updating data in a table. */

UPDATE FACEBOOK_DATABASE set USER_DATEOFBIRTH="22.10.1998" where USER_NAME="Arjun Aravind"
UPDATE EMPLOYEE_DATABASE set EMPLOYEE_NAME="Aravind B" where EMPLOYEE_NAME="Aravind Balakrishnan"

```

<br>

3. **Executing MySQL Queries Inside PDO Code** - We can execute MySQL queries inside PDO code. How? Take a look below.

We have to 'insert', 'retrieve' and 'update' data in a database table. So, the code for all these three situations is a bit different. You can use these examples as reference when you're implementing all this.

We also make use of the ```$Conn``` variable that we talked about in Step 1.

**Updating Data in a Table**

```
$sql = "UPDATE MyGuests SET lastname='Doe' WHERE id=2";
$stmt = $conn->prepare($sql);
$stmt->execute();
```

**Retrieving (Selecting) Data from a Table**

```
$sql_stmt="SELECT EMPLOYEE_NAME FROM EMPLOYEE_DATABASE";
	
$stmt = $conn->query($sql_stmt);
$results = $stmt->fetchAll(PDO::FETCH_ASSOC);

echo "Names of Employees\n";

foreach ($results as $row) {
  echo $row['EMPLOYEE_NAME'];
}
```

and depending on the contents of the SQL table, the output would be something like

```
Names of Employees

Arjun
Aravind
Adnan
SA
...
...
Divya
...
...
```

**Inserting Data into a Table**

The code for this is very similar to the code for the updation of data in a table.

```
$sql_stmt="Insert into EMPLOYEE_DATABASE values (1234, "Aravind Balakrishnan", 1000000000)";
$sql=$conn->prepare($sql_stmt);
$sql->execute();
```

### How do I know if any of this worked?
Well, for insertion and updation of data, it's always good to see if it worked by going go to the corresponding MySQL Database in XAMPP and seeing if the relevant changes actually worked.

<br><br>

## Fixing Errors In Your Code

So, you'll mostly like be getting a few errors in your PHP code. Trust me, PHP/SQL/PDO almost never works perfectly on the first attempt. Here are some things to go over in case you're stuck.

### Access Denied
* If you get an error which denies access to the MySQL database, then start off by checking the username and password that you gave for forming the connection. Check if these credentials are the same in the XAMPP MySQL Server too.
* If those are correct, then double-check the name of the database that you have given. Is this database name the same as the name of the database that you want to use? Are the username/password the correct credentials for this database? Check out all of this.

### Syntax Errors
* Check if all of the statements end with semi-colons. Yeah, it makes a difference.
* Check if all of the variables start with the ```$``` symbol.
* If you're using certain variables multiple times throughout your code, make sure they are spelled the same. PHP doesn't really explicitly tell you if you've gone wrong somewhere.

### SQL Query Sntax
* Check if your SQL queries are syntactically correct. I recommend you try them on the MySQL console in XAMPP before embedding these queries in your code.

<br><br>

## Helpful Reference Links

* **[Forese Mocks 2018 - MockTestSoftware](https://github.com/ForeseTech/MockTestSoftware)** - This is the version I created. It uses PHP/SQL and PDO too. If you're stuck, you could always see how it was done last year and then try it out yourself.
* **[W3Schools - Connecting PHP To MySQL](https://www.w3schools.com/php/php_mysql_connect.asp)** - Refer the PDO examples in the tutorials given here. They give examples for various technologies, but you guys should refer the PDO examples.
* **[Email Your Questions Here](mailto:arjun.aravind1998@gmail.com)** - Click that.
