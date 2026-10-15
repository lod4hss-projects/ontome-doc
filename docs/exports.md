# Understanding RDFS and OWL Exports

OntoME allows users to export ontologies in different formats, depending on their needs and the tools they want to use.

### 1. How are URIs generated?

A URI is a unique address used to identify a class or property in an ontology.

OntoME supports two ways of generating these addresses:
- **Standard URI**: uses the element's usual identifier (e.g. `E1`).
- **Specific URI**: uses a customised identifier, which may include the element's name (e.g. `E1_CRM_Entity`).

The URI generation method is defined in the root namespace settings, under the *Identifiers* tab. Several options are available: using the identifier alone, combining it with the element's name, generating a camelCase name, or entering the identifier manually.

### 2. The different namespace exports

OntoME offers four types of exports:

- **RDFS**: a standard export without inverse properties, using standard URIs.
- **RDFS with inverse properties**: an export that includes inverse properties and uses specific URIs.
- **OWL-DL**: a complete OWL export using standard URIs.
- **OWL-WissKI**: an OWL export designed for use with WissKI. It includes references that allow WissKI to retrieve the ontologies it depends on.

### 3. Other exports

- **Profile exports**: functionality to be specified.
- **Container exports**: generate a list of URIs pointing to the OWL-WissKI exports of namespaces, making them easier to retrieve.

In short, the export format determines which information is included in the file, how elements are identified, and, in some cases, compatibility with specific tools.