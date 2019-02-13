# plant_uml Library Requirements

This document presents the software requirements specifications for this library in accordance with [IEC62304](#ref1). Requirements are grouped in accordance to the structure that is defined in paragraph 5.2.2 'Software requirements content' of [IEC62304](#ref1).

## Revision log

### 2019-02-11 Revision 0 - version 0.1.0.1 (2019-02-07)

Initial version.

## Conventions

### Verification methods

| Term              | Definition                                                                   |
| ----------------- | ---------------------------------------------------------------------------- |
| Inspection (I)    | Control or visual verification                                               |
| Analysis (A)      | Verification based upon analytical evidences                                 |
| Test (T)          | Verification of quantitative characteristics with quantitative measurement   |
| Demonstration (D) | Verification of operational characteristics without quantitative measurement |

### Requirements naming and definitions

Requirements listed in this document are constructed according to the following structure:

| **Requirement ID**  | **REQ-XXX-nnn**                    |
| ------------------- | ---------------------------------- |
| Title               | Title of XXX-nnn requirement       |
| Description         | Description of XXX-nnn requirement |
| Verification method | I / A / T / D (see table above)    |

## Functional and capability requirements

These requirements describe the functional requirements of the product that is to be developed. These are, for example, requirements on purpose of the software, coding language, platform and OS requirements.

## REQ-FUN-L001

**Title**: PlantUML Extention

**Description**: The software is intended to be the plug-in style extention to the PlantUML syntax. As such it should be itself written in PlantUML as a set of parameteric macroses.

**Verification method**: A

## REQ-FUN-P001

**Title**: Platform Compatibility

**Description**: The software should be operational on any PC with x64 architecture in both MS Windows 7+ and Linux OS, providing that the PlantUML application and all its dependencies are installed.

**Verification method**: D

## REQ-FUN-F001

**Title**: Syntax Sugar

**Description**: The software should provide shorter and clearer syntax for the commonly used PlantUML constructs, such as class stereotype and attributes decorators, components decorators, relational links between classes / components, etc.

**Verification method**: A

## REQ-FUN-F002

**Title**: Class Diagram Classes Stereotypes

**Description**: Syntax for creation consistent class decorators for specific classes: generic (abstract), singleton, prototype, (left / right) mixin.

**Verification method**: D

## REQ-FUN-F003

**Title**: Class Diagram Attributes Decorators

**Description**: Replacement for the {static} and {abstract} standard PlantUML decorators / modifiers, such that only the name of the attribute is affect, not the entire definition line

**Verification method**: D

## REQ-FUN-F004

**Title**: Component Diagram Custom Components

**Description**: Syntax for creation of the custom components, based on the standard ones, with the clear indication of their types using the stereotypes. The syntax should cover the situations, when the actual component names and its display name are the same, and when they are different. The required minimum amount of the custom components is:

* class, function and file - based on the common component
* module - based on the frame component
* package and library - based on the package component
* pc - based on the node component

**Verification method**: D

## REQ-FUN-F005

**Title**: Database Data Model as Modified Class Diagram

**Definition**: The software should provide syntax for creation of the graphical representation of the data model of a database using modified class diagram (with the custom skins). It should be able to represent the actual object (tables and views, fields therein) as well as the relations between them.

**Verification method**: D

## REQ-FUN-F006

**Title**: Database objects as classes

**Definition**: The syntax for the graphical representation of the following objects should be provided:

* Tables
* Views
* Queries (as parts of the complex SELECT constructs, e.g. for the views creation), including the special cases of
  - Joins
  - Set operations: union, intersection, exception

These representations should be based on the class template with the specific and clear indication of their type using the letter in the coloured circle and stereotypes.

**Verification method**: D

## REQ-FUN-F007

**Title**: Relation between Objects

**Definition**: The software should provide syntax for displaying the following relations:

* '1 to 1' and '1 to many' relation between two tables (foreign key, referencing)
* 'consists of' relation between the query (joins, unions, intersections and exceptions) and their left and right arguments with the clear indication which part is left, and which is right
* in the case of the joins, except for the cross-join, the fields by which the join is made should also be indicated

**Verification method**: D

## REQ-FUN-F008

**Title**: Naming of the Objects

**Definition**: Each diagram component corresponding to the graphical representation of any database object (table, view, query) should have a name, which can be used for creation of the links (relations) between the objects, but it does not have to be same as the display name, shown on the graphical representation itself. In fact, the following constrains are applied:

* Tables and views must have the same display and actual component names
* Queries may be created with or without the display name; the display name does not have to coincide with the actual component name
* Joins, unions, intersection and exceptions must be created without the display name

**Verification method**: D

## REQ-FUN-F009

**Title**: Primary and Foreign Keys

**Definition**: Simple syntax for creation of the primary and foreign keys decorators for the table (class) attributes with the following constrains:

* primary keys - auto generated, interger or small integer
* foreing keys - integer or small integer, unique (1 to 1 relation) or not unique (1 to many relation), not nullable

**Verification method**: D

## Software system inputs and outputs

These requirements describe the software in- and output format, ranges, limits, defaults, etc.

### REQ-SIO-F001

**Title**: No Input and Output Files

**Description**: The software should not require any input data or configuration files. The software should not generate any files on its own. The rendering of the diagrams should be performed by the PlantUML application.

**Verification method**: D

### REQ-SIO-F002

**Title**: Software Modules Format

**Description**: The modules of the library providing the actual functionality must be in the form of ASCII text files, which include the PlantUML source code but not the complete diagram definition. In other words - the syntax is correct, but the diagram cannot be generated. These modules should have '.cuml' extention.

**Verification method**: A

## Interfaces

These requirements describe the interfaces between the software system and other systems.

### REQ-INT-R001

**Title**: PlantUML Compatibility

**Description**: Source code of a diagram utilizing the functionality added by this software should be properly rendered by either the stand-alone PlantUML application (plantuml.jar, version 1.2018.08 or older) or within an IDE incorporating PlantUML as long as the syntax of the diagram is correct and conforms with the PlantUML syntax in general.

**Verification method**: D

## Alarms, warnings and operator messages

These requirements describe the software driven alarms, warnings, messages, etc.

### REQ-AWM-E001

**Title**: Errors

**Description**: The software is not required to generate own error messages or alarms. The syntax errors in the source code of a diagram should be treated by the PlantUML software itself.

**Verification method**: D

## Security requirements

Security related requirements are described here.

Not applicable because the library is not a part of or designed to be used with medical devices. The software requirements analysis model based on the [IEC62304](#ref1) is used for the convenience only.

## Usability requirements

These requirements describe the manual operations when using this software, personel constrains, etc.

### REQ-USE-U001

**Title**: Mode of Operation

**Description**: The software is to be used by qualified personel, who is familiar with the PlantUML syntax, whereas no other specific programming skills are required. When a specific functionality implemented by this software is required, the user should reference the respective module in the source code of its diagram; after that the functionality implemented in that specific module(s) should be available. Thus, the intended mode of operation is 'on demand'.

**Verification method**: D

## Installation and acceptance requirements

These requirements describe how the software is to be distributed and installed at operation or maintenance sites.

### REQ-IAR-I001

**Title**: Installation process

**Description**: The software does not require an installer program. In order to "install" the software, a user is expected to check-out it from the Git repository or simply copy it from another installation.

**Verification method**: D

## User documentation requirements

Requirements on the development of user documentation are described here.

### REQ-UDR-D001

**Title**: User Manual

**Description**: A user manual must be provided with the library, in which the sufficient information on the installation and usage of the library should be given, including the reference on the available macroses, their syntax and intended use.

**Verification method**: A

### REQ-UDR-D002

**Title**: Inline Documentation

**Description**: The provided modules must include inline documentation on their usage and syntax.

**Verification method**: A

## Regulatory requirements

Regulatory requirements are described here.

Not applicable because the library is not a part of or designed to be used with medical devices. The software requirements analysis model based on the [IEC62304](#ref1) is used for the convenience only.

## References

<a id="ref1">[IEC62304]</a> [NEN-EN-IEC 62304:2006](https://www.nen.nl/NEN-Shop/Norm/NENENIEC-623042006A12015-en.htm)