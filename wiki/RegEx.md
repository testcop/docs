TestCop uses a configurable RegEx to identify which projects within the solution are test projects by applying the RegEx against the 'default namespace' of the project. TestCop does not use the name of the project.

You must name your code and test projects so that it is possible to derive the namespace of the code project from its associated test project namespace e.g. MyCorp.MyApp.DataAccess.Tests => MyCorp.MyApp.DataAccess. Use must **RegEx groupings** (brackets) to extract the code namespace project from the test projects namespace. A blank regex grouping implies all groupings are used, if you want to use only the first grouping then use $1

Define the RegEx according to your namespace standards.

## Example RegExs :
{"
^(.*)\.Tests$ 
for MyCorp.MyApp.DataAccess.Tests 

^(.*)Tests$ 
for MyCorp.MyApp.DataAccessTests 

^(.**)\.Tests(\..**)$ 
for   MyCorp.MyApp.Tests.DataAccess   
"}