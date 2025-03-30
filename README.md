# Knowledge Distillation- experiment of idea on turning domain expert language model to domain and language expert LM 

### Goal  
Given a scientific task and a teacher model(large LLM) that is capable at handling language but is not trained on scientific tasks (not a specialist), can we train/use a student model that is very good at this task and learn the language capabilities from the teacher model through knowledge distillation and still outperform the teacher model at the scientific task?  
- Improving the performance of drug editing on Large Language Models by training a domain expert model then giving language capabilities through knowledge distillation 
- Make any domain oriented (tasks that would benefit from good conversation capabilities) language model into more general yet still accurate language model 

### Methodology 
Teacher Model: TBD   
Student Model: TBD   

### Task Selection & Motivation: Drug Editing
Our student model needs to be good at a specific task, and the selection of this task directs what the outcome of knowledge distillation is.  
- The task we will focus on is **drug editing**. Drug Editing is the scientific task that would benefit the most from having language model because of its iterative process through conversations. 
- Drug editing has commonly been done with pre-trained LLMs like ChatGPT, and finding ways to optimize performance with these LLMs. Several techniques have been proposed to do this including RL_Guider (use RL to guide the best prompts), ChemReasoner (use another LLM to cross check), using existing knowledge base to do search. **No methods have been proposed to use a trained domain expert model and get language capabilities to do conversations through Knowledge Distillation** 
- For example, if our student model has a lot of knowledge on structural validity/similarity but does not have enough training to answer prompts, after knowledge distillation, it should be able to understand prompts and answer if a given structure is valid? 
  
### Choosing a Student Model  
The student model must possess a lot of specific domain knowledge to a specific task (such as drug editing, or even more specifically--telling structural similarity, validity, etc.). The student model will most likely be trained to be good at such task. Then we can use knowledge distillation with the teacher model to learn extra general chemistry knowledge and conversational/language skills.  
- **Since we are doing drug editing, we need a student model that already has a lot of language capabilities, so that knowledge distillation from a teacher model is easier?**   
- Choice 1: A general Language Model with small # of parameters. 
    - Pretrained, so we will need to know how to finetune to our data. 
    - Won't possess deep knowledge/expertise in a task beforehand.  
    - **Can we train a small LM to be good at drug editing? (No conversations/feedback, mainly through training with ground truth data)**
- Choice 2: A domain expert model that is designed/trained on a specific scientific task (i.e. Chemformer, ChemBert, MolGPT, etc.)
    - We can take the architecture then train from scratch or finetune (if weights are opensourced)
    - Need to find a specific task to determine which model to use. 
  
### Model Candidates 
- Teacher Model:  
- Student Model: 
  
### Problems to Resolve: 
- Which scientific task do we want the student model to have expertise in? 
- How does the knowledge distillation training work? 


### Steps needed: 
- [x] Read the ACL paper to understand how to use Language Model on scientific tasks, and the different tasks we can potentially use for this project.   
- [x] Select a task to handle 
- [ ] Literature search: Find similar papers that used     
    - Knowledge Distillation to train student model to get language capabilities 
    - Specialist model at chemistry/material science/other kinds of scientific knowledge
    - Pre-trained models that are successful at doing specific tasks (ex: Chemformer, MolGPT). We might need these as the student model 

- [ ] Student Model search   
- [ ] Teacher Model search  
- [ ] Task 1