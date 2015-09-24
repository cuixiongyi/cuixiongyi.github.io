---
layout: page
subheadline:  "Django Setup"
title:  "Django Setup"
teaser: "get started with Django"
categories:
    - Django
tags:
    - Django
    - database
    - PostgreSQL
comments: true
show_meta: true

---
<div class="row">


<div class="medium-14 medium-pull-3 columns" markdown="1">

For database always use PostgreSQL instead of MySQL.


install PostgreSQL:
	sudo apt-get install postgresql-9.4
	sudo apt-get install postgresql postgresql-contrib


install GUI for config PostgreSQL
	sudo apt-get install pgadmin3


Login to root user postgres
	sudo su - postgres
	psql
	# change pass word of user Postgres
	ALTER USER Postgres WITH PASSWORD '<newpassword>';


</div><!-- /.medium-8.columns -->

</div><!-- /.row -->
