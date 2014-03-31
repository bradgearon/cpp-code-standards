# C++ Code Standards
----------------------------------------------------
## Object Lifetime

#### Use smart pointers
+ Don't manage memory, manage objects: objects manage resources
+ Only use memory allocation when you are implementing hardware
+ Use the most appropriate smart pointer type: unique if you will need only one reference; shared if you will share it

#### Don't allocate memory using global functions
+ Use new instead of alloc and dealloc

#### Encapsulate resources 
+ Use smart pointer instance members
+ Use initialization lists, allocate resources in constructors
+ Release resources in destructors

#### Use copy and move for smart pointers
+ Copy when resources will be used in both the destination and the source
+ Move when resources will be used only in the destination scope
  Additional notes on values and copy/move: http://msdn.microsoft.com/en-us/library/hh438479.aspx
	
#### Use stack based scope / lifetime before heap
+ Declare variables and members at the top of the scope in which they are used
+ Data member lifetime is virtually overhead free (no, there is no garbage collector)
+ Maintainability and simplification (stack) valued over tiny performance gain (heap); also helps eliminate memory leaks

#### Copy constructors should be avoided

## Type definitions

#### Don't use multiple inheritance
+ Confusing; rarely useful

#### Delegate "chain" constructors

#### Don't hide types with variable names
+ C++ allows you to replace a type name with a variable name.. Don't.

#### Names of types, variables, methods, and data members should be meaningful
+ Only widely used abbreviations
+ Underscores should only appear in constants

#### Use pimpl for dependencies (pointer to implementation)
+ http://msdn.microsoft.com/en-us/library/vstudio/hh438477(v=vs.110).aspx
	
#### Namespace your things
+ Don't mess with global namespace... no one else does, why should you

#### Method declaration should not be included in class definitions

#### Use strongly-typed enums
+ enum class vs enum; eliminates potential collisions

## Containers

#### Use range-based for statement
+ Use std::begin and std::end for types that don't already have these
+ Iterator should be marked as constant, especially (and you really shouldn't do this) if you are not replacing a reference in your loop

#### Use appropriate std containers
+ For example: array for fixed size collection; vector, list, map, etc for dynamic
+ Use list for quick insert / removal
+ Use vector if you need random access
+ Use map for lookups
+ Don't be afraid to use smart pointer types as element type
	
#### Use map for associative collections
+ Do not use pointers or complex types for keys
+ Use make_pair for constructing pairs

## Algorithms / Logic

#### Use std algorithms library
+ When a standard algorithm implementation exists for given logic, it should be used instead of writing said logic

## Data Members and variables

#### Use auto for locally scoped variables
+ Reduces redundancy and increases readability
	
#### Use complex argument types over argument lists

#### Use nullptr
+ Don't initialize things to 0

## Threading

#### Minimize use of operating system objects
+ Use atomic types and flags over mutex; use std:mutex over platform specific

#### Use threading efficiently
+ Spawn threads only when they will / can be used: default thread implementation does not consider resources
	
#### Do not use volatile keyword for non-atomic access to variables
+ Operations on volatile variables are not atomic and do not define behavior useful for threading
+ Use atomic types and mutex

## Assertions and Exceptions

#### Use type traits
+ Compile time type queries
+ Static assertions
	
#### Throw and handle exceptions for error condition



