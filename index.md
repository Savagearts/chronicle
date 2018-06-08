## Repository Meta Model
Repository meta model describes the M1 model will be applied for a distributed data repository. It doesn't include the configuration information that will be applied in run-time.  Instead, this meta model just describes the meta information that will be used in the run-time engine without run-time environment consideration. We may apply another chapter to describe the run-time configuration description. The repository meta model can be fall into three parts:
 - Type System Part
 > The Type System model describes the data structure that will be managed by the repository. It includes model of the aggregates structure  are managed by the repository.  It also provides the common capabilities to describe the data structure that used in different scenarios, for instances the argument and the result set.  
 >
 - Operation Model 
> Operation model part describes the behaviors the repositories are in charge of. The operations describe the intention from the consumer side. It describes the intention that the consumer want the repositories to provide. For instances, the CRDU (create/read/update/delete) capabilities. The operation model may be optional.   
 - Directives for  Type System and Operation Model
 > Directive meta description for the repository model (the type system and the operation model). The meta descriptions are applied in the run-time  to instruct the engine or the model transformer to do additional task.
 >
###  Type System
1.  
### Operation Model   

