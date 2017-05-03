## Multiple test projects identified by project name

Where each test project maps to one code project via the project name. The namespace of the test project and associated code project are the same. 

1. Test classes must end in the name **Tests** (configurable)
2. Tests are held in assemblies **separate** to the assembly under test. Each test assembly should correspond to one assembly under test though each code assembly can map to more than one test assembly. e.g. MyProj  --> MyProjTests & MyProjIntegrationTests
3. Assemblies containing tests must have a project name that matches a testcop configurable [RegEx](RegEx.md) and there must be a corresponding code project with a matching name (from the regex). Both the test and code projects must have the same namespace.
4. The file name containing the unit tests must contain the test class name inline with the following rules 
- The file named **MyClass**Tests.cs would contain the class **MyClass**Tests testing **MyClass** 
- The file named **MyClass**.SomeCategoryTests.cs would contain the class **MyClass**SomeCategoryTests testing **MyClass**  (+this enables you to split up your unit tests+ into categories e.g. MyClass.SecurityTests.cs
5. The first part of the test filename (see point 4) must relate to a class within the associated code assembly. This helps ensure renames of code are reflected within the test classes. The only exceptions are BDD style class names which begin typically with **Given** or **When** (configurable).