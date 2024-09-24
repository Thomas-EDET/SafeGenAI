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


### 4 - Example of content you will find: 
#### Change Management for genAI
[...]

<p align="justify"> Today, it's easy to build a model that can perform a specific task, in machine learning terms it's what we call the capability. The gap I mentioned earlier refers to the <b>alignment gap</b>; alignment is what we actually want the model to do, as end users, and refers to the extent to which a model's goals and behavior align with human values and expectations.   </p>

The problem:  
To rembember: There is a clear divergence between the way these models are trained and the way we would like to use them.

<p align="center">
    <img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/alignmentandcapabilities.png" />
</p>    

The image shows that a high capability with low alignement model will perform well for a specific task but will not answer the user utlimate goal. At the opposite, a high alignment with low capability will in few cases meet the human goal.

Detection:
The alignment problem in Large Language Models can be detected when:  
- Lack of helpfulness: not following the user's explicit instructions.  
- Lack of interpretability: it is difficult for humans to understand how the model arrived at a particular decision or prediction.  

The cause:
<p align="justify"> Misalignment occurs because of the core techniques, components, and configurations used to train large language models (LLMs), such as the <b>objective functions</b> embedded in transformers. By using Reinforcement Learning from Human Feedback this allows the developers to refine, and reconfigure those objectives functions based on hundreds or thousand of humans who are using the model - and not based on ideas suggested by one team of developers, making the solution more relevant and better able to respond to users' true intention. </p>

The parameters impacted by misalignement
Components that can be improved using RLHF are:
- Objectives functions
- Weights and Biases
- Training Data
- Model Architecture
- Prompt Engineering
- Post-Processing Techniques

RLHF used by chatGPT:

For users using chatgpt like me we've all seen this : 
<p align="center">
    <img src="https://github.com/Thomas-EDET/SafeGenAI/blob/main/images/humanfeedback.png" />
</p>    

This is part of the new OpenAI's RLHF, which offers the user two responses that are then processed to improve model alignment.  
  
Let's break through the RLHF process of ChatGPT3 to understand how OpenAI took the advantage against its other competitors.

[...]
