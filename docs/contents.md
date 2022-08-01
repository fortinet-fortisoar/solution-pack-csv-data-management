| [Home](https://github.com/fortinet-fortisoar/solution-pack-csv-data-management/blob/release/1.1.0/README.md) |
|--------------------------------------------|

# Contents

The **CSV Data Management** solution pack contains the following resources.

## Connectors

| Name                | Description                              |
|:--------------------|:-----------------------------------------|
| CSV Data Management | Performs various operations on CSV files |

## Record Set

| Name        | Description                                                                        |
|:------------|:-----------------------------------------------------------------------------------|
| Attachments | Demo csv files to understand the working of this solution pack                     |
| Scenario    | Read and merge two CSV files to create a data set                                  |
| Scenario    | Ingest and create artefacts by extracting details from  CSV files                  |
| Scenario    | IP Address Intelligence in the Network Firewall using Fortiguard Threat Intel Feed |

## Playbook Collection

|02 - Use Case - CSV Data Management |
| :- |

| Playbook Name                                                                         | Description                                                                                                   |
|:--------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| Read artefacts and ingest from CSV                                                    | Read rows from CSV and creates a dataset to be ingested in FortiSOAR                                          |
| Read Reports and update assets                                                        | Reads and merges two reports. Resulting data set is used to create/ update assets in FortiSOAR                |
| Update threat intelligence in the Network Firewall using Fortiguard Threat Intel Feed | Filter out IOC based on regex from a threat intel feed and provide as recordset for ingestion into a firewall |

>**WARNING**: We recommend that you clone these playbooks before customizing to avoid loss of information while upgrading the solution pack.
