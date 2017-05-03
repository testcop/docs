## Multiple test projects identified by namespace 

1. Test classes must end in the name **Tests** (configurable)
2. Tests are held in assemblies **separate** to the assembly under test. Each test assembly should correspond to one assembly under test though each code assembly can map to more than one test assembly. e.g. MyOrg.MyProj  --> MyOrg.MyProj.Tests & MyOrg.MyProj.IntegrationTests
3. Assemblies containing tests must have a namespace (not necessariliy file name) that matches a testcop configurable [RegEx](RegEx.md). Typically your test namespace would end in **.Tests** (configurable)
4. The file name containing the unit tests must contain the test class name inline with the following rules 
- The file named **MyClass**Tests.cs would contain the class **MyClass**Tests testing **MyClass** 
- The file named **MyClass**.SomeCategoryTests.cs would contain the class **MyClass**SomeCategoryTests testing **MyClass**  (+this enables you to split up your unit tests+ into categories e.g. MyClass.SecurityTests.cs
5. The first part of the test filename (see point 4) must relate to a class within the associated code assembly. This helps ensure renames of code are reflected within the test classes. The only exceptions are BDD style class names which begin typically with **Given** or **When** (configurable).