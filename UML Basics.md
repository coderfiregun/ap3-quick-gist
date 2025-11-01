https://blog.algomaster.io/p/uml-class-diagram-explained-with-examples


---

UML structure

1. Class Name
2. Attributes
3. Methods


Visibility Markers

```txt
1. + (public)
2. - (private)
3. # (protected)
4. ~ (package)
```


Attributes

```txt
visibility name: type [multiplicity] = defaultValue
```


Methods

```txt
visibility name(parameterList): returnType
```


interface

```txt
«interface» className
```


abstract class

```txt
«abstract» className
```


Enumeration

```txt
«enumeration»
```

---

Relationships

1. Association
2. Aggregation
3. Composition
4. Inheritance
5. Implementation
6. Dependency


The order from strong to weak is: 

```txt
inheritance → implementation → composition → aggregation → association → dependency
```

