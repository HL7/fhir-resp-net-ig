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
* Cases where the influenza, RSV, or COVID-19 test is not accessible in hospital system

### RESP-NET Actors
The following actors from the [MedMorph RA IG]({{site.data.fhir.ver.medmorphIg}}/usecases.html#medmorph-actors-and-definitions) are used by the RESP-NET use cases:
* Data Source (e.g., Healthcare Facility with FHIR-enabled EHR, HIE with FHIR capability)
* Health Data Exchange App (HDEA) (MedMorph’s backend services app)
* Knowledge Artifact Repository
* Data Receiver (e.g., RESP-NET Site)

#### Interactions between MedMorph RA Actors and Systems for RESP-NET
This section outlines the high-level interactions between the various MedMorph Actors and Systems listed above. These interactions are shown in Figures 2.1 and Figure 2.2 along with the descriptions of each step.

{% include img.html img="resp-net-actors-and-systems.png" caption="Figure 2.1 - RESP-NET Actors and Systems with HDEA" %}

The descriptions for each step in the above diagram include:
* Step 1: The Data Receiver (e.g., RESP-NET Site) creates a Knowledge Artifact and makes it available via the Knowledge Artifact Repository.
     * Step 1a: Knowledge Artifact Repositories which implement notifications, can optionally notify the subscribers (Data Source, HDEA, Administrators) of changes in the Knowledge Artifacts.
* Step 2: The Health Data Exchange App (HDEA) queries the Knowledge Artifact Repository to retrieve a Knowledge Artifact. 
     * Step 2a: HDEA receives the Knowledge Artifact as a response to the query in Step 2.
* Step 3: The HDEA processes the Knowledge Artifact and creates subscriptions in the Data Source’s (e.g., EHR) FHIR Server so that it can be notified when specific events occur in clinical workflows.
* Step 4: Providers as part of their clinical workflows update the data in the Data Source’s patient chart.
* Step 5: The Data Source notifies the HDEA based on subscriptions created in Step 3.
* Step 6: The HDEA queries the Data Source for patient’s data.
     * Step 6a: HDEA receives the response from the Data Source with the patient’s data.
* Step 7: The HDEA submits the created report to the Data Receiver.


{% include img.html img="resp-net-actors-and-systems-no-HDEA.png" caption="Figure 2.2 - RESP-NET Actors and Systems without HDEA" %}
The descriptions for each step in the above diagram include:
* Step 1: The Data Receiver (e.g., RESP-NET Site) creates a Knowledge Artifact and makes it available via the Knowledge Artifact Repository.
     * Step 1a: Knowledge Artifact Repositories which implement notifications, can optionally notify the subscribers (Data Source, Administrators) of changes in the Knowledge Artifacts.
* Step 2: The Data Source queries the Knowledge Artifact Repository to retrieve a Knowledge Artifact. 
     * Step 2a: The Data Source receives the Knowledge Artifact as a response to the query in Step 2.
* Step 3: Providers as part of their clinical workflows update the data in the Data Source’s patient chart.
* Step 4: The Data Source creates and submits the report to the Data Receiver.

### Use Case 1: Hospital-based influenza case detection and minimum data elements AND Use Case 2: Hospital-based clinical influenza surveillance
These use cases will identify patients hospitalized with laboratory-confirmed influenza among residents of the FluSurv-NET catchment area (defined by patient county of residence) for active population-based surveillance. The cases are reported along with minimum patient-level data and transmitted to the FluSurv-NET surveillance officers in the relevant state/local jurisdiction.

Use Case 1 is reported within one week of case identification. Minimum data elements include state and county of residence (or other geographic regions) to define the catchment area, patient age or date of birth, sex, race/ethnicity, hospital admission date, positive influenza testing data (test type, test result, test date), and influenza type and subtype (if available). 

Use Case 2 focuses on the more detailed clinical surveillance data collected in FluSurv-NET by site surveillance officers. Patient-level data from EHRs about persons hospitalized with influenza include data on important outcomes and indicators of disease severity such as ICU admission, mechanical ventilation, in-hospital death, and length of hospital stay. Additional elements include health history (underlying conditions, tobacco, alcohol, substance use), clinical course, viral and bacterial codetections, findings from chest imaging, diagnoses, vaccination, and treatment. This use case will include person-level clinical data elements that are currently collected in FluSurv-NET on a standardized case report form for all identified cases. Not all of the current data elements may be reachable in a FHIR-based approach; proposed solutions should recognize that this may evolve over time and surveillance officers may still need to conduct medical chart review on data elements.

#### User Stories for Use Cases 1 and 2
* Scenario 1: A patient is admitted to the hospital and has symptoms consistent with a case of influenza. An influenza test is ordered, and the test results are positive.
* Scenario 2: A patient is admitted to the hospital. Included in the available patient data is a previously recorded positive influenza test result, which was within 14 days of admission at the hospital.
* Scenario 3: A patient arrives at the emergency room (ER) and has symptoms consistent with a case of influenza. The patient is admitted to the hospital before or while awaiting test results. A positive test is recorded within 14 days of admission or at any time during their hospitalization.

#### Workflow for Use Cases 1 and 2
The positive influenza test results in a notification to the HDEA/BSA. The HDEA queries for a limited set of PII, including the patient’s address. If the patient is not a resident of a catchment area, the HDEA stops all activity regarding this patient. If the patient is a resident of a catchment area the HDEA then regularly monitors the patient’s record until discharge occurs. Upon discharge, the HDEA requests a set of FHIR resources representing patient-level encounter information from the Data Source. This limited data set includes PII and other data. The obtained resources are validated (e.g., checked to see if they are conformant to the appropriate FHIR profiles), bundled, and transmitted to the RESP-NET Site.

{% include img.html img="resp-net-use-case-1.png" caption="Figure 2.3 - Use Case 1 and 2 Workflow" %} 

### Use Case 3: Influenza Disease Burden Project
Because testing for influenza and other respiratory viruses is done at the discretion of the clinician and testing practices may vary widely among facilities and over time, some people hospitalized with influenza may not be recognized and diagnosed. To better estimate the full burden of influenza, CDC collects additional information from FluSurv-NET hospitals on the proportion of patients with acute respiratory illnesses (ARI) who are tested for influenza, SARS-CoV-2, and RSV. This use case will focus on obtaining data on respiratory viral testing practices for CDC’s influenza disease burden project and transmitting it directly to CDC throughout the season. This project collects anonymized patient-level data on persons hospitalized with ARI (based on ICD-10 diagnosis codes) along with information about whether or not the patient was tested for influenza, SARS-CoV-2, or RSV and if so, the test result and test type used for all tests performed (patients may be tested multiple times). Additional data elements include state, age, race/ethnicity, week of admission, ICD-10 discharge diagnoses, and if possible, whether the patient had been admitted to the ICU or died during the hospital stay.

#### User Stories
* Scenario 1: A patient is admitted to the hospital and has a diagnosis consistent with an ARI (match into ARI value set). 
* Scenario 2: A patient visits the ED, has a diagnosis consistent with an ARI (match into ARI value set). (May or may not be admitted to hospital.)

#### Workflow
The diagnosis results in a notification to the HDEA/BSA. The HDEA queries for a limited set of PII, including the patient’s address. The HDEA then regularly monitors the patient’s record until discharge occurs. Upon discharge, the HDEA requests a set of FHIR resources representing patient-level encounter information from the Data Source. This limited data set includes PII and other data. The data reported includes testing status for influenza, SARS-CoV-2, and RSV occurred. The obtained resources are validated (e.g., checked to see if they are conformant to the appropriate FHIR profiles), bundled, and transmitted to the RESP-NET site.

{% include img.html img="resp-net-use-case-3.png" caption="Figure 2.4 - Use Case 3 Workflow" %} 

### Use Case 4: Hospital-based Surveillance for SARSCoV-2 AND Use Case 5: Hospital-based surveillance for Respiratory Syncytial Virus (RSV)
These use cases focus on collecting equivalent data to Use Cases 1-2 but for patients who test positive for SARSCoV-2 (the virus that causes COVID-19) or Respiratory Syncytial Virus (RSV). Public health surveillance through COVID-NET and RSV-NET is conducted in the same sites as FluSurv-NET, collects many of the same data elements, with some additional data elements specific to these viral illnesses.

#### User Stories for Use Cases 4 and 5
* Scenario 1: A patient is admitted to the hospital and has symptoms consistent with a case of COVID-19 or RSV. A COVID or RSV test is ordered, and the test results are positive.
* Scenario 2: A patient is admitted to the hospital. Included in the available patient data is a previously recorded positive COVID or RSV test result, which was within 14 days of admission at the hospital.
* Scenario 3: A patient arrives at the emergency room (ER) and has symptoms consistent with a case of COVID or RSV. The patient is admitted to the hospital before or while awaiting test results. A positive test is recorded within 14 days of admission or at any time during their hospitalization.

#### Workflow for Use Cases 4 and 5
The positive COVID or RSV test results in a notification to the HDEA/BSA. The HDEA queries for a limited set of PII, including the patient’s address. If the patient is not a resident of a catchment area, the HDEA stops all activity regarding this patient. If the patient is a resident of a catchment area the HDEA then regularly monitors the patient’s record until discharge occurs. Upon discharge, the HDEA requests a set of FHIR resources representing patient-level encounter information from the Data Source. This limited data set includes PII and other data. The obtained resources are validated (e.g., checked to see if they are conformant to the appropriate FHIR profiles), bundled, and transmitted to the RESP-NET Site.

{% include img.html img="resp-net-use-case-4.png" caption="Figure 2.5 - Use Case 4 and 5 Workflow" %}   