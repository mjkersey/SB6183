# Modem Stats Scraper for Arris SB6183

This script consumes the poorly defined markup from the Arris SB6183 
Consumer Cable Modem, and stores it in MySQL or MariaDB for additional 
parsing or visualization.

As Arris does not provide a quick endpoint for stats on this modem, and many
operators have deemed it necessary to disable read-only SNMP on the customer
facing interface, it is necessary to iterate through tables and cells 
without DOM IDs or useful classes and selectors by brute force.

Thankfully, Arris has graciously provided us huge <th> tags for the tables
we want, so we can use XPath to find those, and iterate through child <tr>  
and <td> of those tables.

Note that while this is written with OOP, it is largely classless. Take that
how you will. Nested foreach statements are the devil, but DOMDocument 
iteration is what it is.
