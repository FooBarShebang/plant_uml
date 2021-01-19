# PlantUML Templates

A set of templates (as macro / preprocessor directives, i.e. functions, procedures and variables) for the commonly used (in my personal experience - Anton Azarov) tasks in creating UML diagrams using PlantUML mark-up language.

Version: 1.0.0.0

## Legacy and modern PlantUML processor syntax support

The syntax of the preprocessor directives has been greatly enhanced and changed. In order to address these changes without breaking the old syntax based work in other projects using this one the changes are implemented as separate templates files.

Basically, the same functionality using the current syntax is implemented in the template '.cuml' files with the same names as the legacy syntax but with '2' suffix in the name.

## Structure

* [Classes2.cuml](./Classes2.cuml)
* [Components2.cuml](./Components2.cuml)
* [General2.cuml](./General.cuml)
* [Tables2.cuml](./Tables.cuml)

### Legacy preprocessor implementation

* [Classes.cuml](./Classes.cuml)
* [Components.cuml](./Components.cuml)
* [General.cuml](./General.cuml)
* [Tables.cuml](./Tables.cuml)

## Examples

### Class Diagram

* [Source](./class_example/class_example.pu)
* [Rendered](./class_example/class_example.png)

### Database Description Using Class Diagram

* [Source](./database_example/standards_constructions_view.pu)
* [Rendered](./database_example/standards_constructions_view.png)
* [Source](./database_example/standards_materials_view.pu)
* [Rendered](./database_example/standards_materials_view.png)
* [Source](./database_example/standards_schema.pu)
* [Rendered](./database_example/standards_schema.png)

### Components Diagram

* [Source](./components_example/components_example.pu)
* [Rendered](./components_example/components_example.png)

## Documentation

* [User Manual](./Documentation/user_manual.md)
* Technical documentation
  * [Requirements document](./Documentation/requirements.md)
  * [Design](./Documentation/design.md)
  * [Test report](./Documentation/test_report.md)
