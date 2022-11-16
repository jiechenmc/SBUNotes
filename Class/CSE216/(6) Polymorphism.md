#concept #java 

>[!info] 
>"Diamond Problem" is a result of multiple inheritance
>Java enforces **single inheritance**

# Parameterized Types \<T\>

### Type Erasure
	- Generate a new representation for every instantiation of a generic type or function; yielding the raw type; for example List<String>
	- C# use this for non reference data types
	- C++ use it for templates

>[!info]
>Generics are compile time construct; they will undergo type erasure at compile time

>[!tip]
>If A is a subtype of B, and R is a parameterized type;
>R\<A\> is not a subtype of R\<B\>

### Declaring Parameterized Types
```java
public <T> T func(T arg){};
// <T> declares the parameterized type, T
```

>[!info]
>```java
>? extends T
>// T and its subtypes

>[!info]
>```java
>? super T
>// T and its supertypes
