# Overview

The LDS is database is using tradition relational database structure with MySQL. The database structure can be mainly divied to three parts: design, template and site management.

* Design: contains all the data/ table directly related to the learning design itself.
* Template: contains the templates which is imported as the skeleton while the users.
* Site Management: contains the options, users and the others site settings.


Besides, the LDS is trying to use the redis to publish the announcement for the users who subscribe the design and force the user updating the course data.