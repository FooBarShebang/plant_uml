# plant_uml Library Test Plan

This document presents the software test plan for this library in which a plan is described for testing and verifying the requirements which are described in the [requirements document](./requirements.md).

Tests are grouped on their method of testing. These groupes are: Inspection (I), Analysis (A), Test (T) or Demonstration (D).

## Revision log

### 2019-02-13 Revision 0 - version 0.1.0.1 (2019-02-07)

Initial version.

### 20201-01-18 Revision 1 - version 1.0.0.0 (2021-01-18)

Added the PlantUML preprocessor based functionality in addition to the legacy code. The requirements are not changed, therefore no changes in the test plan.

## Conventions

### Verification methods

| Term              | Definition                                                                   |
| ----------------- | ---------------------------------------------------------------------------- |
| Inspection (I)    | Control or visual verification                                               |
| Analysis (A)      | Verification based upon analytical evidences                                 |
| Test (T)          | Verification of quantitative characteristics with quantitative measurement   |
| Demonstration (D) | Verification of operational characteristics without quantitative measurement |

### Tests naming and definitions

Each test is defined following the same format. Each test receives a unique test identifier and a reference to the IDs of the requirements it covers (if applicable). The goal of the test is described to clarify what is to be tested. The test steps are described in brief, but clear instructions per test are defined as well as what the expected result is for a test to pass. Finally, the test result is given, this can only be pass or fail.

The test format is as follows:

**Test identifier**: TEST-[I/A/D/T]-xxx

**Requirement ID(s)**: REQ-XXX-nnn

**Verification method**: I/A/D/T

**Test goal**: Description of what is to be tested

**Expected result**: What test result is expected for the test to pass

**Test steps**: Step by step instruction of how to perform the test

**Test result**: PASS / FAIL (To be filled in the test report)

## Test definitions (Test)

None.

## Test definitions (Demonstration)

**Test identifier**: TEST-D-001

**Requirement ID(s)**: REQ-FUN-P001, REQ-SIO-F001, REQ-INT-R001, REQ-AWM-E001, REQ-USE-U001, REQ-IAR-I001

**Verification method**: D

**Test goal**: Software usability and platform compatibility.

**Expected result**: Previews are generated without errors as well as the .png files using the examples provided with the software within the VS Code IDE environment running on a Linux x64 machine. No other files are generated.

**Test steps**:

* Use a Linux x64 machine with the PlantUML and all dependencies (ditta, dot, graphviz, etc.) installed as well as VS Code (with the PlantUML plugin)
* Create a new project in the VS Code
* Check-out the plant_uml library from the repository (Git) into this project
* Locate included folders with the examples (*class_example*, *component_example*, *database_example*)
* Open a .pu file within any of these folders and open it
* Generate a preview (usually, Alt+D in the case of the VS Code PlantUML plugin) - no error should be reported by the PlantUML render
* Generate a .png file - normally it should be placed into *out* folder inside the project / workspace, check the VS Code settings otherwise
* Open the generated .png file - it should look like the same as the preview
* Repeat the last 4 steps with other examples

**Test result**: PASS / FAIL (To be filled in the test report)

---

**Test identifier**: TEST-D-002

**Requirement ID(s)**: REQ-FUN-P001, REQ-SIO-F001, REQ-INT-R001, REQ-AWM-E001, REQ-USE-U001, REQ-IAR-I001

**Verification method**: D

**Test goal**: Software usability and platform compatibility.

**Expected result**: The .png files are generated without errors using the examples provided with the software when the plantuml.jar stand-alone tool is used on a Windows 8 / 10 x64 machine. No other files are generated.

**Test steps**:

* Copy the entire plant_uml library from one installation (e.g. used in TEST-D-001) into another x64 machine running Windows 8 or 10 OS, which also has the PlantUML and all dependencies (ditta, dot, graphviz, etc.) installed as well as Java
* Locate included folders with the examples (*class_example*, *component_example*, *database_example*)
* Delete all rendered (.png files) diagrams, while leaving all other files (.iuml, .pu., etc.) intact
* Run the plantuml.jar application over each of these folders
* For each .pu file a corresponding .png rendered diagram should be generated without errors

**Test result**: PASS / FAIL (To be filled in the test report)

---

**Test identifier**: TEST-D-003

**Requirement ID(s)**: REQ-AWM-E001, REQ-USE-U001

**Verification method**: D

**Test goal**: The software does not generate own error messages, but the PlantUML application itself generates errors in the case of the syntax errors or missing files.

**Expected result**: When a syntax error is present, or the file to be imported is not found, the preview is not generated, instead the PlantUML application reports an error.

