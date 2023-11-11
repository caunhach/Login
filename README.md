# SignUp
This project is about practicing how to create servlets and connect each web page with servlets. We have 3 pages are login page, a registration page, and an index page(which shows when u can log in with the correct username and password). The steps below are the brief guides.
## Brief.
![Architecture](https://github.com/caunhach/SignUp/blob/main/arch.png)<br>
<strong>important components: </strong><br>
- <strong>Server Container : Apache-Tomcat</strong> - A server container is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software
- <strong>Deployment Descriptor : web.xml</strong> -  it is a deployment descriptor file used in Java web applications. It is an XML file that provides configuration information for the web components that comprise a web application. The web.xml file is typically located in the WEB-INF directory of a web application.
- <strong>Servlets : java files (login.java, logout.java, RegristrationServlet.java)</strong> - Servlets are Java classes that extend the capabilities of servers to handle requests and responses. They are part of the Java Platform, Enterprise Edition (Java EE), which is now known as Jakarta EE. Servlets are primarily used to create web applications, and they operate at the server-side to generate dynamic web content, process user input, and manage state.
- <strong>jsp files</strong> - JavaServer Pages (JSP) is a technology used in Java web development to create dynamic web pages. JSP allows developers to embed Java code in HTML pages, making it easier to build web applications with dynamic content.
- <strong>JDBC</strong> - Java Database Connectivity (JDBC) is a Java-based API that provides a standard interface for connecting and interacting with relational databases. JDBC allows Java applications to execute SQL queries, retrieve and update data in a database. It acts as a bridge between Java applications and database management systems (DBMS).
## Step1 : Set the welcome page.
go to the deployment descriptor which is named <strong>web.xml</strong> and change the implemented code as follows. this will make <strong>index.jsp</strong> the first page (if users have logged in)
```
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://xmlns.jcp.org/xml/ns/javaee" xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd" id="WebApp_ID" version="4.0">
  <display-name>signup</display-name>
  <welcome-file-list>
    <welcome-file>index.jsp</welcome-file>
 
  </welcome-file-list>
</web-app>
```
So, if the users are new or haven't logged in yet. we will send them to the login page with this code in index.jsp.
```
<%
	if(session.getAttribute("name")==null){
		response.sendRedirect("login.jsp");
	}
%>
```
## Step2 : Manage Registration Page.
In registration.jsp, set the method="post" and action="register". post is the method to request a web server accept and store the data enclosed in the body of the request message. and the value in action is the servelet where the data will be sent to.
```
<form method="post" action="register" class="register-form" id="register-form">
```
