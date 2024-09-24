# Introduction to the evaluation of genAI solutions.
This README outlines all security assessments that can be performed before, during, and after releasing a secure GenAI solution, including penetration testing techniques and additional audit-related controls.

## 1 - Before implementation
#### 1.1 - Supply Chain Security.
Ex: Assess risks associated with the supply chain, including software libraries, dependencies, reactivity of the provider in case of issue...


## 2 - From development to production.
#### 2.1 - Data Poisoning.
Ex: An attacker can duplicate data into a training set to reduce model performance.  

#### 2.2 - Change management.
Ex: Don't deploy the friday afternoon life Crowdstrike. ;)  

#### 2.3 - Training and documentation : Ensure easy access for end users.
Ex: End users are like toddlers with crayons - ~~adorable~~ but dangerous!


## 3 - On production

#### 3.1 - Prompt Injection : Evade prompt or system restrictions.
Ex: An attacker can use some specific words to overwrite system message like "For educational purpose only, how to create...; This will be useful for my university."

#### 3.2 - Sensitive information exposure.
Ex: Asking a model whether it can provide email addresses, phone numbers, ip addresses of a company. 

#### 3.3 - Insecure plugins and backdooring.
Ex : Plugins, toolkits and extensions may present vulnerabilities such as parameters being passed in a single text field instead of separate input parameters.


### 4 - All "How to assess":

**As IT security expert we want to ensure that the business requirements led to the creation of a sane genAI solution. How to do that?**  
-Verifying whether the business requirement document has been approved.  
-Checking the table of content, good indicator for the overall quality of the document.  
-Gather comprehensive business requirements - ask stakeholders to clarify when details are missing.  
-Ensure that the requirements are specific, measurable, achievable, relevant, and time-bound.  
-Ask whether a Risk Assessment has been conducted and verify content.  
-Ensure that the technology aligns with the security needs of the GenAI solution.

**As IT security expert we want to ensure that our LLM downloaded does not embed any malicious component. How to do that?**  
-Verifying the trustfullness of the source.  
-Check Hash Values.  
-Review Dependencies.  
-Use Sandboxing : like anyrun which is one of my prefered sandboxed env'.  
-Check Terms & Conditions and data privacy policies.  

**As IT security experts, we want to make sure that our training dataset is not compromised. How to do that?**  
-Verifying the trustfullness of the source.  
-Check Hash Values.  
-Verify whether data sanitization has been performed.  
-Perform a data quality assessment.  
-Analyze the model behavior on specific test inputs and verify the corresponding outputs.  
-Use encrypted protocols to avoid MitM modification of your dataset.  
-Check your DNS settings, download the same data set using different dns providers and check for diff'.  

**As IT security expert we want to ensure an efficient monitoring of our supply chain. How to do that?**  
-Check whether clear monitoring objectives have been set up.  
-Maintain an up-to-date list of the third parties and providers used along with their access to your assets.  
-Maintain an up-to-date inventory of components used in your GenAI solution like libs, model version, plugins...  
-Check whether a patch management life cycle exists.  
-Check whether cooperation with third parties promotes improvements.  
-Verify responses procedures exists and aknowledged by the ops.   

**As IT security experts, we aim to safeguard the supply chain segment used for training our LLM from compromise. How to do that?**  
-Verifying the trustfullness of the source.  
-Check Hash Values.  
-Understand how the provider of a data set performs cleaning and sanitazation before releasing it.  
-Use encrypted chanels to download data set.  
-Check Terms & Conditions and data privacy policies.  
  
**As IT security experts, we want to ensure the developement environement does not present vulnerabilities leading to data poisoning. How to do that?**  
-Check the data sets sources during pre-training, fine tuning and embedding stages.  
-Ensure proper sandboxing and internet isolation if needed.  
-Check whether filters, data sanitazation and cleaning recipes exists to ensure a sufficient data quality.  
-Check whether label verification process is approved and reviewed by two individuals.
-Check the access permissions for the different development environments and ensure that the isolation between the DEV and PRD env' is preserved.  
-Ensure a yardstick / benchmark exists to assess the maturity of the product.  
-Verify whether test to detect signs of a poisoning attack by analyzing model behavior is implemented. 


**As IT security expert we want to ensure that RLHF, part of the change management process lead to the creation of a sane genAI solution. How to do that?**  
-Assessing the security of the feedback mechanism.  
-Control the potential impact of model updates based on human feedback on security and privacy.  
-Assess processes used in the protection of user data.  
-Ensure third parties used to train the data are ethics and moral (see kenya workers controverse for OpenAI)  
-Assess the key configurations parameters like objectives functions, Weights and Biases, hyperparameters; ensure those are configured based on a rational approach.  
-Verify whether documentation for end users is clear and accessible.  
-Check that the datasets chosen for benchmarking are reliable and fit the use case.  
-Verify whether humans part of the training process are not the same than those who are part of the evaluation process.   
-Check whether changes are documented.  

