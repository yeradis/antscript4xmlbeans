# antscript4xmlbeans

### Ant script for "automatic" XMLBeans JavaBeans-style generation using custom namespaces

This script will loop a folder content and will compile every XMLSchema(XSD) to Java, using a JavaBeans-style.

Every XMLSchema (XSD) need a XSDCONFIG file indicating to XMLBeans the namespace where this XSD will have its Java class definitions. 


    <xb:config xmlns:pol="http://www.whateveryouneed.com" xmlns:xb="http://www.bea.com/2002/09/xbean/config">
        <xb:namespace uri="##any">
            <xb:package>com.whateveryouneed.package.path.whatever</xb:package>
        </xb:namespace>
    </xb:config>


In this way, using a XSDCONFIG file, you will be able to put every schema on its own packages, avoiding problems with those XSD that define same nodes(objects) with diferent body, XSDs that cause XMLBeans to fail when compiling.

In other words, using a XSDCONFIG file i'm able to guide the naming of generated classes and packages. Without XSDCONFIG file,XMLBeans *scomp* will use the schema's type names and URI available on XMLSchemas for classes and packages.

This ANT script is using:

-ANT-CONTRIB
-a folder for output called WORKING , this get erased before ever build
-a folder for XML Schemas (XSD) called SCHEMAS, folder wich contains .xsd files and .xsdconfig files, .xsconfig files must have same name as the xsd will represent.
-finnally will generate a .jar for every .xsd file.