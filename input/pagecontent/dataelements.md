This section provides an overview of the RESP-NET use case data elements (as depicted on case report forms (CRF)) and their mappings to HL7 FHIR resources, profiles, and elements. 

### Use Case 1
<b>Hospital-based Influenza Case Detection</b>: This use case includes a minimum set of data elements which include: data elements to define the catchment area, patient age or date of birth, sex, race/ethnicity, hospital admission date, hospital facility name, positive influenza testing data (test type, test result, test date), and influenza type and subtype (if available).

{% include uc1_data_element_mapping.html %}

### Use Case 2
<b>Hospital-based Clinical Influenza Surveillance</b>: This use case focuses on the more detailed clinical surveillance data collected in FluSurv-NET by site surveillance officers. Patient-level data from EHRs about persons hospitalized with influenza include data on important outcomes and indicators of disease severity such as ICU admission, mechanical ventilation, in-hospital death, and length of hospital stay. Additional elements include health history (underlying conditions, tobacco, alcohol, substance use), clinical course, viral and bacterial codetections, findings from chest imaging, diagnoses, vaccination, and treatment. This use case will include person-level clinical data elements that are currently collected in FluSurv-NET on a standardized case report form for all identified cases. Not all of the current data elements may be reachable in a FHIR-based approach; proposed solutions should recognize that this may evolve over time and surveillance officers may still need to conduct medical chart review on data elements.

{% include uc2_data_element_mapping.html %}

### Use Case 3
<b>RESP-NET Disease Burden Project</b>: Because testing for influenza and other respiratory viruses is done at the discretion of the clinician and testing practices may vary widely among facilities and over time, some people hospitalized with influenza may not be recognized and diagnosed. To better estimate the full burden of influenza, CDC collects additional information from FluSurv-NET hospitals on the proportion of patients with acute respiratory illnesses (ARI) who are tested for influenza, SARS-CoV-2, and RSV. This use case will focus on obtaining data on respiratory viral testing practices for CDC’s RESP-NET disease burden project. This project collects patient-level data on persons hospitalized with ARI (based on ICD-10 diagnosis codes) along with information about whether or not the patient was tested for influenza, SARS-CoV-2, or RSV and if so, the test result and test type used for all tests performed (patients may be tested multiple times). Additional data elements include state, age, race/ethnicity, week of admission, ICD-10 discharge diagnoses, and if possible, whether the patient had been admitted to the ICU or died during the hospital stay.

{% include uc3_data_element_mapping.html %}

### Use Case 4
<b>Hospital-based Surveillance for SARSCoV-2</b>: This use case focuses on collecting data similar to use case 2 but for patients who test positive for SARSCoV-2 (the virus that causes COVID-19). Public health surveillance through COVID-NET is conducted in many of the same sites as FluSurv-NET, collects many of the same data elements, with some additional data elements specific to these viral illnesses.

{% include uc4_data_element_mapping.html %}

### Use Case 5
<b>Hospital-based Surveillance for Respiratory Syncytial Virus (RSV)</b>: This use case focuses on collecting data similar to use case 2 but for patients who test positive for RSV. Public health surveillance through RSV-NET is conducted in many of the same sites as FluSurv-NET, collects many of the same data elements, with some additional data elements specific to these viral illnesses.

{% include uc5_data_element_mapping.html %}


### Mapping Sheet Legend
Each mapping table contains three columns. The left column contains the name of data element from each use case CRF. The right column contains the mapping to FHIR profile.element. The middle column designates the mapping fidelity. The mapping fidelity values and their descriptions are as follows:
* Complete: The CRF element is directly and completely mapped to a FHIR element.
* Partial: The CRF element is partially mapped to a FHIR element. In most cases, the partial mapping resides in the list of expected values. An example is Race because FHIR doesn't have a "multiracial" value (but up to 5 races can be applied).
* Indirect: The CRF element is indirectly mapped to a FHIR element. One example is that Age is indirectly mapped to FHIR by subtracting Patient.birthdate from Encounter.period.start. Another example is when the CRF has a yes/no value for each condition. FHIR has the condition, but doesn't record yes/no values hence the indirect mapping.
* Gap: The CRF element does not map to an element in FHIR.