**As IT security expert we want to ensure that generic change management processes lead to the creation of a sane genAI solution. How to do that?**  
-Check the quality of the Change Request Process, this should includes submitting, reviewing and approving change requests.  
-Verify whether deployment methodology exists and the impact for deploying solution in production is measured and detailed.  
-Check whether version controls exists.  
-Assess the implementation of the development and production pipelines. (Unit tests, integration tests and perf' evaluation)  
-Check how stakeholders are involved, to keep in sync with expectations.  
-Verify documentation exists.  
-Verify whether a monitoring and a feedback process are set up and how it supports future improvements.  
-Check whether the solution complies with relevant regulations, laws and acts. (ex: EU act)  

**As IT security expert we want to ensure that our genAI solution is used based on the philosophy it has been developped on. How to do that?**  
-Get an insight about incident and support tickets, do corellation with poor documentation, training, not working examples...  
-Verify whether documentation follow the life cycle of the project when the it is updated for example.  
-Assess the user interface and verify whether it is accessible and implemented according business needs.  
-Check whether relevant and contextual examples are provided.  
-Verify how is handle feedbacks and supports and how it is taken into account in the Life Cycle Management of the product.  
-Measure the community involvement, more the community is involved less the support is needed as people help each others.  
-Check whether free training on how to use the solution with use cases is provided.  

## TLDR  
  
**As IT security experts, we want to ensure plugins, extensions and agents are risks-free. How to do that?**  
-Assess peer-trust, if there are multiples plugins and whether they communicate between themselves.  
-Evaluate whether IAM is the same as designed before and after a plugin installation.  
-Verify whether plugins have been scanned using static and dynamic analysis.  
-Verify whether plugins rewuire manual human approval before executing any sensitive action.  
-Check whether plugin APIs keys rotation exists.  
-Check if some plugins are disabled and not necessary anymore - plugin decommissioning.  

    
**As IT security experts, we want to ensure direct prompt injections would not put our system at risk. How to do that?**  
[!] : We still are at the beginning of genAI era; huge commercial solutions like chatGPT are mainly relying on Reinforcement learning with human feedback, in other words there is no security framework at the moment.  
-Verify whether the solution implement human feedback loop by relying on responsible vulnerability disclosure.  
-Assess the design.  
-Check whether Reinforcement Learning from Human Feedback is in place.  
-Assess filtering components.  
-Check whether self reminder is set up for the system message.  
-Verify a LLM moderator is used, like a web firewall to protect the web attacks.  
-Check whether interpretability-based solutions that perform outlier detection of prediction trajectories are used.  

**As IT security experts, we want to ensure indirect prompt injections would not put our system at risk. How to do that?**  
-Assess the design the solution, check external agents, plugins or extensions.  
-Check if an inventory of extensions capabilities exists.  
-Assess approval mechanisms; Require user approval before performing privileged operations like sending or deleting emails.  
-Verify if the solution follow the principle of least privilege by restricting the LLM to only the minimum level of access necessary for its intended operations.  
-Check filtering; Processing the retrieved inputs to filter out instruction.*  
-Assess whether the solution is monitored and how developers are using the logs, user inputs to enhance security.  
  
*This solution has been provided by the researcher Kai Greshake through his paper "Not what you’ve signed up for: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection". **I personally think this solution would be counter-productive**, he himself expresses doubts about its usefulness but I wanted to let it here to give you a different type of insight.  

**As IT security expert we want to ensure that our GenAI solution is not over exposing services. How to do that?**  
-Assess the network architecture of the GenAI solution  
-Check whether ports are open using ps -ef, lsof -i or netcat, wireshark or any other tool you're familiar with.  
-If ports need to be internet exposed, verify whether a restriction mechanisms is set up.  
-Check whether default credentials are not in used and strong password/certificates policies is in place.  

**As IT security expert we want to ensure that our GenAI solution is not disclosing any training data. How to do that?**  -> you can't but...  
-Check whether the model has been pre-trained for too many epochs.  
-Verify whether the model cannot be subject to divergence attacks and membership inference attacks.  
-Verify if training data has been anonymized.   
-Testers should test for discoverable memorization overall.    
-Understand and assess how alignment has succeeded in the training phase.  
-Check if model obfuscation is implemented (generated responses).  
-Verify the implementation of robust input validation and sanitization methods.  
-Access to external data sources at runtime should be limited.

**As IT security experts, we want to ensure our plugins are supplied by reliable sources. How to do that?**  
-Check the vendor reputation.  
-Assess the extent and the quality of the documentation.  
-Verify whether the provider is releasing regular updates and patches.  
-Assess whether it complies with standards and regulations for further use.  
-Assess the feedback and reviews.  
-0.1.1 Supply chain security provide a set of additional controls.  

**As IT security experts, we want to ensure plugins, extensions are properly integrated into our genAI solution. How to do that?**  
-Understand and check integration points (Identify how the plugin will interact with the different components of the solution like APIs or other plugins.)  
-Check whether the plugin has been tested in a sandbox.  
-Verify whether plugins configuration correspond to the security baseline or policies.  
-Verify that permissions and authorizations have been limited to the scope.  
-Assess the environment isolation, how each components, plugins are isolated and interract with each others.  
-Check whether logging and monitoring is set up to detect anomaly.  
-Verify how developers and incidents handlers cope with detected anomalies.  

