# Overview

The LDS is database is using tradition relational database structure with Mysql. The database structure can be mainly divied to three part, design, template and site management.

* Design: contains all the data/ table directly related to the learning design itself.
* Template: contains the templates which is imported as the skeleton while the users.
* Site Management: contains the options, users and the others site setting.


Besides, the LDS is trying to use the redis to publish the announcement for the users who subcride the design and force the user updating the course data.