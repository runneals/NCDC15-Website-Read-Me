# NCDC15 Website Team 12 Secure Version
Read this document completyly. otherwise don't waste your time
Note: Links won't work till you register and give me your account name. 
#About

This website run on apache on a Debian 4 server. It use CGI-BIN to communicate from HTML to the server to display, add, and modify users and user information(More on this later).

#What is CGI-BIN
<h6>My own very technical answer:</h6>
The Common Gateway Interface (CGI) is a standard for interfacing external applications with information servers, such as HTTP or Web servers. A plain HTML document that the Web daemon retrieves is static, which means it exists in a constant state: a text file that doesn't change. A CGI program, on the other hand, is executed in real-time, so that it can output dynamic information.
<h6>Easier to understand version(read above first)</h6>:
CGI stand for Common Gateway Interface. It's a way for a website to talk dirrectly to a server's command line using a programing langauge other than a web development language. You still must use some sort of front end language such as HTML, but you can use for example c to pass an argument to the server
Something like this:
```
<body>
<form action="/cgi-bin/cat" method="POST">
      File to display:<input type="text" name="file"><br>
      <input type="submit" text="Submit!">
</form>
</body>
```

You can then have a cgi-bin programing language such as C handle the data which is sent using the post function so via url. You can catch the passed file in c and pint out the data like this:
```
sprintf(buffer, "cat %s", query_value("file"));
```

#So how does this site work? 


That is the entire point of this file.

This website is basicly a big gui interface for editing a bunch of no extetnion text files. 

<h3>User Info/DB</h3>

You'll be happy to know we don't have to mess with DB's such as MySQL and shit this time around like we did at IT-Olympics. All the so called databases for this website are just no extention plain text files that are munipulated using command line. no actual databases instalation.
Users are Defined by a file called user_'user_name" where user name being the name of the user. 
Structure of inside the file:
  from: <name> <amount> <balance>
	to: <name> <amount> <balance>
it's pretty lame, each line is a transaction entry. The balance at the end of the last entry is the current balance of the account.


</h1>How does it work</h1>
When a user logs in, they are presented with a single page with an option to view account(1) and transfer money(2)

1. View Account is a link that runs a c scripted using cgi to view the user's balance. It uses the loged in user's name and echo's that to the url which then runs a cgi script on the server and echo's back the data. that file can be found <a href="https://github.com/apples723/NCDC15-Website/blob/master/src/show-user.c">here</a>.
2. Trnasfer Money is a form that when a user clicks submits it sends over the url just like view account data that is then transferd on the server to the user's browser that file can be found <a href="https://github.com/apples723/NCDC15-Website/blob/master/src/make-payment.c">here</a>.


any other question leave in the issues section and i will answer them.
