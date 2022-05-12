## Release Information

- Solution Pack Version: 1.0.0
- Minimum Compatible FortiSOAR™ Version: 7.2.0
- Authored By: Fortinet
- Certified: No

## Overview

### Introduction
**CSV Data Management ** solution pack demonstrates usage of CSV Data Management connector. This connector uses python modules like CSV, Pandas and NumPy to 
read and manipulate CSV files to create a dataset which can be ingested in FortiSOAR as records 

## Simulation

## Simulation 1 

This scenario demonstrates how can we ingest rows as records from a CSV File.  

Lets consider below use case follow

* A tool which allows to export artefacts  in a CSV File 
* We have to read CSV file and convert into a dataset which can be ingested in ForiSOAR
* Here we use 'Extract Data from Single CSV' operation of CSV Data Management connector to read file and extract data
* Data is then ingested using 'Ingest Bulk Feed' playbook step

Usage

* Deploy current scenario 
* A playbook will execute which will download CSV feed from following URLs
    * https://malsilo.gitlab.io/feeds/dumps/url_list.txt
    * https://malsilo.gitlab.io/feeds/dumps/ip_list.txt
* Above feeds are saved as attachment in CSV format
* We will use CSV Data Management connector to join both files and create data set
* This data set will be ingested in ForiSOAR using 'Ingest Bulk Feed'

**Note :** This simulation will create IOC records , tagged 'csv-demo'


## Simulation 2

This scenario demonstrates how can we create a single dataset by merging two CSV files pivoting over a common column.

Lets consider below use case follow

* A tool which allows to vulnerability  scan report in a CSV file  which has IP address as column name
* An assets  inventory tool which allows to export assets details in CSV file which has also IP address as column name
* We have to create single dataset by merging two CSV files pivoting over a common column which can be ingested in ForiSOAR  
* Here we use 'Merge and Extract Data from two CSV' operation of CSV Data Management connector to read file and extract data  
* Data is then ingested using playbook 

Usage

* Deploy current scenario  
* A playbook will using CSV Data Management connector  read both CSV files and merge using common column.
	* The resultant dataset will be used to create assets records which will have asset name along with vulnerability details 

**Note :** This simulation will  a demo alert which will correlate assets record. 
