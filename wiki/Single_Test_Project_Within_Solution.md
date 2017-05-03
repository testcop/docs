## Single test project in a solution

A single test project for all code projects within an assembly is supported but configuration is a little more complex. 
**Contact me if you have ideas on how to make this simpler!**

RegEx patterns need to be supplied to 
* Identify the test project and then to map the test namespace to the associated code assembly and to provide the namespace within it. E.g. **MyCorp.MyApp**.Tests.**Infrastructure**.NS1 --> to the namespace NS1 within the code project **MyCorp.MyApp.Infrastructure**. The RegEx needs to perform both these operations...find test projects and extract the sub namespace.
* Extract the namespace from the namespace of the code file that will be the subnamespace for the test E.g. MyCorp.MyApp.**Infrastructure.NS1** --> to the namespace **Infrastructure.NS1** which will be under the single test project of the solution

The default Regex is for projects where the name space is prefixed with two strings e.g. MyCorp.MyApp. In the following two examples the $2 substitution enables testcop to identify the part which will become the subnamespace within the test project. 
* RegEx for MyCorp.MyApp.Infrastructure.NS1 is {" ^(.**\..**?)(\..**?)$ "}
* Regex for MyApp.Infrastructure.NS1 is {" ^(.**?)(\..**?)$ "}

1. Test classes must end in the name **Tests** (configurable)
2. Tests are held in a single assembly **separate** to the code assembly under test. The sub-namespace within the test assembly should correspond to the code assembly under test 
3. Assemblies containing tests must have a namespace (not necessariliy file name) that matches a testcop configurable RegEx. Typically your test namespace would end in **.Tests** (configurable)
4. The file name containing the unit tests must contain the test class name inline with the following rules 
- The file named **MyClass**Tests.cs would contain the class **MyClass**Tests testing **MyClass** 
- The file named **MyClass**.SomeCategoryTests.cs would contain the class MyClassSomeCategoryTests testing MyClass (this enables you to split up your unit tests into categories e.g. MyClass.SecurityTests.cs
5. The first part of the test filename (see point 4) must relate to a class within the associated code assembly. This helps ensure renames of code are reflected within the test classes. The only exceptions are BDD style class names which begin typically with Given or When (configurable).