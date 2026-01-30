The following is a list of all the changes based on versions.

### Changes made from STU 2 (Ballot) to STU 2:

#### Addressed the following Jira Tickets:

|JIRA #|Ticket Description|
|---------|----------|
|[FHIR-52800](https://jira.hl7.org/browse/FHIR-52800) | Please add project contributors and IG author information |
|[FHIR-52472](https://jira.hl7.org/browse/FHIR-52472) | Typos in IG |
|[FHIR-52364](https://jira.hl7.org/browse/FHIR-52364) | Alternative Mapping to Length of Stay Data Element in Use Case 1 |
|[FHIR-52361](https://jira.hl7.org/browse/FHIR-52361) | Duplicate Date of Death Data Elements |
|[FHIR-52360](https://jira.hl7.org/browse/FHIR-52360) | Missing example of flu subtyping result codes |
|[FHIR-52248](https://jira.hl7.org/browse/FHIR-52248) | Descriptions of Scenarios 1, 2 and 3 |
|[FHIR-52247](https://jira.hl7.org/browse/FHIR-52247) | other respiratory viruses |
|[FHIR-52235](https://jira.hl7.org/browse/FHIR-52235) | Rename RESP-NET EHR Capability Statement |
|[FHIR-52234](https://jira.hl7.org/browse/FHIR-52234) | Add a tab/page for Change Log |
|[FHIR-52233](https://jira.hl7.org/browse/FHIR-52233) | Rename Knowledge Artifacts: Libraries section |
|[FHIR-52232](https://jira.hl7.org/browse/FHIR-52232) | Fix broken links on Specification page |
|[FHIR-52231](https://jira.hl7.org/browse/FHIR-52231) | Create Data Submitter Capability Statement |
|[FHIR-52230](https://jira.hl7.org/browse/FHIR-52230) | Create Data Receiver Capability Statement |
|[FHIR-51804](https://jira.hl7.org/browse/FHIR-51804) | Clarify encounter expectations |
|[FHIR-51749](https://jira.hl7.org/browse/FHIR-51749) | N. ICD-10 CMS codes Discharged Diagnoses as header, but ICD-9 listed in table |
|[FHIR-51748](https://jira.hl7.org/browse/FHIR-51748) | respiratory support (bipap, cpap, high flow nasal cannula) using lab result incorrectly |
|[FHIR-51742](https://jira.hl7.org/browse/FHIR-51742) | US Public Health Triggering Valueset Library Example has no content |
|[FHIR-51741](https://jira.hl7.org/browse/FHIR-51741) | Typo found Figure 2.1 label - "Worflow" should be "Workflow"? |
|[FHIR-51469](https://jira.hl7.org/browse/FHIR-51469) | Update to align with USCDI V3/US Core 6.1 |


#### Detailed Description of Changes:

<table border="1">
    <thead>
       <tr style="background-color:#DCDCDC">
            <th style="text-align: center; vertical-align: middle;">Artifact</th>
            <th style="text-align: center; vertical-align: middle;">Change Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Plan Definition Example</td>
            <td>Updated based on pilot testing results</td>
        </tr>
    </tbody>
</table>

### Changes made from STU 1 to STU 2 (Ballot)

#### Addressed the following Jira Tickets:

|JIRA #|Ticket Description|
|---------|----------|
|[FHIR-51469](https://jira.hl7.org/browse/FHIR-51469) | Update to align with USCDI V3/US Core 6.1.0 |

#### Detailed Description of Changes:

<table border="1">
    <thead>
       <tr style="background-color:#DCDCDC">
            <th style="text-align: center; vertical-align: middle;">Artifact</th>
            <th style="text-align: center; vertical-align: middle;">Change Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>All</td>
            <td>Aligned with <a href="https://hl7.org/fhir/us/core/STU6.1/index.html">US Core 6.1.0</a></td>
        </tr>
        <tr>
            <td>All (where applicable)</td>
            <td>Removed references to MedMorph Reference Architecture IG</td>
        </tr>
         <tr>
            <td>All (where applicable)</td>
            <td>Added references to US PH Library profiles</td>
        </tr>
        <tr>
            <td><a href="StructureDefinition-resp-net-composition.html">RESP-NET Composition</a></td>
            <td>Added Encounter section</td>
        </tr>
    </tbody>
</table>

### Changes made from STU 1 (Ballot) to STU 1

#### Addressed the following Jira Tickets:

|JIRA #|Ticket Description|
|---------|----------|
|[FHIR-45328](https://jira.hl7.org/browse/FHIR-45328) | Tag bundles to identify which use case is being reported |
|[FHIR-45327](https://jira.hl7.org/browse/FHIR-45327) | Support Catchment Area |
|[FHIR-44524](https://jira.hl7.org/browse/FHIR-44524) | Revise Introduction to include other approaches than MedMorph RA |
|[FHIR-44516](https://jira.hl7.org/browse/FHIR-44516) | Clarify sections included in profile content table and not in the Intro section |
|[FHIR-44513](https://jira.hl7.org/browse/FHIR-44513) | Revise workflow to incorporate De-Identification and use UDS+ approach |
|[FHIR-44025](https://jira.hl7.org/browse/FHIR-44025) | Clarify scope of catchment area |
|[FHIR-44024](https://jira.hl7.org/browse/FHIR-44024) | Clarify scope to include test RESULTS available in hospital system |
|[FHIR-43823](https://jira.hl7.org/browse/FHIR-43823) | Fix Update Capability Statement description |
|[FHIR-43680](https://jira.hl7.org/browse/FHIR-43680) | Data for the disease burden project are not anonymous to the RESP-NET site |
|[FHIR-43679](https://jira.hl7.org/browse/FHIR-43679) | Consider adding a hospital identifier |
|[FHIR-43678](https://jira.hl7.org/browse/FHIR-43678) | Section's title should be changed for consistent terminology throughout |
|[FHIR-43677](https://jira.hl7.org/browse/FHIR-43677) | Can the system distinguish between patient discharge vs. patient transfer to another hospital? |
|[FHIR-43676](https://jira.hl7.org/browse/FHIR-43676) | Restate description for Use Cases 4 and 5 |
|[FHIR-43675](https://jira.hl7.org/browse/FHIR-43675) | Evaluate the consistency of using "case" |
|[FHIR-43604](https://jira.hl7.org/browse/FHIR-43604) | References to MedMorph create ambiguity |
|[FHIR-43598](https://jira.hl7.org/browse/FHIR-43598) | Subscription requirement |
|[FHIR-43584](https://jira.hl7.org/browse/FHIR-43584) | Focus IG on Knowledge and Content |
|[FHIR-43534](https://jira.hl7.org/browse/FHIR-43534) | Data Element Requirements |
|[FHIR-43532](https://jira.hl7.org/browse/FHIR-43532) | Editorial Updates in 7.1.1 CapabilityStatement |
|[FHIR-43503](https://jira.hl7.org/browse/FHIR-43503) | Clarify the Pregnancy Outcome entry |
|[FHIR-43502](https://jira.hl7.org/browse/FHIR-43502) | Content missing from the Composition profile narrative |
|[FHIR-43500](https://jira.hl7.org/browse/FHIR-43500) | Clarify placement of DiagnosticReport in the Composition |
|[FHIR-43498](https://jira.hl7.org/browse/FHIR-43498) | Possible duplicate entry in Composition narrative |
|[FHIR-43497](https://jira.hl7.org/browse/FHIR-43497) | Clarify use of MedicationReference slice |
|[FHIR-43496](https://jira.hl7.org/browse/FHIR-43496) | Clarify usage of Medication resources in Composition profile |
|[FHIR-43495](https://jira.hl7.org/browse/FHIR-43495) | Clarify the nature of requirements in the Composition profile narrative |
|[FHIR-43493](https://jira.hl7.org/browse/FHIR-43493) | Please confirm the use of the Composition.type LOINC code |
|[FHIR-43492](https://jira.hl7.org/browse/FHIR-43492) | Clarify the 72 hours threshold after encounter close |
|[FHIR-43491](https://jira.hl7.org/browse/FHIR-43491) | Missing word in Section 3.4.5 |
|[FHIR-43490](https://jira.hl7.org/browse/FHIR-43490) | Figure text overlaps a line |
|[FHIR-43489](https://jira.hl7.org/browse/FHIR-43489) | Inconsistency in COVID references  |
|[FHIR-43486](https://jira.hl7.org/browse/FHIR-43486) | Clarify reporting requirement time frame |
|[FHIR-43485](https://jira.hl7.org/browse/FHIR-43485) | Alignment of Use Cases 1,2 and 3 |
|[FHIR-43462](https://jira.hl7.org/browse/FHIR-43462) | Clarify monitoring of positive patients |
|[FHIR-43461](https://jira.hl7.org/browse/FHIR-43461) | Remove references to BSA |

### Changes for STU 1 (Ballot)

#### Detailed Description of Changes:
Initial version of the IG.
