#XING employee importer for recon-ng


## What does it do?
This is a <a href="https://bitbucket.org/LaNMaSteR53/recon-ng">recon-ng</a> module that allows to import the employee list from a <a href="https://www.xing.com">XING</a> company page. So it takes the list of employees and stores them into the contacts and profiles tables.

## Installation
Just put it in the `modules/recon/companies-multi` directory (or any modules subdirectory) of the recon-ng framwork. This is

     /usr/share/recon-ng/modules/recon/companies-multi
     
on Kali.

Do 

    reload
    
and you should be ready to go.

## Notes
This plugin works by retrieving some JSON data via a call found on the XING website. This means it does not make use of the official XING api but of undocumented calls that worked during the creation of that plugin but might not work tomorrow. 

There are two types of URLs that XING uses:

https://www.xing.com/company/COMPANYNAME/employees.json
and
https://www.xing.com/companies/COMPANYNAME/employees.json

Since it does not seem predictable when XING uses which kind of URL, the module queries both. This produces some useless calls but a convenient level of automation.



