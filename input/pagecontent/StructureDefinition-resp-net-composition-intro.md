### Introduction

This profile is used to represent the clinical content present within a RESP-NET report.

**Sections and Population Criteria**

The following sections and population criteria should be used to create the composition resource below.

* Patient: The Patient who is the subject of the encounter
* Encounter: The Encounter that was closed (Updated documentation has to be added to the encounter before saying it is closed)
* Problems section: Underlying medical conditions and active problems. All clinicalStatuses except InActive, verificationStatus = Confirmed
* Medications Administered section: Medications administered during the encounter and status = active
* Medications section: Current medications and pertinent medication history
* Results section: Lab results and associated diagnostic reports for laboratory results reporting linked to the encounter, ordered during the encounter, or received during the encounter plus thresholds. (72 hours after the encounter close). Status = final, preliminary
* Vital Signs section: Vital signs for the encounter with status = final, amended
* Procedures section: Procedures performed during the encounter limited to status = completed, in-progress 
* Immunizations section: Immunizations associated with the patient
* Notes section: Clinical notes and diagnostic reports (for report and note exchange) created during the encounter 
* Plan of Treatment section: Medications or procedures ordered during the encounter. Status = active, completed. Intent = order
* Social History section: Smoking status, disability status, and characteristics of home environment with status = final, amended
* Pregnancy section: Pregnancy status, pregnancy outcome, postpartum status for the patient during the encounter

The above data has to be populated by the implementers of either the DataSource actors or the MedMorph HDEA (backend services app).
 