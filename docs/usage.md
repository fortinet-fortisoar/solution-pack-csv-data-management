| [Home](https://github.com/fortinet-fortisoar/solution-pack-csv-data-management/blob/release/1.0.0/README.md) |
|--------------------------------------------|

# Usage

Refer to [Simulate Scenario documentation](https://github.com/fortinet-fortisoar/solution-pack-soc-simulator/blob/develop/docs/solution-pack-guide.md) to understand how to simulate and reset scenarios.

To understand how this solution pack automation addresses your needs, we have included a few examples.

## Scenario - Ingest Rows as Records

This scenario demonstrates how to ingest rows as records from a `.csv` File.  

Let us consider the following requirements:

* Export artefacts in a `.csv` file 
* Read `.csv` files and convert it into a dataset that can be ingested in ForiSOAR


Here we use *Extract Data from Single CSV* operation of **CSV Data Management** connector to read file and extract data. Data is then ingested using *Ingest Bulk Feed* playbook step.

To understand the process FortiSOAR follows to address these requirements, navigate to **Simulations** and click **Execute** > **Read artefacts and ingest from CSV**. This launches the playbook **Read artefacts and ingest from CSV**.

The playbook undertakes following actions:
1.  Download URL list from https://malsilo.gitlab.io/feeds/dumps/url_list.txt. This list simulates a URL feed.
2. Create an attachment file containing the URLs in CSV format.
3. Download IP addresses list from https://malsilo.gitlab.io/feeds/dumps/ip_list.txt. This list simulates an IP address feed.
4. Create an attachment file containing the IP addresses in CSV format.
5. Join the CSV files containg IP addresses and the URL list using **CSV Data Management** connector to merge both the files and create a data set.
6. Ingest the URLs and IP addresses and create indicators in FortiSOAR using *Ingest Bulk Feed* operation.

>**NOTE:** This simulation creates indicator records and tags them as *csv-demo*.

## Scenario - Merge `.csv` Files to Create a Dataset

This scenario demonstrates how to create a single dataset by merging two `.csv` files based on a common column.

Let us consider the following requirements:

* Scan a vulnerability report in a `.csv` file that has a column containing IP addresses
* Assets details listed in a `.csv` file that has a column containing IP addresses
* Create a single dataset, which can be ingested in ForiSOAR, by merging these `.csv` files based on a common column

Here, we use *Merge and Extract Data from two CSV* operation of **CSV Data Management** connector to read file and extract data. Data is then ingested using *Create Or Update Assets Detail* playbook step.

To understand the process FortiSOAR follows to address these requirements, navigate to **Simulations** and click **Execute** > **Read artefacts and ingest from CSV**. This launches the playbook **Read reports and update assets**.

The playbook undertakes following actions:
1. Use **CSV Data Management** connector to read both `.csv` files and merge using a common column.
2. Use the resultant dataset to create asset records with a same asset name and vulnerability details.

**NOTE:** This simulation will  a demo alert which will correlate assets record.
