------------------------------------------------------------------------

layout: post\
title: Subversion or SourceSafe\
category: subversion\
----

In the avenue of Software Version Control and Agile Technologies there
are two competing technologies, open-source Subversion SVN and Microsoft
SourceSafe 2005 (now Team System).

But which is which and what benefits does each offer?

#### Subversion

Subversion in it's essence is open-source so is perfectly suited for
LAMP (Linux, Apache, MySQL, PHP) projects. It is uniquely flexible and
simple to apply to any medium type or operating system, with easy
integration to Windows via the TortoiseSVN software add-on.

It allows you to import, commit, export and differentiate successive
code releases down to their line numbers really easily.

Also being in the public domain, the source-code is frequently updated
and bugs fixed rapidly due to the larger exposure of it's code-base.

#### Microsoft SourceSafe

Very similar to Subversion, it has been designed as a source-code
cataloging and version control tool primarily for .NET / Visual Studio
projects; and thus it's flexibility ends there. It does however allow
you to set aside a server as your primary project Source center and
drill down to key changes in code, much like SVN.

People however have complained about a long-running database corruption
issue within but this should be fixed.

#### So Which ?

Well the tight integration into the VS.NET IDE environment is a definite
plus and on top of this SourceSafe gives you a database and Vault
repository in which it keeps track of code changes; however the O/S
inflexibility and more importantly the new VS.NET Team System pricing
does put it out of scope for small businesses and independent startups.

It really is like my dad says 'horses for courses', SS maybe good in a
Microsoft-Only environment, but SVN maybe better for independent
startups and projects where flexibility and O/S independence are vital.

Really down to you, I know this isn't that detailed a guide but should
give you some idea as to which to choose.

#### What do I use ?

In reality I employ both,

For my Ruby on Rails projects I use a mixture of Capistrano, Deprec
capped to a SubVersion repository on the Linux server. Works well as my
development machine for that is an Apple Mac.

Workwise, I employ Subversion + TortoiseSVN to keep catalogued and
protected all my web script files and xhtml micro-sites, with the
repositories kept on a protected remote server.

However all my VS.NET applications are kept under SourceSafe control,
hooked up to a remote server in another office; used by other
developers.

Works quite well, the quick-install nature of SVN would allow me to get
up-to-speed from a stolen laptop really fast (if another machine existed
on standby). VS.NET would take longer but then that comes with the
territory, but could be faster if you had a disk-image on standby with a
carbon-copy of your development system setup.

Your choice.

John.
