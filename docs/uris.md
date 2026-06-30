# URIS in RDFS / OWL 

## RDFS

* Entity URIs follow this structure:
    * **Base URI** + **entity identifier**
    * Example: `http://www.cidoc-crm.org/cidoc-crm/E1`
    * Base URI is defined by root (or by version if exists)

## RDFS with Inverse Properties
* Entity URIs follow this structure:
    * **Base URI** + **specific identifier**
* To find the specific identifier, go to the **Identification** tab of the entity and read the "Official URI".

## OWL-DL
* todo

## OWL-Wisski
* todo

## How to configure specific identifier for a namespace ?

* This specific identifier can be configured in the **Root namespace**, under the **Identifiers** tab (only for external namespaces).

* There are four possible options:

  * **Entity identifier**
    `http://www.cidoc-crm.org/cidoc-crm/E1`

  * **Entity identifier + label**
    `http://www.cidoc-crm.org/cidoc-crm/E1_CRM_Entity`

  * **CamelCase**
    `http://iflastandards.info/ns/fr/frbr/frbroo/classLabel`

  * **No parameter**
    You define the identifier manually when creating the entity (it may be prefilled if needed).
