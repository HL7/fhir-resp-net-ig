### Business Need
Respiratory Virus Hospitalization Surveillance Network (RESP-NET) cases are currently identified through a variety of mechanisms at each site, including review of daily or weekly hospital and laboratory line lists and reportable disease databases, through an often manual and labor-intensive process. Additionally, for laboratory-confirmed hospitalized cases identified through RESP-NET, surveillance staff conduct medical chart abstractions based on a standardized case report form to obtain detailed demographic and clinical data on hospitalized cases including length of stay, underlying medical conditions, hospital course, and in-hospital deaths.

CDC seeks to expand the utilization of electronic health information in RESP-NET and improve data exchange between healthcare facilities, state/local public health partners, and CDC to maintain the quality of these important surveillance activities while improving the efficiency and timeliness with which these data are available. Such enhancements will reduce the burden on surveillance sites and allow for scalability to additional sites in the future.

### Goals of the Use Cases
The goals of the RESP-NET reporting use cases include:
* Expand the utilization of electronic health information in RESP-NET
* Improve the availability of EHR data for public health surveillance of hospitalized persons with influenza and other respiratory viruses including SARS-CoV-2 and RSV
* Improve data exchange between healthcare facilities, state/local public health partners, and CDC to maintain the quality of these important surveillance activities 
* Improve the efficiency and timeliness with which these data are available and reported
* Reduce burden of data collection on surveillance officers and healthcare facilities 
* Allow for scalability to additional sites in the future

### Scope of the Use Cases
#### In Scope
* Patients hospitalized with laboratory-confirmed respiratory viruses among residents of the RESP-NET catchment area (defined by patient county of residence) for active population-based surveillance
* Identify the data elements to be retrieved from the data source to produce the report
* Define under what circumstances a report must be created and transmitted to RESP-NET sites

#### Out of Scope
* Assessment of the data quality of the content extracted from the data source
* Changes to existing provider workflow or existing data entry
* Policies of the clinical care setting to collect consent for data sharing
* Cases where the influenza, RSV, or SARSCoV-2 test result is not accessible in hospital system

