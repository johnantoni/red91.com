------------------------------------------------------------------------

layout: post\
title: DNS Mastery and Google Apps\
category: linux\
keywords: "google apps, dns, domain name, tutorial"\
----

DNS = Domain Naming Service\
p. ...quite simply the glue that ties your newly purchased .com to your
server's hardware.

There's a few other bits to it, like the Name Server, or the original
Domain Name Registrar (e.g. godaddy.com); they're a little more involved
but I'll try to cover them here.

#### Buying your Domain Name

First off, go buy your new domain name at one of the domain name
registrars. I've suggested [godaddy.com](http://www.godaddy.com) purely
because they're so cheap, but you can use any other.

Next once you've bought your domain name, go in and you'll be able to
point it to a naming server. This connects your .com to the server
containing your dns details and thus to your meat & potatoes server box.

So for this example, we'll use [SliceHost](http://www.slicehost.com)
(although you can use the free DNS provider
[FreeDNS](http://freedns.afraid.org/) who provide the service free of
charge, I've used and are really good.

Go to your DNS provider and they'll provide you with a list of
nameservers you can use.

e.g.\
bq. ns1.slicehost.net<br />ns2.slicehost.net<br />ns3.slicehost.net

Go to your domain registrar and in the nameserver provider part, enter
these three (3 for automatic failover, one fails the other takes charge,
etc.).

#### Creating your DNS records

Now we've got the .com pointed to the DNS provider that will host our
DNS records, let's go create some.

So, for SliceHost, go to the DNS Records section, click 'advanced view'
(specifically for slicehost); and now We'll begin.

Create a record for each one of these

> type: A\
> <br />name: www\
> <br />data: (ip address of your serverbox)

> type: A\
> <br />name: mysite.com.\
> <br />data: (ip address of your serverbox)

Note the . at the end of the one above (DNS records always have a
fullstop at the end), and that it doesn't have www. at the start.

Next we need to tie the domain name to the name server for a sort-of
reverse lookup. So create records like...

> type: NS\
> <br />name: mysite.com.\
> <br />data: ns1.slicehost.net.

> type: NS\
> <br />name: mysite.com.\
> <br />data: ns2.slicehost.net.

> type: NS\
> <br />name: mysite.com.\
> <br />data: ns3.slicehost.net.

Notice the fullstop at the end of the Name and Data part.

Unfortunately now we have to wait for these settings to propogate thru
the web, can take up-to 48 hours but usually quicker (try doing this at
midnight in the UK).

#### Using Google Apps for your Email

Now we've got the site hooked up to the server box, how about email?.
Well, you could install an exchange mail server on your box but they're
usually a nightmare for the beginners; so how about we use Google Apps &
GMail?.

Google Apps is a new free service google has launched to provide home
users and small business with a way of having standard google tools but
tied to their domain name. So you can have contact\@mysite.com be your
email address but use Google GMail to handle it without building an
exchange server; big headache gone.

Go to the [Google Apps website](http://www.google.com/a/) and register
for the free Standard service. Use your new domain name mysite.com and
create an email account for it.

You'll need to verify your site with Google to turn the service on,
quickest method is to put an HTML file on your server's /public web
directory and click VERIFY.

Once done go back to SliceHost / Your DNS provider and create a new
record,

> type: MS\
> <br />name: mysite.com.\
> <br />data: ASPMX.L.GOOGLE.COM.\
> <br />auxilary info: 1

..the 1 is the priority level, Google will probably tell you to create
more of these but for now one will do.

Now once google shows your site as Verified all the services (calendar,
excel, start page, etc.) will switch to Active. Setup your Email part
and tell it you've done the MX record change and it'll switch to
Updating. Now wait 3-48 hours for it to check the MX record on your DNS
provider.

If all ok, that'll go to Active, send an email to the address to check
and it should work.

#### Using shorter URLs for Google Apps

As you'll have worked out, Google doesn't give you the best web
addresses to access your Google Apps email, docs, etc.

To make this more simple, go to each service in your Google Apps
Dashboard and click 'change url', pick the one it gives you (usually
mail.\[mysite.com\], etc. ) and click ok.

It will then tell you how to adjust your DNS settings appropriately, but
to make this simpler, login to your DNS control panel in SliceHost (or
whatever DNS service your using) and add some CNAME aliases.

> type: CNAME\
> <br />name: mail\
> <br />data: GHS.GOOGLE.COM.

> type: CNAME\
> <br />name: start\
> <br />data: GHS.GOOGLE.COM.

> type: CNAME\
> <br />name: docs\
> <br />data: GHS.GOOGLE.COM.

> type: CNAME\
> <br />name: calendar\
> <br />data: GHS.GOOGLE.COM.

CNAME records basically act like an alias pointing to your core domain.
So adding a record with a name of 'mail' will suddenly redirect anything
with mail.mysite.com to the location you put in data. Once done, it
should take effect in 1-3 hours.

#### Final Points

A name records are much like CNAME records only they have a lesser
performance impact, however if you are gonna create some more like
blog.mysite.com I'd stick to CNAME's; only create one A record for your
www =\> www.mysite.com connection.

Drop me a line if you get stuck,

All the best,

John.
