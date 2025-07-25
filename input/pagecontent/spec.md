This section defines the specific requirements for systems wishing to conform to actors specified in this Respiratory Virus Hospitalization Surveillance Network (RESP-NET) Content Implementation Guide (IG). The specification highlights the requirements used to  report the data to RESP-NET sites.

### Pre-reading
Before reading this formal specification, implementers should first be familiar with the [Use Cases](usecases.html) page which provides the business context and general process flow.

### Conventions
This IG uses specific terminology to flag statements that have relevance for the evaluation of conformance with the guide:

* **SHALL** indicates requirements that must be met to be conformant with the specification.
* **SHOULD** indicates behaviors that are strongly recommended (and which may result in interoperability issues or sub-optimal behavior if not adhered to), but which do not, for this version of the specification, affect the determination of specification conformance.
* **MAY** describes optional behaviors that are free to consider but where there is no recommendation for or against adoption.

### Claiming Conformance 

Actors and Systems asserting conformance to this IG must implement the requirements outlined in the corresponding capability statements. The following definition of Must Support is to be used in the implementation of the requirements.

#### Must Support Definition

* Systems **SHALL** be capable of populating data elements as specified by the profiles and data elements are returned using the specified APIs in the capability statement.
* Systems **SHALL** be capable of processing resource instances containing the Must Support data elements without generating an error or causing the application to fail. 
* Systems **SHOULD** be capable of displaying the Must Support data elements for human use or storing them for other purposes.
* In situations where information on a particular data element is not present and the reason for absence is unknown, Systems **SHALL NOT** include the data elements in the resource instance returned from executing the API requests.
* When accessing RESP-NET Content IG data, Systems **SHALL** interpret missing data elements within resource instances returned from API requests as data not present.
* When data is not available for any of the mandatory elements specified in the IG, a data absent reason extension should be added to satisfy the requirement along with an appropriate value from the [data-absent-reason value set](http://hl7.org/fhir/ValueSet/data-absent-reason).


### Profiles and Other IGs Used by the Specification
This specification makes significant use of [FHIR profiles]({{site.data.fhir.path}}profiling.html), search parameter definitions, and terminology artifacts to describe the content to be shared as part of RESP-NET Content IG workflows. The IG is based on [FHIR R4]({{site.data.fhir.path}}) and profiles are listed for each interaction.

The full set of profiles defined in this IG can be found by following the links on the [FHIR Artifacts](artifacts.html) page.

#### US Core Usage

This IG leverages the [US Core]({{site.data.fhir.ver.uscoreR4}}) set of profiles defined by HL7 for sharing non-veterinary electronic medical record (EMR) individual health data in the U.S.  Where US Core profiles exist, this IG either leverages them directly or uses them as a base for any additional constraints needed to support the research use cases.  If no constraints are needed, this IG does not define any profiles.

#### Subscriptions Backport IG Usage

This IG leverages the [Subscriptions Backport IG]({{site.data.fhir.ver.subscriptionsIg}}/index.html) defined by HL7 Infrastructure WG for automating reporting workflows using subscriptions.

#### US Public Health Profiles Library (USPHPL) IG Usage

This IG leverages the [US Public Health Profiles Library IG]({{site.data.fhir.ver.uspublichealthprofileslibraryIg}}/index.html) defined by the Public Health WG as a collection of reusable architecture and content profiles representing common public health concepts and patterns. The USPHPL IG is intended to be a complement to US Core used to ease implementation burden of healthcare organizations, electronic health record companies, public health agencies, and others involved in the US public health endeavor.

#### electronic Case Reporting (eCR) IG Usage
This IG leverages the [electronic Case Reporting (eCR) IG]({{site.data.fhir.ver.ecrIg}}/index.html) defined by the Public Health WG which specifies the appropriate FHIR resources and transactions needed for the eCR process. FHIR offers opportunities to further enable automated triggering and reporting of cases from EHRs, to ease implementation and integration, to support the acquisition of public health investigation supplemental data, and to connect public health information (e.g., guidelines) with clinical workflows.

### Implementation Requirements

#### SMART App Launch IG Usage

This IG leverages the [SMART App Launch IG]({{site.data.fhir.ver.smartapplaunch}}/index.html) defined by HL7 Infrastructure WG for enabling authentication and authorization between various actors involved in the workflows. This IG leverages Substitutable Medical Applications, Reusable Technologies (SMART) on FHIR Backend Services Authorization requirements.

#### SMART on FHIR Backend Services Requirements

This section outlines how the SMART on FHIR Backend Services Authorization will be used by the RESP-NET Content IG.

* The system actors namely Data Source, Data Submitter, and the Data Receiver are required to use the SMART on FHIR Backend Services Authorization mechanisms as outlined below for the following interactions:


    * Data Submitter accessing data from the Data Source
    * Data Submitter posting data to the Data Receiver with FHIR capabilities
    

* System actors acting as servers (e.g., Data Source and Data Receiver) **SHALL** advertise conformance to SMART on FHIR Backend Services by hosting Well-Known Uniform Resource Identifiers (URIs) as defined in the [SMART App Launch IG Backend Services]({{site.data.fhir.ver.smartapplaunch}}/backend-services.html) specification.

* System actors acting as servers **SHALL** include token_endpoint, scopes_supported, token_endpoint_auth_methods_supported and token_endpoint_auth_signing_alg_values_supported as defined in the [SMART App Launch IG Backend Services]({{site.data.fhir.ver.smartapplaunch}}/backend-services.html) specification.

* When System actors act as clients (e.g., Data Submitter), they **SHALL** share their JSON Web Key Set (JWKS) with the server System actors (e.g., Data Source and Data Receiver) using Uniform Resource Locators (URLs) as defined in the [SMART App Launch IG Backend Services]({{site.data.fhir.ver.smartapplaunch}}/backend-services.html) specification.

* System actors acting as clients **SHALL** obtain the access token as defined in the [SMART App Launch IG Backend Services]({{site.data.fhir.ver.smartapplaunch}}/backend-services.html) specification.

* For the RESP-NET use cases, Data Sources **SHALL** support the system/*.read scopes. 

* The Data Receiver **SHALL** support the system/*.read and system/*.write scopes. 

* The health care organization's existing processes along with the Data Source's authorization server **SHALL** verify any organizational policy requirements (for example, registration of the Data Submitter, authorizing requested scopes, testing and verification of Data Submitter implementation in sandbox environment prior to production) before allowing the Data Submitter to access the data to be included in the RESP-NET report. 

#### Data Source Requirements

* The Data Source (e.g., EHR, HIE) **SHALL** support the requirements as outlined in the [Data Source Capability Statement](CapabilityStatement-resp-net-data-source.html).

##### Authorization Requirements 

* The Data Source **SHALL** support the [SMART on FHIR Backend Services Authorization](spec.html#smart-on-fhir-backend-services-requirements) outlined above as a Server. 
 

##### Subscription Requirements

* The Data Source **SHALL** support the creation of Subscriptions for the encounter-end Subscription Topic

* The Data Source **SHALL** support [``rest-hook``]({{site.data.fhir.path}}subscription.html#2.46.7.1) Subscription channel to notify the Data Submitter.

* The Data Source **SHALL** support Notification Bundles with [``full resource payload``]({{site.data.fhir.ver.subscriptionsIg}}/payloads.html#full-resource) as outlined in the Backport Subscriptions IG. 

* For the RESP-NET Content IG, the Data Source **SHALL** include the Encounter resource which was closed as part of the Notification Bundle.

* The Data Source **SHALL** support operations and APIs for Subscription, Notification Bundle, Subscription status resources as outlined in the [Data Source Capability Statement](CapabilityStatement-resp-net-data-source.html).


##### Data API Requirements

* The Data Source **SHALL** support the [US Core Server APIs]({{site.data.fhir.ver.uscoreR4}}/CapabilityStatement-us-core-server.html) and MedicationAdministration APIs as outlined in the [Data Source Capability Statement](CapabilityStatement-resp-net-data-source.html) for the Data Submitter to access patient data.

 
#### Data Submitter Requirements 


##### Authorization Requirements

* The Data Submitter **SHALL** support the [SMART on FHIR Backend Services Authorization](spec.html#smart-on-fhir-backend-services-requirements) outlined above as a client. 


##### Subscription Requirements

* The Data Submitter **SHALL** create Subscriptions for the encounter-end Subscription Topic.

* The Data Submitter **SHALL** support [``rest-hook``]({{site.data.fhir.path}}subscription.html#2.46.7.1) Subscription channel to receive notifications from the Data Source.


##### Subscription Notification API 

* The Data Submitter **SHALL** support a POST API <BSA Base URL>/receive-notification with a payload of the Subscription Notification Bundle to receive the notifications from the Data Source. 



* The Data Submitter **SHALL** ensure no duplicate reports are submitted for the same patient and encounter occurring within a health care organization.


##### Data API Requirements 

* The Data Submitter acting as a client **SHALL** use the [US Core Server APIs]({{site.data.fhir.ver.uscoreR4}}/CapabilityStatement-us-core-server.html) and MedicationAdministration APIs as outlined in the [Data Source Capability Statement](CapabilityStatement-resp-net-data-source.html) to access patient data from the Data Source.


##### Report Generation Requirements 

* The Data Submitter **SHALL** create a RESP-NET report following the constraints identified in [RESP-NET Content Bundle](StructureDefinition-resp-net-content-bundle.html).

* The Data Submitter **SHALL** package the RESP-NET report following the constraints identified in [RESP-NET Reporting Bundle](StructureDefinition-resp-net-reporting-bundle.html).

* The Data Submitter **SHALL** submit the message containing the RESP-NET report to the identified endpoint.

##### Use of Non-FHIR Based Approaches to Submit the RESP-NET Report

* The Data Submitter **MAY** use other transport methods such as Direct Transport to submit the RESP-NET Report created when appropriate.

#### RESP-NET Data Receiver Actor Requirements


##### Message Receiving and Processing Requirements

* The Data Receiver **SHALL** implement the $process-message operation on the ROOT URL of the FHIR Server to receive reports from the Data Submitter using the POST operation.

* Upon receipt of the message, the Data Receiver **SHALL** validate the message before accepting the message.

* When there are validation failures, the Data Receiver **SHALL** return an Operation Outcome response with the details of the validations as part of the POST response.



