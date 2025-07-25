### Introduction

This profile is used to represent the clinical content present within a RESP-NET report.

**Sections and Population Criteria**

The following sections and population criteria should be used to create the composition resource below.

* Patient: The Patient who is the subject of the encounter
* Encounter: The Encounter that was closed (updated documentation has to be added to the encounter before saying it is closed)
* Encounter section: Encounter and encounter diagnosis for the patient.
* Problems section: Underlying medical conditions and active health concerns and problems. All clinicalStatuses except InActive, verificationStatus = Confirmed
* Medications Administered section: Medications administered during the encounter and status = active
* Medications section: Current medications and pertinent medication history
* Results section: Lab results and associated diagnostic reports for laboratory results reporting linked to the encounter, ordered during the encounter, or received during the encounter plus thresholds. (72 hours after the encounter close). Status = final, preliminary
* Vital Signs section: Vital signs for the encounter with status = final, amended
* Procedures section: Procedures performed during the encounter limited to status = completed, in-progress 
* Immunizations section: Immunizations associated with the patient
* Notes section: Clinical notes and diagnostic reports (for report and note exchange) created during the encounter 
* Plan of Treatment section: Services or medications ordered during the encounter. Status = active, completed. Intent = order
* Social History section: Smoking status, disability status, and characteristics of home environment with status = final, amended
* Pregnancy section: Pregnancy status, pregnancy outcome, postpartum status for the patient during the encounter

The above data has to be populated by the implementers of the DataSource or Data Submitter.

### Populating the RESP-NET Use Case

The [RESP-NET Report Context extension](StructureDefinition-respnet-report-context-extension.html) is used to convey how a RESP-NET report receiver can use the data for different programs and use cases associated with the RESP-NET activities.

The extension **SHALL** always have two codings from the [RESP-NET Context value set](ValueSet-respnet-report-context-codes.html), one containing the Level 1 code of "respnet-case-report" and the second one will be one of the Level 2 use case specific codes.
 
