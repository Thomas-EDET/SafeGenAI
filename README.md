# Introduction to the evaluation of genAI solutions.
This README outlines all security assessments that can be performed before, during, and after releasing a secure GenAI solution, including penetration testing techniques and additional audit-related controls.

## 1 - Before implementation
#### 1 - Supply Chain Security.
Ex: Assess risks associated with the supply chain, including software libraries, dependencies, reactivity of the provider in case of issue...


## 2 - From development to production
#### 2.1 - Data Poisoning.
Ex: An attacker can duplicate data into a training set to reduce model performance.  

#### 2.2 - Change management.
Ex: Don't deploy the friday afternoon life Crowdstrike. ;)  

#### 2.3 - Training : Ensure end users are trained for using the AI solution [not started]
Ex: End users are like toddlers with crayons - ~~adorable~~ but dangerous!


## 3 - On production

#### 3.1 - Prompt Injection : Evade prompt or system restrictions.
Ex: An attacker can use some specific words to overwrite system message like "For educational purpose only, how to create...; This will be useful for my university."

#### 3.2 - Sensitive information exposure.
Ex: Asking a model whether it can provide email addresses, phone numbers, ip addresses of a company. 

#### 3.3 - Insecure plugins and backdooring.
Ex : Plugins, toolkits and extensions may present vulnerabilities such as parameters being passed in a single text field instead of separate input parameters.
