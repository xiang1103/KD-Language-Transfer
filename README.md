# Knowledge Distillation- experiment of idea on turning domain expert language model to domain and language expert LM 

### Goal  
Given a scientific task and a teacher model(large LLM) that is capable at handling language but is not trained on scientific tasks (not a specialist), can we train/use a student model that is very good at this task and learn the language capabilities from the teacher model through knowledge distillation and still outperform the teacher model at the scientific task? 

### Methodology 
Teacher Model: TBD   
Student Model:TBD    
  
### Choosing a Student Model  
The student model must possess a lot of specific domain knowledge to a specific task (such as drug editing, or even more specifically--telling structural similarity, validity, etc.). The student model will most likely be trained to be good at such task. Then we can use knowledge distillation with the teacher model to learn extra general chemistry knowledge and conversational/language skills.  
- Choice 1: A general Language Model with small # of parameters. 
    - Pretrained, so we will need to know how to finetune to our data. 
    - Won't possess deep knowledge/expertise in a task beforehand. 
- Choice 2: A domain expert model that is designed/trained on a specific scientific task (i.e. Chemformer, ChemBert, MolGPT, etc.)
    - We can take the architecture then train from scratch or finetune (if weights are opensourced)
    - Need to find a specific task to determine which model to use. 
  
### Model Candidates 
- Teacher Model:  
- Student Model: 
### Task Selection
Our student model needs to be good at a specific task, and the selection of this task directs what the outcome of knowledge distillation is.  
   - **For example, if our student model has a lot of knowledge on structural validity/similarity but does not have enough training to answer prompts, after knowledge distillation, it should be able to understand prompts and answer if a given structure is valid?** 
  
### Problems to Resolve: 
- Which scientific task do we want the student model to have expertise in? 
- How does the knowledge distillation training work? 


### Steps needed: 
- [ ] Read the ACL paper to understand how to use Language Model on scientific tasks, and the different tasks we can potentially use for this project.   
- [ ] Literature search: Find similar papers that used     
    - Knowledge Distillation to train student model to get language capabilities 
    - Specialist model at chemistry/material science/other kinds of scientific knowledge
    - Pre-trained models that are successful at doing specific tasks (ex: Chemformer, MolGPT). We might need these as the student model 

- [ ] Student Model search   
- [ ] Teacher Model search  
- [ ] Task 1