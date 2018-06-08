## Repository Meta Model
Repository meta model describes the M1 model will be applied for a distributed data repository. It doesn't include the configuration information that will be applied in run-time.  Instead, this meta model just describes the meta information that will be used in the run-time engine without run-time environment consideration. We may apply another chapter to describe the run-time configuration description. The repository meta model can be fall into three parts:
 - Data Structure Model
 > The Data Structure  model describes the data structure that will be managed by the repository. It includes model of the aggregates structure  are managed by the repository.  It also provides the common capabilities to describe the data structure that used in different scenarios, for instances the argument and the result set.  
 >
 - Operation Model 
> Operation model part describes the behaviors the repositories are in charge of. The operations describe the intention from the consumer side. It describes the intention that the consumer want the repositories to provide. For instances, the CRDU (create/read/update/delete) capabilities. The operation model may be optional.   
 - Directives for  Type System and Operation Model
 > Directive meta description for the repository model (the type system and the operation model). The meta descriptions are applied in the run-time  to instruct the engine or the model transformer to do additional task.
 >
###  Type System
A type definition is the cornerstone of the system. It describe the system' s structure and the behaviors.  A type system can fall into two parts: the __initial type__ and __developer defined types__:
1. __initial type__: There are three __initial types__: __Query, Mutation and Subscription__.  The three types are the built-in types that you can't change the type's name. But our developers can define the fields of the type.  The __initial types__ definition are actually the system behaviors definition. Without the __initial types__ definition, the system will provide no behaviors. In other words, If we want to define the system's behaviors, we should define the fields for the __initial types__. 
>A typical query type definition and example as following:
```
type Query{
   student(age: Int!): [Student]
   classes(grade: Int!):[Class]
}
With the query type definition, we can apply query language to get the information from the server side:
query{
	student(10)
	{
		name
		grade
	}
}
```
2. The other types: Except initial types, the other types define the data structures and behaviors used by the initial types. 
>A typical type definition and example as following:
```
type Student{
   name: String!
   age: Int!
   grade: Grade!
   classes:[Class]!
}
With the Student type definition, we can apply query language to get the student's name and grade from the repository. Otherwise we can't wirte the query selection set with field name and grade. 
```
### Type Definition
1. Primitive (scalar) Types: As expected by the name, a primitive type represents a primitive value in repository.  Repository responses take the form of a hierarchical tree; the leaves on these trees are primitive types.
1.1 Int:A signed 32‐bit integer
1.2 Float: A signed double-precision numeric value
1.3 String: A UTF‐8 character sequence
1.4 Boolean: `true` or `false`.
1.5 ID: The ID type represents a unique identifier, often used to refetch an object or as the key for a cache. The ID type is serialized in the same way as a String; however, defining it as an `ID` signifies that it is not intended to be human‐readable
1.6 Customized Primitive Type: we may extend the built-in primitive types for simply development scenario usages. If we declare expression as following:
```
scalar IPV4
```
In other  type definition, we can use the __IPV4__ as the built-in primitive type:
```
	type IPResource{
		id: ID!
		name:String!
		ip: IPV4!
		...
	}
```
2. Objects: A hierarchical and composed information structure definition that  represent a list of named fields, each of which yield a value of a specific type. Object values should be serialized as ordered maps, where the queried field names (or aliases) are the keys and the result of evaluating the field is the value, ordered by the order in which they appear in the query. For an instance, a typed Person can be defined as following
```
type Person {# The type for Person
  name: String #field for Person 
  age: Int     #field for person
  picture: Url #field for person
}
```
4. __Object Type__ and __Field__
The most basic components of Type Definition are object types, which just represent a kind of object you can fetch from repository, and what fields it has. In the type definition system, we might represent it like this
```
type Character {
  name: String!
  appearsIn: [Episode]!
}
```
5. The primitive types: the primitive types define the 
a. 
 

