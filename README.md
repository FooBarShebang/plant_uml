# PlantUML Templates

A set of templates (as macro / preprocessor directives) for the commonly used (in my personal experience - Anton Azarov) tasks in creating UML diagrams using PlantUML mark-up language.

NOTE: the entire approach is based upon "!include" preprocessor directive, which may not work correctly depending on the local Java installation / RTE environmental variables. In the conducted, though limited, testing no issues are found with the stand-alone application (plantuml.jar) nor with VS Code (using PlantUML plug-in by jebbs, v2.10.3). With the Eclipse IDE (Neon and later, e.g. 2018-12) the preview is generated properly, but the rendering into files is broken (both on Linux and Windows 8 / 10 OSes).

## Note on the future changes

The syntax of the preprocessor directives has been greatly enhanced and changed. In order to address these changes without breaking the old syntax based work in other projects using this one the changes will be implemented as separate templates files.

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
* Technical documentation
  * [Requirements document](./Documentation/requirements.md)
  * [Design](./Documentation/design.md)
  * [Test report](./Documentation/test_report.md)
