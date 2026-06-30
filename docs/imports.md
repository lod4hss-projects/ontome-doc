# How to Import XML Namespaces in OntoME

_This page explains how to import namespaces into OntoME from an XML file_

**/!\ This feature is currently available to a limited number of users**

# 1. Prerequisites & Access rights
- Before importing a namespace from an XML file in OntoME, make sure the project already has a root namespace created.
- Only users with **project administrator** privileges can perform namespace imports, ensuring proper management and integration of ontology elements within the project.
- When a namespace is imported through an XML file, it is automatically considered **published** in OntoME and cannot be modified afterward.
- The import form is available in a dedicated tab on the project page, accessible when the project is in **Edit mode**.


# 2. Basic XML structure
This section shows the XML structure required for a simple namespace import, without any dependencies on other namespaces.
```xml
<namespace>
    <standardLabel lang=""></standardLabel>
    <version></version>
    <publishedAt></publishedAt>
    <contributors></contributors>
    <description lang=""></description>
    <classes>
        <class>
            <identifierInNamespace></identifierInNamespace>
            <identifierInURI></identifierInURI>
            <standardLabel lang=""></standardLabel>
            <subClassOf></subClassOf>
            <parentClassOf></parentClassOf>
            <equivalentClass></equivalentClass>
            <disjointWith></disjointWith>
            <textProperties>
                <scopeNote lang=""></scopeNote>
                <example lang=""></example>
            </textProperties>
        </class>
    </classes>
    <properties>
        <property>
            <identifierInNamespace></identifierInNamespace>
            <identifierInURI></identifierInURI>
            <label lang="">
                <standardLabel></standardLabel>
                <inverseLabel></inverseLabel>
            </label>
            <subPropertyOf></subPropertyOf>
            <parentPropertyOf></parentPropertyOf>
            <equivalentProperty></equivalentProperty>
            <inverseOf></inverseOf>
            <hasDomain></hasDomain>
            <hasRange></hasRange>
            <domainInstancesMinQuantifier></domainInstancesMinQuantifier>
            <domainInstancesMaxQuantifier></domainInstancesMaxQuantifier>
            <rangeInstancesMinQuantifier></rangeInstancesMinQuantifier>
            <rangeInstancesMaxQuantifier></rangeInstancesMaxQuantifier>
            <textProperties>
                <scopeNote lang=""></scopeNote>
                <example lang=""></example>
                <contextNote lang=""></contextNote>
                <bibliographicalNote lang=""></bibliographicalNote>
            </textProperties>
        </property>
    </properties>
</namespace>
```
## Explanation of XML Tags
- `<namespace>` – Required and unique.  
    - `<standardLabel lang="">` – Required and can be repeated once per language (_en_, _fr_, _de_...). Example: `CIDOC CRM v7.1.1`.  
    - `<version>` – Optional, but unique. Example: `7.1.1`.  
    - `<publishedAt>` – Optional, indicate a dateTime. Example: [DateTime format reference](http://books.xmlschemata.org/relaxng/ch19-77049.html).  
    - `<contributors>` – Optional, but unique. Example: `John Doe, Alice Carter and Bob Dave`.  
    - `<description lang="">` – Optional, can be repeated once per language.  
    - `<classes>` – Optional, if present must be unique.  
        - `<class>` – Required if `<classes>` is defined; can be repeated, one by class.  
            - `<identifierInNamespace>` – Required, e.g., `E5`.  
            - `<identifierInURI>` – Optional, e.g., `E7_Activity`.  
            - `<standardLabel lang="">` – Required, can be repeated. The first English label is used as default for display. Example: `Event`.  
            - `<subClassOf>` – Optional, can be repeated. Example: `E2`.  
            - `<parentClassOf>` – Optional, can be repeated. Example: `E2`.  
            - `<equivalentClass>` – Optional, can be repeated. Example: `E2`.  
            - `<disjointWith>` – Optional, can be repeated. Example: `E2`.  
            - `<textProperties>` – Required and unique.  
                - `<scopeNote lang="">` – Optional (recommended), can be repeated once per language. Example: `This class comprises...`.  
                - `<example lang="">` – Optional, can be repeated. Example: `The birth of Cleopatra`.  
                - `<contextNote lang="">` – Optional, can be repeated.  
                - `<bibliographicalNote lang="">` – Optional, can be repeated.  
    - `<properties>` – Optional, if present must be unique.  
        - `<property>` – Required if `<properties>` is defined; can be repeated.  
            - `<identifierInNamespace>` – Required, e.g., `P5`.  
            - `<identifierInURI>` – Optional, e.g., `PE1_Service`.  
            - `<label>` – Required and can be repeated once per language. The first English label is default for display.  
                - `<standardLabel>` – Required, unique; must match the language of `<label>`. Example: `consists of`.  
                - `<inverseLabel>` – Optional, unique. Example: `forms part of`.  
            - `<subPropertyOf>` – Optional, can be repeated. Example: `P2`.  
            - `<parentPropertyOf>` – Optional, can be repeated. Example: `P2`.  
            - `<equivalentProperty>` – Optional, can be repeated. Example: `P2`.  
            - `<inverseOf>` – Optional, can be repeated. Example: `P2`.  
            - `<hasDomain>` – Required and unique. Specify the identifier (e.g., `C1`).  
            - `<hasRange>` – Required and unique. Specify the identifier (e.g., `C1`).  
            - `<domainInstancesMinQuantifier>` – Specify `0` or `1`.  
            - `<domainInstancesMaxQuantifier>` – Specify `1`, `2`, `3`, `4`, `5`, or `n`.  
            - `<rangeInstancesMinQuantifier>` – Specify `0` or `1`.  
            - `<rangeInstancesMaxQuantifier>` – Specify `1`, `2`, `3`, `4`, `5`, or `n`.  
            - `<textProperties>` – Optional, unique.  
                - `<scopeNote lang="">` – Optional (recommended), can be repeated once per language. Example: `This property describes...`.  
                - `<example lang="">` – Optional, can be repeated. Example: `The period "Révolution française" (E4)...`.  
                - `<contextNote lang="">` – Optional, can be repeated.  
                - `<bibliographicalNote lang="">` – Optional, can be repeated.  

# 3. Advanced XML Structure
This section describes how to import namespaces in OntoME using **reference namespaces** that are already present in the system. This allows you to create new namespaces that build upon or extend existing ones, reusing classes and properties from other namespaces to maintain consistency and avoid duplication.
```xml
<namespace>
    <standardLabel lang=""></standardLabel>
    <version></version>
    <publishedAt></publishedAt>
    <contributors></contributors>
    <referenceNamespace></referenceNamespace>
    <description lang=""> 
    <classes>
        <class>
            <identifierInNamespace></identifierInNamespace>
            <identifierInURI></identifierInURI>
            <standardLabel lang=""></standardLabel>
            <subClassOf></subClassOf>
            <subClassOf referenceNamespace=""></subClassOf>
            <parentClassOf></parentClassOf>
            <parentClassOf referenceNamespace=""></parentClassOf>
            <equivalentClass></equivalentClass>
            <equivalentClass referenceNamespace=""></equivalentClass>
            <disjointWith></disjointWith>
            <disjointWith referenceNamespace=""></disjointWith>
            <textProperties>
                <scopeNote lang=""></scopeNote>
                <example lang=""></example>
                <contextNote lang=""></contextNote>
                <bibliographicalNote lang=""></bibliographicalNote>
            </textProperties>
        </class>
    </classes>
    <properties>
        <property>
            <identifierInNamespace></identifierInNamespace>
            <identifierInURI></identifierInURI>
            <label lang="">
                <standardLabel></standardLabel>
                <inverseLabel></inverseLabel>
            </label>
            <subPropertyOf></subPropertyOf>
            <subPropertyOf referenceNamespace=""></subPropertyOf>
            <parentPropertyOf></parentPropertyOf>
            <parentPropertyOf referenceNamespace=""></parentPropertyOf>
            <equivalentProperty></equivalentProperty>
            <equivalentProperty referenceNamespace=""></equivalentProperty>
            <inverseOf></inverseOf>
            <inverseOf referenceNamespace=""></inverseOf>
            <hasDomain></hasDomain>
            <hasDomain referenceNamespace=""></hasDomain>
            <hasRange></hasRange>
            <hasRange referenceNamespace=""></hasRange>
            <domainInstancesMinQuantifier></domainInstancesMinQuantifier>
            <domainInstancesMaxQuantifier></domainInstancesMaxQuantifier>
            <rangeInstancesMinQuantifier></rangeInstancesMinQuantifier>
            <rangeInstancesMaxQuantifier></rangeInstancesMaxQuantifier>
            <textProperties>
                <scopeNote lang=""></scopeNote>
                <example lang=""></example>
                <contextNote lang=""></contextNote>
                <bibliographicalNote lang=""></bibliographicalNote>
            </textProperties>
        </property>
    </properties>
</namespace>
```
## Explanation of XML Tags (Advanced XML Structure)
All tags described in the **Basic XML Structure** are still valid in the advanced XML import.  
The following explanation adds extra tags and behaviors specific to advanced imports using reference namespaces:
- `<referenceNamespace>` – Optional, can be repeated. Indicates the OntoME ID of an existing reference namespace.  

**Behavior:**  
When `referenceNamespace="ID_ontome_namespace"` is specified to the following tags, the entity (class or property) will be taken from the referenced namespace. If not specified, the entity will belong to the namespace being imported:

  * `<subClassOf>`  
  * `<parentClassOf>`  
  * `<equivalentClass>`  
  * `<disjointWith>`  
  * `<subPropertyOf>`  
  * `<parentPropertyOf>`  
  * `<equivalentProperty>`  
  * `<inverseOf>`  
  * `<hasDomain>`  
  * `<hasRange>` 

**Usage:** Specify the OntoME ID of the reference namespace in `<referenceNamespace>` to reuse classes or properties from an existing namespace.
**Tip:** The ID of a namespace can be found easily by checking the URL of the corresponding namespace in OntoME.

# 4. XML Schema Definition (XSD)

The XSD is used to validate the structure of the XML file before importing it into OntoME. It ensures that all required elements and attributes are correctly defined, helping to prevent errors during the import process.

You can use this XSD with your preferred XML editor or validation tool to check your XML file before importing it into OntoME.

The schema file can be downloaded [here](https://ontome.net/documents/schemaImportXmlwithReferences.xml).
