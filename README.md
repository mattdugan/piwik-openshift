piwik-openshift
===============

Playing with openshift.  I've no affiliation to piwik.

The OpenShift `php` cartridge documentation can be found at:

https://github.com/openshift/origin-server/tree/master/cartridges/openshift-origin-cartridge-php/README.md


Piwik on OpenShift
==================

Piwik is a downloadable, open source (GPL licensed) real time web analytics
software program. It provides you with detailed reports on your website visitors:
the search engines and keywords they used, the language they speak, your popular
pages, and so much more.
Piwik aims to be an open source alternative to Google Analytics, and is already
used on more than 150,000 websites.

More information can be found on the official Piwik website at http://piwik.org

Running on OpenShift
--------------------
Create an account at http://openshift.redhat.com/

Install the rhc tools and run rhc setup if you haven't already.

Create a PHP application with MySQL support

    rhc app create piwik php-5.3 mysql-5.1

Make a note of the username, password, and host name as you will need to use
these to complete the Piwik installation on OpenShift

Add this upstream Piwik quickstart repo

    cd piwik/php
    rm -rf *
    git remote add upstream -m master \
        git://github.com/mattdugan/piwik-openshift.git
    git pull -s recursive -X theirs upstream master

Then push the repo upstream to OpenShift

    git push

That's it, you can now checkout your application at:

    http://piwik-${your_app_namespace}.rhcloud.com

