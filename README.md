#XING employee importer for recon-ng


## What does it do?
This is a <a href="https://bitbucket.org/LaNMaSteR53/recon-ng">recon-ng</a> module that allows to import the employee list from a <a href="https://www.xing.com">XING</a> company page. So it takes the list of employees and stores them into the contacts and profiles tables.

## Installation
Just put it in the `modules/recon/companies-multi` directory (or any modules subdirectory) of the recon-ng framwork. This is

     ~/.recon-ng/modules/recon/companies-multi
     
on Kali.

Do 

    modules reload
    
and you should be ready to go.

## Example

```
[recon-ng][default] > workspaces create Telekom
[recon-ng][Telekom] > db insert companies
company (TEXT): Deutsche Telekom AG
description (TEXT): 
[recon-ng][Telekom] > modules load recon/companies-multi/xing_employees
[recon-ng][Telekom][xing_employees] > run
[*] [profile] Laurence_ABRARD - Xing (https://www.xing.com/profile/Laurence_ABRARD)
[*] [contact] Laurence Abrard (<blank>) - Human resources international business partner
[*] [profile] Fevzi_ACAR2 - Xing (https://www.xing.com/profile/Fevzi_ACAR2)
[*] [contact] Fevzi Acar (<blank>) - Tekniker
...

```
## Help

```
[recon-ng][Telekom][xing_employees] > show info

      Name: XING employee grabber
      Path: modules/recon/companies-multi/xing_employees.py
    Author: Michael Helwig (@c0dmtr1x)

Description:
  Imports employee list from a XING company page to contacts and profiles tables. Iterates through the
  alphabet and grabs data for each letter with up to LIMIT results.

Options:
  Name    Current Value  Required  Description
  ------  -------------  --------  -----------
  COOKIE                 no        Cookie data from your current XING login. You might get more data when logged in. At least "_session_id" and "login" parameters are needed.
  LIMIT   500            yes       Limit of employees per letter
  SOURCE  default        yes       source of input (see 'show info' for details)

Source Options:
  default        SELECT DISTINCT company FROM companies WHERE company IS NOT NULL
  <string>       string representing a single input
  <path>         path to a file containing a list of inputs
  query <sql>    database query returning one column of inputs

```
## Notes
This plugin works by retrieving some JSON data via a call found on the XING website. This means it does not make use of the official XING api but of undocumented calls that worked during the creation of that plugin but might not work tomorrow. 

There are two types of URLs that XING uses:

https://www.xing.com/company/COMPANYNAME/employees.json
and
https://www.xing.com/companies/COMPANYNAME/employees.json

Since it does not seem predictable when XING uses which kind of URL, the module queries both. This produces some useless calls but a convenient level of automation.