**Test steps**:

* Use the machine with the installed PlantUML and its dependencies, VS Code (and the PlantUML plugin) and the plant_uml library in the active project / workspace of the VS Code
* Locate any of the complete example diagram source code (.pu file within the *class_example*, *component_example* or *database_example* sub-folders)
* Generate preview - it should be generated properly
* Comment the !include preprocessor directive - the preview should not be generated, PlantUML error should be displayed instead
* Remove the comment, but mis-spell the base filename or the relative path to the included file - the preview should not be generated, PlantUML error should be displayed instead
* Spell the include file path / base name correctly - the preview should be generated correctly
* Mis-spell (change) the name of any of the macroses defined; two outcomes must be observed
  * for the macroses defining the components (function, class, file, module, package, library and pc) and the database objects (table, view, query, etc., joins, intersections, unions and exceptions, objects relations) the mis-spelled macros name is a syntax error - the preview should not be generated, PlantUML error should be displayed
  * for the non-parameteric macroses (as class decorators) and parametric macroses for the attributes decorators (abstract method, static method / field, primary and foreign keys) the mis-spelled macros name is not a syntax error - the preview is generated, but the resulting image is wrong

**Test result**: PASS / FAIL (To be filled in the test report)

---

**Test identifier**: TEST-D-004

**Requirement ID(s)**: REQ-FUN-F002, REQ-FUN-F003, REQ-FUN-F008

**Verification method**: D

**Test goal**: Proper rendering of the class diagram with the custom stereotypes and attributes decorators

**Expected result**: The class diagram is rendered as usual, except for the custom letters inside and the color of the circles in the class definition header and the custom stereotype strings; the relational links between the classes are as usual. The re-defined abstract and static decorators emphasize only the name of the attribute, not the entire definition line. The decorated static fields are placed amongst the fields, the static and abstract methods - amongst the methods. The public, private, protected modifiers work as usual.

**Test steps**:

* Use the machine with the installed PlantUML and its dependencies, VS Code (and the PlantUML plugin) and the plant_uml library in the active project / workspace of the VS Code
* Locate the plant_uml library, create a new class diagram source file and include the Classes.cuml template file into it (preprocessor directive)
* Define a class with each of the defined custom stereotypes
* Add randomly usual fields and methods definitions into the bodies of these classes with the access modifiers
* Add randomly fields with the re-defined static modifier and methods with the re-defined static and abstract modifiers, use the access modifiers as well
* Add randomly relational links between the classes (extends, includes, etc.) in the arbitrary directions
* Generate and analyze the preview

**Test result**: PASS / FAIL (To be filled in the test report)

---

**Test identifier**: TEST-D-005

**Requirement ID(s)**: REQ-FUN-F004, REQ-FUN-F008

**Verification method**: D

**Test goal**: Proper rendering of the custom components of the UML components diagram.

**Expected result**: The custom components are rendered as should the base components they are build from with and without the enclosed other components but with the custom stereotype string. Function, class and file components have the appearance of a generic UML component; module component - of a frame component; package (custom) and library - of the base package component; and pc - of a node.

**Test steps**:

* Use the machine with the installed PlantUML and its dependencies, VS Code (and the PlantUML plugin) and the plant_uml library in the active project / workspace of the VS Code
* Locate the plant_uml library, create a new component diagram source file and include the Components.cuml template file into it (preprocessor directive)
* Add two components of the each type: function, class and file - one without and one with the alternative display name
* Add four components of the each type: module, package, library and pc - one of each pair combination - without and with the alternative display name vs with and without enclosed sub-components
* Render the preview and inspect the result

**Test result**: PASS / FAIL (To be filled in the test report)

---

**Test identifier**: TEST-D-006

**Requirement ID(s)**: REQ-FUN-F005, REQ-FUN-F006, REQ-FUN-F007, REQ-FUN-F008, REQ-FUN-F009

**Verification method**: D

**Test goal**: Proper rendering of a database data model representation based on the custom class diagram.

**Expected result**: All database objects (tables, views, queries, including joins, unions, etc.) are displayed as classes with the custom decorators (letter within and the colour of the circles, stereorype strings) and are clearly distinguishable from each other and standard classes. Table / view fields are displayed in the fields section of the base class component they are based upon. Primary and foreign key fields are rendered as expected: with the graphical icons, emphasis on their names, and SQL data / constrains definitions. '1 to 1' and '1 to many' relational links are rendered between the proper tables; in the case of one to many relation the '1' is placed next to the table, which is referenced, and '*' - which references. Tables and views have the same display names as the actual names of the components. Joins, unions, intersections and exceptions have no dispay names but the 'consists of' links to their left and right parts with the clear indication 'L' and 'R' of the parts. Joins (except for the cross-joins) also show the SQL 'ON' clause with the linking fields. The generic queries do not have display names, unless they are explicitely forced as the second argument of the macros function.

