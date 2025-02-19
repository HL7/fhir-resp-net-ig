### Introduction

This profile is used to create the PlanDefinition instances for RESPNet programs.

The RESPNet program deals with identification and surveillance of Flu(Influenza), RSV, ARI, COVID 19 cases across predefined participating zipcodes across the country. 

The PlanDefintiion profile is capable of identifying reportable conditions for the following use cases

* Use Case 1: Hospital-based influenza case detection (Detected based on positive Flu test result for an encounter in-progress)
* Use Case 2: Hospital-based clinical influenza surveillance (Detected based on positive Flu test result for an encounter which is already closed)
* Use Case 3: RESP-NET Disease Burden cases (Detected based on Acute Respiratory Illness diagnosis along with a Flu or RSV or a Covid 19 test)
* Use Case 4: Hospital-based surveillance for COVID-19 (Detected based on a positive test result and the encounter has been closed)
* Use Case 5: Hospital-based surveillance for RSV (Detected based on a positive RSV test result and the encounter has been closed)
* Use Case 6: Influenza vaccine effectiveness evaluation (Detected based on a negative flu test result and the encounter has been closed)

### Triggers for initiating the workflow 

The workflow can be initiated by either the starting of an encounter or the closing of an encounter.


 