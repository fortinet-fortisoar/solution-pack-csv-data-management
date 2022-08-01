| [Home](https://github.com/fortinet-fortisoar/solution-pack-csv-data-management/blob/release/1.1.0/README.md) |
|--------------------------------------------|

# Usage

Refer to [Simulate Scenario documentation](https://github.com/fortinet-fortisoar/solution-pack-soc-simulator/blob/develop/docs/solution-pack-guide.md) to understand how to simulate and reset scenarios.

To understand how this solution pack's automation addresses your needs, we have included a few scenarios.

## Scenario - Read and merge two CSV files to create a data set

This scenario demonstrates how to create a single dataset by merging two `.csv` files based on a common column.

Let us consider the following requirements:

- Scan a vulnerability report in a `.csv` file that has a column containing IP addresses
- Scan assets details listed in a `.csv` file that has a column containing IP addresses
- Create a single dataset, which can be ingested in FortiSOAR, by merging these `.csv` files based on the common column &ndash; *IP Address*

Here, we use *Merge and Extract Data from two CSV* operation of **CSV Data Management** connector to read file and extract data. Data is then ingested using the playbook *Read Reports and update assets*.

This playbook undertakes following actions:
1. Use **CSV Data Management** connector to read both `.csv` files and merge using the common column &ndash; *IP Address*.
    - Users can choose to remove duplicates on resultant record set based on the specified columns.  
2. Use the resultant dataset to create asset records with the same asset name and vulnerability details.

>**NOTE**: This simulation creates an example alert that correlates assets record.

## Scenario - Ingest and create artefacts by extracting details from  CSV files

This scenario demonstrates how to ingest rows as records from a `.csv` file.

Let us consider the following requirements:
- Export artefacts in a `.csv` file
- Read `.csv` files and convert it into a dataset that can be ingested in FortiSOAR

Here we use *Extract Data from Single CSV* operation of **CSV Data Management** connector to read file and extract data. Data is then ingested using the playbook *Read artefacts and ingest from CSV*.

The playbook undertakes following actions:
1. Download URL list from https://malsilo.gitlab.io/feeds/dumps/url_list.txt. This list simulates a URL feed.
2. Create an attachment file containing the URLs in CSV format.
3. Download IP addresses list from https://malsilo.gitlab.io/feeds/dumps/ip_list.txt. This list simulates an IP address feed.
4. Create an attachment file containing the IP addresses in CSV format.
5. Join the CSV files containing IP addresses and the URL list using **CSV Data Management** connector to merge both the files and create a data set.
6. Ingest the URLs and IP addresses and create indicators in FortiSOAR using *Ingest Bulk Feed* operation.

>**NOTE:** This simulation creates indicator records and tags them as *csv-demo*.

## Scenario - IP Address Intelligence in the Network Firewall using Fortiguard Threat Intel Feed

This scenario demonstrates how to filter a CSV file containing various types of IOCs (Indicators of Compromise). It uses regex to extract only the IP address to create a resultant dataset that can be directly passed to a firewall's block list or saved as a CSV file.

Let us consider the following requirements:

- User downloads threat intel feed in a CSV file from Fortiguard
    >**NOTE**: For this scenario, the solution pack installation downloads a CSV file, for demonstration purposes, and saves it in **Resources** > **Attachments** named `all.csv`
- This file contains various types of IOCs
- User needs to extract only the IP address as a separate dataset, in CSV format, to upload it to a network firewall

Here, we use *Extract Data from Single CSV* operation of **CSV Data Management** connector to read file and extract data. The file is then processed to extract only the IP addresses in a separate CSV file using the playbook *Update threat intelligence in the Network Firewall using Fortiguard Threat Intel Feed*.

The playbook undertakes following actions:

1. Create an attachment named **IOC**.
    - This acts as a sample CSV file provided by Fortiguard and used as an input to playbook.
2. Use CSV Data Management connector to read CSV files and filter out data based on regex provided by user.
	  - The regex filter provided in this scenario is for IP address
3. The resultant data set can be used as is to pass to firewall or saved as attachment in FortiSOAR for later use.

>**NOTE:** This simulation does not create any example records.