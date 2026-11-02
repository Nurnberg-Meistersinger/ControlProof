# ControlProof

Open scanner results as NIS2-mapped OSCAL evidence.

**Status:** planning. No code yet. This repository will hold the work described below.

## Why

Organisations have to show their security measures to auditors, regulators and customers. Today they do it with questionnaires and screenshots that the other side cannot check.

The pieces for something better already exist. Open scanners such as CISA ScubaGear and Prowler read real configurations, and NIST and BSI publish their requirements in OSCAL, an open format for security assessments. What is missing is the link between the two: these scanners do not produce OSCAL, some checks that auditors ask for do not exist in open form, and there is no OSCAL catalog of NIS2 Article 21.

## How it works

1. **Collect.** Read security settings from Microsoft 365, AWS and Microsoft Defender for Endpoint with ScubaGear, Prowler and small collectors for the fields they skip.
2. **Evaluate.** Run the data through open, versioned and tested rules in Open Policy Agent (Rego).
3. **Convert.** Write the results as OSCAL Assessment Results, where each check is linked to the requirement it supports.
4. **Share.** The organisation keeps the file and gives it to an auditor, regulator or customer, who can open and validate it with any OSCAL tool.

## Planned results

- Converters from ScubaGear and Prowler (OCSF) output to OSCAL Assessment Results, validated with oscal-cli.
- Open checks for AWS Backup Vault Lock mode and backup age, and for Defender for Endpoint coverage and antivirus mode per device.
- An OSCAL catalog of NIS2 Article 21 and mappings from each check to NIS2, BSI Grundschutz++ and NIST SP 800-53.

Where a piece fits an existing project, we will offer it there: converters to compliance-trestle (OSCAL Compass), AWS Backup checks to Prowler.

## Not in scope

A general-purpose scanner, a GRC tool, or signing of evidence files.

## Licence

Code: Apache-2.0. Mapping files: CC BY 4.0, except files derived from the BSI catalog, which are CC BY-SA 4.0 like their source.
