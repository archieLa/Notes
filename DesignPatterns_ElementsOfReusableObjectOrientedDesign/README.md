# Creational patterns
## Benefits
- encapsulate knowledge about which conctete classes system uses
- hide how instances of these classes are created and put together
- instruct how to make design more flexible but not necessary smaller
## Abstract factory
Exposes interface for creating dependent objects without specifying concrete classes
### Aplicability
- when system needs to be configure with family of objects e.g. family of drivers or widgets
- when there is direct dependencies between objects of the family and they have to be used as a group
- you want to hide implementations of library of products and expose interface only
### Diagram
![abstractFactory image](uml/AbstractFactory.png?)