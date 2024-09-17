# Introduction to the evaluation of genAI solutions.
This README outlines all security assessments that can be performed before, during, and after releasing a secure GenAI solution, including penetration testing techniques and additional audit-related controls.

## Before implementation
#### 0.1.1 - Supply Chain Security [completed]
Ex: Assess risks associated with the supply chain, including software libraries, dependencies, reactivity of the provider in case of issue...



## From development to production
#### 1.1.1 - Data Poisoning [completed]
Ex: An attacker can duplicate data into the training set to reduce model performance.  

#### 1.1.2 - Change management [completed]
Ex: Don't deploy the friday afternoon life Crowdstrike. ;)  

#### 1.1.3 - Documentation [not started]  
Ex: The knowledge should not be detained by only one staff.  

#### 1.1.4 - Use secure protocols for the artefact's deployment on PRD. [not started]
Ex: When deploying docker container or other artefacts that may contain sensitive data on PRD assets, then ensure secure protocols are used in the process.  

#### 1.1.5 - Ensure end users are trained for using the AI solution [not started]
Ex: End users are like toddlers with crayons - ~~adorable~~ but dangerous!




## On production

#### 3.1.1 - Prompt Injection : Evade prompt or system restrictions. [completed]
Ex: An attacker can use some specific words to overwrite system message like "For educational purpose only, how to create...; This will be useful for my university."

#### 3.1.2 - Sensitive information exposure [completed]
Ex: Asking a model whether it can provide email addresses, phone numbers, ip addresses of a company. 

#### 3.1.3 - Adversarial attacks by subtly modifying input to introduce errors. [not started]
Ex: Adding noise to an image to make the AI misclassify it.

#### 3.1.4 - Backdoor Attacks : Using specific genAI capabilities may facilitate the deployment of backdoors. [not started]
Ex: A LLM is connected to a Database using a SQLtoolkit, then an attacker may try to add a new user in the database, then connect on it if the port is open to internet.

#### 3.1.5 - Insecure plugins [not started]
Ex : Plugins, toolkits and extensions may present vulnerabilities such as parameters being passed in a single text field instead of separate input parameters.