**Test steps**:

* Use the machine with the installed PlantUML and its dependencies, VS Code (and the PlantUML plugin) and the plant_uml library in the active project / workspace of the VS Code
* Locate the plant_uml library, create a new class diagram source file and include the Tables.cuml template file into it (preprocessor directive)
* Create several instances of the table and view macroses
* Add some fields into the definitions of these instances, including those created with help of the primary and foreign key macroses
* Create '1 to 1' and '1 to many' relational links between the tables
* Create a query instance without the display name, and another query with the display name
* Create a join between two tables, then a chained join between the first one and the third table / view
* Render the preview and inspect the result
* Repeat the previous two steps with all defined types of joins, unions, intersections and exceptions

**Test result**: PASS / FAIL (To be filled in the test report)

---

## Test definitions (Inspection)

None.

## Test definitions (Analysis)

**Test identifier**: TEST-A-001

**Requirement ID(s)**: REQ-FUN-L001, REQ-FUN-F001, REQ-SIO-F002, REQ-UDR-D002

**Verification method**: A

**Test goal**: Overall design (architechture) test - modularity, use of the PlantUML language, logical grouping of the functionality by modules, completeness of the implementation.

**Expected result**: The software is modular, the implemented functionality is grouped by the intended uses into the modules with '.cuml' extention, which can be openned with any text editor, and which contain PlantUML code and the inline documentation (comments, doc-strings, etc.). The implemented macroses cover all expected functionality, see REQ-FUN-F001.

**Test steps**:

* Inspect the content of the library. The files with the '.cuml' extension must be present.
* Inspect each '.cuml' file
  * It can be openned with any text editor (e.g. Notepad, GEdit, etc., or IDE, e.g. VS Code)
  * It contains PlantUML code defining the macroses
  * It contains the macroses designed for the generation of only specific type of the UML diagram: components, class or class diagram based database data model representation
  * It contains macroses for all required functionality
  * It contains the inline documentation for each defined macros, which provide clear reference on the syntax and intended use of the macros

**Test result**: PASS / FAIL (To be filled in the test report)

---

**Test identifier**: TEST-A-002

**Requirement ID(s)**: REQ-UDR-D001

**Verification method**: A

**Test goal**: The software has a user manual, which provides sufficient information on the installation and usage of the software, including the references on the syntax of the implemented extentions.

**Expected result**: The user manual is provided, and it contains all the required information.

**Test steps**: Locate the user manual. Read it. Compare the provided content with the source code and the inline documentation within.

**Test result**: PASS / FAIL (To be filled in the test report)

## Traceability

For traceability the relation between the tests and requirements is summarized in the table below:

| Requirement ID | Covered in test                    | Verified [YES/NO] |
| -------------- | ---------------------------------- | ----------------- |
| REQ-FUN-L001   | TEST-A-001                         | NO                |
| REQ-FUN-P001   | TEST-D-001, TEST-D-002             | NO                |
| REQ-FUN-F001   | TEST-A-001                         | NO                |
| REQ-FUN-F002   | TEST-D-004                         | NO                |
| REQ-FUN-F003   | TEST-D-004                         | NO                |
| REQ-FUN-F004   | TEST-D-005                         | NO                |
| REQ-FUN-F005   | TEST-D-006                         | NO                |
| REQ-FUN-F006   | TEST-D-006                         | NO                |
| REQ-FUN-F007   | TEST-D-006                         | NO                |
| REQ-FUN-F008   | TEST-D-004, TEST-D-005, TEST-D-006 | NO                |
| REQ-FUN-F009   | TEST-D-006                         | NO                |
| REQ-SIO-F001   | TEST-D-001, TEST-D-002             | NO                |
| REQ-SIO-F002   | TEST-A-001                         | NO                |
| REQ-INT-R001   | TEST-D-001, TEST-D-002             | NO                |
| REQ-AWM-E001   | TEST-D-001, TEST-D-002, TEST-D-003 | NO                |
| REQ-USE-U001   | TEST-D-001, TEST-D-002, TEST-D-003 | NO                |
| REQ-IAR-I001   | TEST-D-001, TEST-D-002             | NO                |
| REQ-UDR-D001   | TEST-A-002                         | NO                |
| REQ-UDR-D002   | TEST-A-001                         | NO                |

| Software ready for production [YES/NO] | Rationale |
| -------------------------------------- | --------- |
| NO                                     |           |
