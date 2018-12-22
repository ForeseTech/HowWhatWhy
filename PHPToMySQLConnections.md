# Connecting PHP to MySQL Databases

### Pre-Requisites
1. You'll be required to have some basic knowledge of PHP if you want to follow some examples here.
2. You'll also want to get yourself familiarised with SQL to follow along.

Let's go! We'll start off with some fundamentals.

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

  **For example,** Facebook is a dynamic website because information displayed on the site not only varies from user to user, but also from time to time. On the other hand, my website (www.arjunaravind.com) is static because whoever you are and whenever you see the site, the information remains the same.

Now, let's take Facebook as an example throughout this course so that it's easier for beginners to understand.

### What exactly does a back-end do?

Back-ends are what enable a website to be dynamic. They get information from the database an display it onto the website. 

**For example,** Facebook's back-end enables it to get your profile picture, about information, recent posts, etc and display it in HTML whenever you go to your Facebook profile. All these data are stored in the database, which is usually built using SQL.

### How will the back-end help in our Aptitude Test Software?

* When a user logs in to the software, his/her information will be stored in the database by the back-end. 
* When a user is attempting the test, the back-end is what will retrieve questions, based on a user's department and set number (set 1, set 2, etc) and their respective options stored in the database and display these onto the user's screen.
* When a user presses 'submit', the back-end is what will store these answers and the user's score into the database for future use.

Hopefully, you've gotten an idea of what the back-end does for our site. Here's a [link](https://careerfoundry.com/en/blog/web-development/whats-the-difference-between-frontend-and-backend/) if you want to understand it better.

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

### So, how do make them work together?

Ahh yes, here is the part where we have to understand some concepts and code a little bit.

I'll explain it in the form of steps. 

1. 
