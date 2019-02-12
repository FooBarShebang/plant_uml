# PlantUML Templates

A set of templates (as macro / preprocessor directives) for the commonly used
(in my personal experience - Anton Azarov) tasks in creating UML diagrams using
PlantUML mark-up language.

NOTE: the entire approach is based upon "!include" preprocessor directive, which
may not work correctly depending on the local Java installation / RTE
environmental variables.

## Structure

All templates are defined in the folder **Templates**

* [Classes.cuml](./Templates/Classes.cuml)
* [Components.cuml](./Templates/Components.cuml)
* [General.cuml](./Templates/General.cuml)
* [Tables.cuml](./Templates/Tables.cuml)

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