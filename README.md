# Knowledge Distillation- experiment of idea on turning domain expert language model to domain and language expert LM 

### Goal  
Given a scientific task and a teacher model(large LLM) that is capable at handling language but is not trained on scientific tasks (not a specialist), can we train/use a student model that is very good at this task and learn the language capabilities from the teacher model through knowledge distillation and still outperform the teacher model at the scientific task?  
- Improving the performance of drug editing on Large Language Models by training a domain expert model then giving language capabilities through knowledge distillation 
- Make any domain oriented (tasks that would benefit from good conversation capabilities) language model into more general yet still accurate language model 

### Problem Formulation 
- Problem Statement: Traditionally, drug editing relies on feedback and prompting to get good results from existing LLMs. How can we train a student model that's an expert on certain drug editing tasks (such as making a molecule more soluble in water), and improve its language capabilities through Knowledge Distillation? 
- Student Model Training: Decide a scientific task, input data from a dataset like ZINC, train the student model to be good at executing that task through loss functions like Cross Entropy. 
- Knowledge Distillation Training: Study the training process of DDK paper, how to distill the language abilities to the student model?  

### Methodology 
Teacher Model:    
Student Model:  
- Train the student model to be good at a specific drug editing task (details incoming) 
- Evaluate how good this student model has become   
- Choose a teacher model and use knowledge distillation to improve the language capabilities of the student model (what this means needs more discussion and how to do this involves Engineering) 
- Evaluate improved language  

### Task Selection & Motivation: Drug Editing
Our student model needs to be good at a specific task, and the selection of this task directs what the outcome of knowledge distillation is.  
- The task we will focus on is **drug editing**. Drug Editing is the scientific task that would benefit the most from having language model because of its iterative process through conversations. 
- Drug editing has commonly been done with pre-trained LLMs like ChatGPT, and finding ways to optimize performance with these LLMs. Several techniques have been proposed to do this including RL_Guider (use RL to guide the best prompts), ChemReasoner (use another LLM to cross check), using existing knowledge base to do search. **No methods have been proposed to use a trained domain expert model and get language capabilities to do conversations through Knowledge Distillation** 
- For example, if our student model has a lot of knowledge on structural validity/similarity but does not have enough training to answer prompts, after knowledge distillation, it should be able to understand prompts and answer if a given structure is valid? 
  
### Training Student Model on Expert Performance 
- Which Task from drug editing?   

#### Our method vs. RL Guider 
- RL Guider uses past feedback to train a Reinforcement Learning model that gives the best prompt to an existing LLM for better drug editing performance 
- **Our method does not directly involve feedback and prompting.** We train a domain expert small LM and use knowledge distillation to give it good language skills while retaining the domain expertise performance. 
- Our method *currently* does not use RL to keep in track of feedback from a LLM because we will not be prompting to a LLM 
- RL Guider maximizes the drug editing performance by optimizing prompts, we maximize the performance by having an expert student model 
- Our method does not dependent on an existing LLM (chatGPT, DeepSeek)'s ability to do drug editing (we also don't know their training data), because we can train a student model with our data and we can better evaluate its performance at drug editing before and after training, which is not something that other papers have done before. 
- Most papers in drug editing involves prompting and feedback to a LLM, our method bypasses the prompting by directly training an expert student model, then let it have the conversation abilities through Knowledge Distillation. This part of training to have an expert model is not done before. **Our performance of drug editing is directly related to how much knowledge the student model has before and after knowledge distillation. It is not dependent on how good a pretrained LLM is or how good that LLM is at incorporating prompt feedback.**  
  
### Our method vs. DDK 

### Our method vs. Finetuning Approaches 

### Choosing a Student Model (Open Source)   
The student model must possess a lot of specific domain knowledge to a specific task (such as drug editing, or even more specifically--telling structural similarity, validity, etc.).   
 
- **Since we are doing drug editing, we need a student model that already has a lot of language capabilities, so that knowledge distillation from a teacher model is easier?**   
- Choice 1: A general transformer-based Language Model with small # of parameters. 
    - Pretrained, so we will need to know how to finetune to our data. 
    - Won't possess deep knowledge/expertise in a task beforehand.  
    - **Can we train a small LM to be good at drug editing? (No conversations/feedback, mainly through training with ground truth data)** 
- Choice 2: A domain expert model that is designed/trained on a specific scientific task (i.e. Chemformer, ChemBert, MolGPT, etc.)
    - We can take the architecture then train from scratch or finetune (if weights are opensourced)
    - Need to find a specific task to determine which model to use. 
  
### Model Candidates 
- Teacher Model: Qwen, Llama
- Student Model: 
  
### Problems to Resolve: 
- How to define language capabilities and quantify we have improved? 
    - Cross compare with existing LLMs like GPT with multiple rounds of conversation 
    - Test reasoning capabilities: Chain of thought; give an answer and ask it to explain the process. 
- How to train the student model to perform well on drug editing? And how to train this? 
- Can knowledge distillation improve language capabilities? 
- What tasks to use from drug editing? And find corresponding data for those for training. 
- How does the knowledge distillation training process work? 


### Steps needed: 
- [x] Read the ACL paper to understand how to use Language Model on scientific tasks, and the different tasks we can potentially use for this project.   
- [x] Select a task to handle 
- [ ] Literature search: Find similar papers that used     
    - Knowledge Distillation to train student model to get language capabilities 
    - Specialist model at chemistry/material science/other kinds of scientific knowledge
    - Pre-trained models that are successful at doing specific tasks (ex: Chemformer, MolGPT). We might need these as the student model (No models found)
- [ ] Select specific tasks from drug editing to use (start with ACL paper)
- [ ] Student Model search   
- [ ] Teacher Model search  
- [ ] Find suitable datasets 
- [ ] Train the student model to be good at the specific drug editing tasks 
- [ ] Use knowledge distillation to improve model language abilities 
- [ ] Testing with other models with metrics   
  
### References 
- Look at Knowledge Distillation Papers (DDK, MiniLLM ...) to know the training techniques for knowledge distillation (loss function, training loader ...)
- Look at different drug editing paper (RL Guider, ChemReasoner) to decide how to train a successful base student model 