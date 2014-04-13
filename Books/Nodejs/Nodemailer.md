
Nodemailer is an easy to use module to send e-mails with Node.JS (using SMTP or sendmail or Amazon SES) and is unicode friendly

Nodemailer supports

Unicode to use any characters
HTML content as well as plain text alternative
Attachments (including attachment streaming for sending larger files)
Embedded images in HTML
SSL/STARTTLS for secure e-mail delivery
Different transport methods - SMTP, sendmail, Amazon SES or directly to recipients MX server or even a custom method
SMTP Connection pool and connection reuse for rapid delivery
Preconfigured services for using SMTP with Gmail, Hotmail etc.
Use objects as header values for SendGrid SMTP API
XOAUTH2 authentication and token generation support - useful with Gmail
DKIM signing

Setup
Create a directory

$ mkdir mailer
$ cd mailer
npm install nodemailer

Include the module

var nodemailer = require("nodemailer");



var nodemailer = require("nodemailer");

// create reusable transport method (opens pool of SMTP connections)
var smtpTransport = nodemailer.createTransport("SMTP",{
    service: "Gmail",
    auth: {
        user: "gmail.user@gmail.com",
        pass: "userpass"
    }
});

// setup e-mail data with unicode symbols
var mailOptions = {
    from: "Fred Foo ✔ <foo@blurdybloop.com>", // sender address
    to: "bar@blurdybloop.com, baz@blurdybloop.com", // list of receivers
    subject: "Hello ✔", // Subject line
    text: "Hello world ✔", // plaintext body
    html: "<b>Hello world ✔</b>" // html body
}

// send mail with defined transport object
smtpTransport.sendMail(mailOptions, function(error, response){
    if(error){
        console.log(error);
    }else{
        console.log("Message sent: " + response.message);
    }

    // if you don't want to use this transport object anymore, uncomment following line
    //smtpTransport.close(); // shut down the connection pool, no more messages
});