### RESP-NET Actors
The following actors are used by the RESP-NET use cases:
* Data Source (e.g., Healthcare Facility with FHIR-enabled EHR, HIE with FHIR capability)
* Data Submitter (e.g., a system responsible for exracting the data from the Data Source, evaluate the data for submission and is responsible for submitting the data (report) to the Data Receiver
* Data Receiver (e.g., RESP-NET Site)

#### Interactions between RESP-NET Actors 
This section outlines the high-level interactions between the actors listed above. 

{% include img.html img="resp-net-actors-and-systems-datasubinsource.png" caption="Figure 2.1 - RESP-NET Reporting Worflow with Data Submitted in Data Source Organization" %}

The descriptions for each step in the above diagram where the Data Submitter is hosted within the Data Source Organization are as follow:

* Step 1: The Data Submitter creates a subscription in the Data Source so that it can be notified when specific events occur in clinical workflows.In this model, Subscriptions should be implemented using FHIR Subscriptions.
* Step 2: Providers as part of their clinical workflows update the data in the Data Source’s patient chart.
* Step 3: The Data Source notifies the Data Submitter based on subscriptions created in Step 1.
* Step 4: The Data Submitter queries the Data Source for patient’s data. 
	* Step 4a: Data Submitter receives the response from the Data Source with the patient’s data.
* Step 5: The Data Submitter evaluates the received data to determine if a report needs to be submitted.
* Step 6: In cases where the report needs to be submitted, The Data Submitter submits the created report to the Data Receiver.



{% include img.html img="resp-net-actors-and-systems-datasubinreceiver.png" caption="Figure 2.2 - RESP-NET Reporting Workflow with Data Submitter in Data Receiver Organization" %}

Implementers may package the Data Submitter within the DataSource as illustrated in the diagram below.

The descriptions for each step in the above diagram are as follows:

* Step 1: Providers as part of their clinical workflows update the data in the Data Source’s patient chart
* Step 2: DataSubmitter which is part of the DataSource package evaluates the changes to determine if a report needs to be generated
* Step 3: In case a report needs to be submitted, The Data Submitter submits the created report to the Data Receiver.

The next section identifies the list of RESP-Net use cases and provides brief descriptions for the use cases 

### Use Case 1: Hospital-based influenza case detection and minimum data elements
This use case will identify patients hospitalized with laboratory-confirmed influenza among residents of the RESP-NET catchment area (defined by patient state and county of residence (or other geographic regions)) for active population-based surveillance. The cases are reported along with minimum patient-level data and transmitted to the RESP-NET surveillance officers in the relevant state/local jurisdiction.

Use Case 1 is reported when case identification is met. Minimum data elements to define the catchment area, patient age or date of birth, sex, race/ethnicity, hospital admission date, hospital facility name, positive influenza testing data (test type, test result, test date), and influenza type and subtype (if available). 

<!--Use Case 2 focuses on the more detailed clinical surveillance data collected in RESP-NET by site surveillance officers. Patient-level data from EHRs about persons hospitalized with influenza include data on important outcomes and indicators of disease severity such as ICU admission, mechanical ventilation, in-hospital death, and length of hospital stay. Additional elements include health history (underlying conditions, tobacco, alcohol, substance use), clinical course, viral and bacterial codetections, findings from chest imaging, diagnoses, vaccination, and treatment. This use case will include person-level clinical data elements that are currently collected in RESP-NET on a standardized case report form for all identified cases. Not all of the current data elements may be reachable in a FHIR-based approach; proposed solutions should recognize that this may evolve over time and surveillance officers may still need to conduct medical chart review on data elements.-->

#### User Stories for Use Case 1
* Scenario 1: A patient is admitted to the hospital. An influenza test is ordered, and the test results are positive.
* Scenario 2: A patient is admitted to the hospital. Included in the available patient data is a previously recorded positive influenza test result, which was within 14 days before admission at the hospital.
* Scenario 3: A patient arrives at the emergency room (ER). The patient is admitted to the hospital before or while awaiting test results. A positive test is recorded at any time during their hospitalization.

#### Workflow for Use Case 1
The positive influenza test prompts a notification to the Data Submitter. The Data Submitter queries for a limited set of PII, including the patient’s address. If the patient is not a resident of a catchment area, the Data Submitter stops all activity regarding this patient. If the patient is a resident of a catchment area, the Data Submitter requests a set of FHIR resources representing patient-level encounter information from the Data Source. The obtained resources are bundled and transmitted to the RESP-NET Site.

### Use Case 2: Hospital-based clinical influenza surveillance
Use Case 2 focuses on the more detailed clinical surveillance data collected in RESP-NET by site surveillance officers. Patient-level data from EHRs about persons hospitalized with influenza include data on important outcomes and indicators of disease severity such as ICU admission, mechanical ventilation, in-hospital death, and length of hospital stay. Additional elements include health history (underlying conditions, tobacco, alcohol, substance use), clinical course, viral and bacterial codetections, findings from chest imaging, diagnoses, vaccination, and treatment. This use case will include person-level clinical data elements that are currently collected in RESP-NET on a standardized case report form for all identified cases. Not all of the current data elements may be reachable in a FHIR-based approach; proposed solutions should recognize that this may evolve over time and surveillance officers may still need to conduct medical chart review on data elements.

#### User Stories for Use Case 2
* Scenario 1: A patient is admitted to the hospital. An influenza test is ordered, and the test results are positive.
* Scenario 2: A patient is admitted to the hospital. Included in the available patient data is a previously recorded positive influenza test result, which was within 14 days before admission at the hospital.
* Scenario 3: A patient arrives at the emergency room (ER). The patient is admitted to the hospital before or while awaiting test results. A positive test is recorded at any time during their hospitalization.

#### Workflow for Use Case 2
The close of an encounter prompts a notification to the Data Submitter. The Data Submitter (after a 72-hour delay for lab results) queries for a limited set of data, including the patient’s address, in-patient status, and influenza lab result. If the patient is not a resident of a catchment area, the Data Submitter stops all activity regarding this patient. If the patient is a resident of a catchment area, was admitted to the hospital, and has a positive influenza lab result, the Data Submitter requests a set of FHIR resources representing patient-level encounter information from the Data Source. The obtained resources are bundled and transmitted to the RESP-NET Site.

### Use Case 3: RESP-NET Disease Burden Project
Because testing for influenza and other respiratory viruses is done at the discretion of the clinician and testing practices may vary widely among facilities and over time, some people hospitalized with influenza may not be recognized and diagnosed. To better estimate the full burden of influenza, CDC collects additional information from RESP-NET hospitals on the proportion of patients with acute respiratory illnesses (ARI) who are tested for influenza, SARS-CoV-2, and RSV. This use case will focus on obtaining data on respiratory viral testing practices for CDC’s RESP-NET disease burden project. This project collects patient-level data on persons hospitalized with ARI (based on ICD-10 diagnosis codes) along with information about whether or not the patient was tested for influenza, SARS-CoV-2, or RSV and if so, the test result and test type used for all tests performed (patients may be tested multiple times). Additional data elements include state, age, race/ethnicity, week of admission, ICD-10 discharge diagnoses, and if possible, whether the patient had been admitted to the ICU or died during the hospital stay.

#### User Stories for Use Case 3
* Scenario 1: A patient is admitted to the hospital and has a diagnosis consistent with an ARI (match into ARI value set). 
* Scenario 2: A patient visits the ED, has a diagnosis consistent with an ARI (match into ARI value set). (May or may not be admitted to hospital.)

#### Workflow for Use Case 3
The close of an encounter prompts a notification to the Data Submitter. The Data Submitter (after a 72-hour delay for lab results) queries for a limited set of PII data, including the patient’s address, in-patient status, and ARI lab result. If the patient is not a resident of a catchment area, the Data Submitter stops all activity regarding this patient. If the patient is a resident of a catchment area, was admitted to the hospital, and has a positive ARI lab result, the Data Submitter requests a set of FHIR resources representing patient-level encounter information from the Data Source. The obtained resources are bundled and transmitted to the RESP-NET site.

### Use Case 4: Hospital-based Surveillance for SARSCoV-2 AND Use Case 5: Hospital-based surveillance for Respiratory Syncytial Virus (RSV)
These use cases focus on collecting equivalent data to Use Case 2 but for patients who test positive for SARSCoV-2 (the virus that causes COVID-19) (Use Case 4) or Respiratory Syncytial Virus (RSV) (Use Case 5). Public health surveillance through COVID-NET and RSV-NET is conducted in many of the same sites as RESP-NET, collects many of the same data elements, with some additional data elements specific to these viral illnesses.

#### User Stories for Use Cases 4 and 5
* Scenario 1: A patient is admitted to the hospital. A SARSCoV-2 or RSV test is ordered, and the test results are positive.
* Scenario 2: A patient is admitted to the hospital. Included in the available patient data is a previously recorded positive SARSCoV-2 or RSV test result, which was within 14 days before admission at the hospital.
* Scenario 3: A patient arrives at the emergency room (ER). The patient is admitted to the hospital before or while awaiting test results. A positive test is recorded at any time during their hospitalization.

#### Workflow for Use Cases 4 and 5
The close of an encounter prompts a notification to the Data Submitter. The Data Submitter (after a 72-hour delay for lab results) queries for a limited set of data, including the patient’s address, in-patient status, and ARI lab result. If the patient is not a resident of a catchment area, the Data Submitter stops all activity regarding this patient. If the patient is a resident of a catchment area, was admitted to the hospital, and has a positive SARSCoV-2 or RSV lab result, the Data Submitter requests a set of FHIR resources representing patient-level encounter information from the Data Source. The obtained resources are bundled and transmitted to the RESP-NET site.