# PlantUML_Templates
A set of templates (as macro / preprocessor directives) for the commonly used
(in my personal experience - Anton Azarov) tasks in creating UML diagrams using
PlantUML mark-up language.

Contact: anton.v.azarov@gmail.com

NOTE: the entire approach is based upon "!include" preprocessor directive, which
may not work correctly depending on the local Java installation / RTE
environmental variables and used PlantUML implementation.
For instance, on my local machine (Anton Azarov) the PlantUML plug-in for
Eclipse (Oxygen.2 (4.7)) generates the diagrams correctly inside the Eclipse,
but it fails to export them into PNG files under both Win7-64 and Linux Mint
18-64, being unable to resolve the import paths. The stand-alone PlantUML JAR
has no such problems.
