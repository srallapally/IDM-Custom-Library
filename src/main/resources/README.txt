Build the custom lib via maven (mvn clean install) and drop it into <openidm/bundle.
Start openidm.
The maven project is set up to build a bundle fragment that makes the contents available to script.

To test the code, login to openidm admin console --> Configure Managed Objects -> Role --> Scripts
Add the following snippet to onCreate as an inline script
var mypkg = JavaImporter(Packages.com.example);
with(mypkg){
  var w = new com.example.WriteCSV();
  var b = w.writeCSV("Hello");
}

Save.
Navigate to Manage --> Roles --> Create
If all goes to plan, you will see a xls created in your OPENIDM_HOME