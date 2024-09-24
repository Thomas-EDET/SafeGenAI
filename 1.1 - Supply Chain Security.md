## TLDR
**As IT security expert we want to ensure that the business requirements led to the creation of a sane genAI solution. How to do that?**  
-Verifying whether the document has been approved.  
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

---  
# Supply Chain Security

Here, the supply chain security focuses on risk management of external genAI (LLM and data sets) suppliers, vendors, and other third parties.

## Risks  
Not controlling the risks for the supply chain can lead:
- Compromised data integrity and confidentiality.
- Increased vulnerability to cyber attacks and data breaches due to a large attack surface.
- Potential loss of intellectual property, this can happened if a third library is used and exploited by an attacker.  
- Disruption of operations and financial losses.  
- Regulatory non-compliance and legal consequences.  
- Damage to reputation and loss of customer trust.  

## Objective
Provide a basic set of controls to assess the maturity of the supply chain security of an AI solution along with examples and explanations.  
The controls for the supply chain security are not exhaustive and may need to be supplemented based on specific requirements and evolving threats.  

  

## General Controls for GenAI

#### 1 - The business requirements of a GenAI solution.
If your AI solution process secret data for governement, it makes sense to process the data using LLM deployed on premises and not on ChatGPT servers.  
  
The needs should be defined upstream in a business requirement like document. Understanding this document will help the architect to choose the components that fit the best to the requirements - and not depending its preferences otherwise you got something like that:
<p align="center">
    <img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/finalproduct.PNG" />
</p>    
To better illustrate why the business requirement workpaper is utterly important let's use an example; A pentesting company created a draft of business requirements and directly sent it to the developer teams.

- Project title:  
Chatbot to create audit reports.

- Overview of the project:  
The chatbot should help pentesters to create pentest reports. 

- Stakeholders and third parties involved:  
The project is being led by the in-house team of developers. No third party is involved.

- Business objective:  
 The bot should be capable of automating the writing process based on input regarding a vulnerability and its context.

- Functional requirements :  
The chatbot must use our internal vulnerability database and other internal data to create a high-performance result.  

- Non Functional requirements:  
Depending the usage, we want to free instances in order to get them back in the bruteforce cluster.  

- Constraints:  
The purchase budget is limited to 1000 euros.

- Risks:  
We don't want our vulnerability database compromise or internal data being leaked.  

- Assumptions:  
Limit the acessibility of the solution to the internal network of the company.

From this terrible example, we can speculate on 2 points of the architecture:  
  
Chatbot Interface: User interacts with the chatbot to input vulnerability details and context.  
Problem -> This may be a CLI, GUI or even by voice as the functional requirements are not explicitely mentionning how the pentesters should interract with the chatbot.  

Data Retrieval Module: Accesses internal vulnerability database and other relevant data sources.  
Problem -> The solution may be developed to embed an LLM extension like a SQLtoolkit to query the database on live while opting for a RAG chatbot would've been prefered and sufficient. 
  
The business requirement document should limit the options available for creating a solution, which was not done previously.

**As IT security expert we want to ensure that the business requirements led to the creation of a sane genAI solution. How to do that?**  
-Verifying whether the document has been approved.  
-Checking the table of content, good indicator for the overall quality of the document.  
-Gather comprehensive business requirements - ask stakeholders to clarify when details are missing.  
-Ensure that the requirements are specific, measurable, achievable, relevant, and time-bound.  
-Ask whether a Risk Assessment has been conducted and verify content.  
-Ensure that the technology aligns with the security needs of the GenAI solution. 


To ensure supply chain security, it is essential to understand the detailed needs of businesses and to have a team that understands them. Let's explore key components of a common genAI solution to enhance our supply chain further.

#### 2 - The LLM of a genAI solution

The LLM is the core of every genAI solution.

It's very easy to download and use infected LLM as described by PoisonGPT:

<p align="center">
    <img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/poisongpt.PNG" />
</p>    

The team used impersonification to trick an end users downloading its model from Huggingface. Subsequently, students asking history questions were given the wrong answers.  

  
source: https://blog.mithrilsecurity.io/poisongpt-how-we-hid-a-lobotomized-llm-on-hugging-face-to-spread-fake-news/

**As IT security expert we want to ensure that our LLM downloaded does not embed any malicious component. How to do that?**  
-Verifying the trustfullness of the source.  
-Check Hash Values.  
-Review Dependencies.  
-Use Sandboxing and isolated environements to dissect outputs; ex: with and without internet.  
-Check Terms & Conditions and data privacy policies.  

Those controls are extremly important because the AI models cannot be 100 % verified due to the randomness generated by our GPU, by the non-determinism in the hardware and often the lack of systematic guidelines.  
Source:https://arxiv.org/pdf/2202.02326

#### 3 - The training data sets of a genAI solution

Same as you LLM, choosing a dataset is a sensitive task; some controls are identicals.

**As IT security experts, we want to make sure that our training dataset is not compromised. How to do that?**  
-Verifying the trustfullness of the source.  
-Check Hash Values.  
-Verify whether data sanitization has been performed.  
-Perform a data quality assessment.  
-Analyze the model behavior on specific test inputs and verify the corresponding outputs.  
-Use encrypted protocols to avoid MitM modification of your dataset.  
-Check your DNS settings.  
<p align="center">
<img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/dataquality.png" width="300" height="300">
</p>
source : https://www.youtube.com/watch?v=h9jf1ikcGyk - Stanford Poisoning Web-Scale Training Datasets  

  
#### 4 - Monitoring your supply chain

Vulnerabilities in the genAI supply chain are very important mainly due to pre-trained models.  
Badnet paper demonstrates how it is possible to introduce backdoors by compromising part of the supply chain -  which can lead to catastrophic results:  
  


<p align="center">
<img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/backdooreddl.png" width="500" height="500">  
</p>
In this paper, the researchers shown how to backdoor a model before deployment to misclassify the type of road signs.  
  
**As IT security expert we want to ensure an efficient monitoring of our supply chain. How to do that?**  
-Check whether clear monitoring objectives have been set up.  
-Maintain an up-to-date list of the third parties and providers used along with their access to your assets.  
-Maintain an up-to-date inventory of components used in your GenAI solution like libs, model version, plugins...  
-Check whether a patch management life cycle exists.  
-Check whether cooperation with third parties promotes improvements.  
-Verify responses procedures exists and aknowledged by the ops.   

<p align="center">
<img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/supplychain.png" width="600" height="300">
</p>
  
source : https://arxiv.org/pdf/1708.06733


