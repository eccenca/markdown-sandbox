---
status: new
icon: octicons/cross-reference-24
tags:
    - Reference
    - Vocabulary
---
# Property Shapes
<!-- This file was generated - DO NOT CHANGE IT MANUALLY -->

Property Shapes are resources of type `shacl:PropertyShape`.
They are used to specify constraints and UI options that need to be met in the context of a Node Shape.

The following Property Shape properties are supported:


## Naming and Presentation

!!! info

    In this group, presentation and naming properties are collected. Most of the properties are straight forward to use, other properties provide more complex features, such as table reports.

### Name


This name will be shown to the user.

Used Path: `shacl:name`


### Description


This text will be shown to the user in a tooltip. You can use new and blank lines for basic text structuring.

Used Path: `shacl:description`


### Query: Table Report


Use this property to provide a tabular report of a custom SPARQL query at the place where this property shape is used in the user interface.

The following placeholder can be used in the query text of the SPARQL query:

- `{{shuiGraph}}` - the currently used graph
- `{{shuiResource}}` - refers to the resource which is rendered in the node shape where this property shape is used (maybe a sub-shape)
- `{{shuiAccount}}` - the account IRI of the active user, this includes the username (use a SUBSTR() function if you need the name only)
- `{{shuiAccountName}}` - the user name/ID of the active user account
- `{{shuiMainResource}}` - refers to the main resource rendered in the start node shape of the currently displayed node shape tree (only relevant in case of sub-shape usage)

Beta Feature: This query will be used as well to populate the related resources for the advanced editor. In this case, you need to have the projection variables `resource` (the resource IRI which is linked to the shaped resource) and `graph` or _graph (the graph IRI where the relation statement is saved) in your query.

If your table report is not intended to be used with the advanced editor, you can set the property as read only.


Used Path: `shui:valueQuery`


### Query: Table Report (hide header)


If set to true, the report table will be rendered without header (in case you expect only a single value).

Used Path: `shui:valueQueryHideHeader`


### Query: Table Report (hide footer)


If set to true, the report table will be rendered without footer (in case you expect only a single value or row).

Used Path: `shui:valueQueryHideFooter`


### Order


Specifies the order of the property in the UI. Ordering is separate for each group.

Used Path: `shacl:order`


### Group


Group to which the property belongs to.

Used Path: `shacl:group`


### Show always


Default is false. A value of true let optional properties (min count = 0) show up by default.

Used Path: `shui:showAlways`


### Read only


Default is false. A value of true means the properties are not editable by the user. Useful for displaying system properties.

Used Path: `shui:readOnly`


### Chart Visualization (deprecated)


Integrates a chart visualization in the property shape area. Shapes with an integrated chart are ALWAYS shown in read mode and NEVER shown in edit mode. This Property is deprecated - please use a Widget Integration instead.

Used Path: `shui:provideChartVisualization`


### Provide Workflow Trigger (deprecated)


Integrates a workflow trigger button in order to execute workflows from or with this resource. Shapes with an integrated workflow trigger are ALWAYS shown in read mode and NEVER shown in edit mode.

This property is deprecated - use a Widget Integration instead.


Used Path: `shui:provideWorkflowTrigger`

## Vocabulary

!!! info

    In this group, property paths as well cardinality restrictions are managed.

### Property of


The node shape this property shape belongs to.

Used Path: `shacl:property`


### Path


The datatype or object property used in this shape. This path will be ignored if there is a table report defined for the property shape. However, in Easynav, this path can always be used for exploration.

Used Path: `shacl:path`


### Node kind


The type of the linked nodes. In BKE, if these nodes are literals, they cannot be explored, but will be shown as metadata.

Used Path: `shacl:nodeKind`


### Min count


Min cardinality, 0 will show this property under optionals unless 'Show always = true'

Used Path: `shacl:minCount`


### Max count


Max cardinality

Used Path: `shacl:maxCount`

## Datatype Property Specific

!!! info

    In this group, all shape properties are managed, which only have effects on datatype properties.

### Datatype


The datatype of the property.

Used Path: `shacl:datatype`


### Use textarea


Default is false. A value of true enables multiline editing capabilities for Literals via a `textarea` widget.

Used Path: `shui:textarea`


### Regex Pattern


A XPath regular expression (Perl like) that all literal strings need to match.

Used Path: `shacl:pattern`


### Regex Flags


An optional string of flags for the regular expression pattern (e.g. 'i' for case-insensitive mode)

Used Path: `shacl:flags`


### Languages allowed


This limits the given Literals to a list of languages. This property works only in combination with the datatype `rdf:langString`. Note that the expression for this property only allows for '2 Char ISO-639-1-Codes' only (no sub-tags).

Used Path: `shui:languageIn`


### Languages Unique


Default is false. A value of true enforces that no pair of Literals may use the same language tag.

Used Path: `shacl:uniqueLang`

## Object Property Specific

!!! info

    In this group, all shape properties are managed, which only have effects on object properties.

### Class


Class of the connected IRI if its nodeKind is sh:IRI. In Easynav, any new node that a user creates by means of this property shape, will be an instance this class.

Used Path: `shacl:class`


### Used Class for Resource Creation


Use this property to overrule which class is used when a user creates a new resource inside of this property shape on-the-fly.

Used Path: `shui:usedClassForResourceCreation`


### Query: Selectable Resources


This query allows for listing selectable resources in the dropdown list for this property shape.

You need to provide the projection variable `resource` in your query.

The following placeholder can be used in the query text of the SPARQL query:

- `{{shuiGraph}}` - the currently used graph
- `{{shuiResource}}` - refers to the resource which is rendered in the node shape where this property shape is used (maybe a sub-shape)
- `{{shuiAccount}}` - the account IRI of the active user, this includes the username (use a SUBSTR() function if you need the name only)
- `{{shuiAccountName}}` - the user name/ID of the active user account
- `{{shuiMainResource}}` - refers to the main resource rendered in the start node shape of the currently displayed node shape tree (only relevant in case of sub-shape usage)

Beta Feature: This query will be used as well to populate the selectable resources for the advanced editor and the candidate resources in EasyNav.

Used Path: `shui:uiQuery`


### Inverse Path


Default is false. A value of true inverts the expected / created direction of a relation.

Used Path: `shui:inversePath`


### Deny new resources


A value of true disables the option to create new resources.

Used Path: `shui:denyNewResources`


### Resource viewer widget


Selects default object relation resource viewer widget. (NOTE: shacl2 only)

Used Path: `shui:viewResourcesWithWidget`


### Node shape


This shape will be used to create an embedded view of the linked resource.

Used Path: `shacl:node`

## Processing

!!! info

    In this group, all shape properties are managed, have an effect on how new or existing resources are processed or created.

### Severity


Categorize validation results (:Info, :Warning, :Violation). Defaults to :Violation.

Used Path: `shacl:severity`


### Message


If there is a message value, then all validation results produced as a result of this shape will have exactly this message.

Used Path: `shacl:message`


### Ignore on copy


Disables reusing the value(s) when creating a copy of the resource.

Used Path: `shui:ignoreOnCopy`


### Query: On insert update


This query is executed when a property value is added or changed.

The following placeholder can be used in the query text of the SPARQL query:

- `{{shuiGraph}}` - the currently used graph
- `{{shuiResource}}` - refers to the resource which is rendered in the node shape where this property shape is used (maybe a sub-shape)
- `{{shuiAccount}}` - the account IRI of the active user, this includes the username (use a SUBSTR() function if you need the name only)
- `{{shuiAccountName}}` - the user name/ID of the active user account
- `{{shuiMainResource}}` - refers to the main resource rendered in the start node shape of the currently displayed node shape tree (only relevant in case of sub-shape usage)
- `{{shuiObject}}` - the object value of the statement matched by the property shape
- `{{shuiProperty}}` - the IRI of the property of the statement matched by the property shape


Used Path: `shui:onInsertUpdate`


### Query: On delete update


A query which is executed when the statement the property shape applies to gets deleted.

The following placeholder can be used in the query text of the SPARQL query:

- `{{shuiGraph}}` - the currently used graph
- `{{shuiResource}}` - refers to the resource which is rendered in the node shape where this property shape is used (maybe a sub-shape)
- `{{shuiAccount}}` - the account IRI of the active user, this includes the username (use a SUBSTR() function if you need the name only)
- `{{shuiAccountName}}` - the user name/ID of the active user account
- `{{shuiMainResource}}` - refers to the main resource rendered in the start node shape of the currently displayed node shape tree (only relevant in case of sub-shape usage)
- `{{shuiObject}}` - the object value of the statement matched by the property shape
- `{{shuiProperty}}` - the IRI of the property of the statement matched by the property shape


Used Path: `shui:onDeleteUpdate`


### Target Graph Template


Graph templates can be used to enforce writing statement in specific graphs rather than into the selected graph. Graph templates can be added to node and property shapes. A template on a property shape is used only for overwriting a template on a node shape (without a node shape graph template, they do not have an effect).

Used Path: `shui:targetGraphTemplate`

## Statement Annotation

!!! info

    Statement Annotations provide a way to express knowledge about statements. This group is dedicated to properties which configure the Statement Annotation feature.

### Enable


A value of true enables visualisation and management capabilities of statement annotations (reification) for all statements which are shown via this shape.

Used Path: `shui:enableStatementLevelMetadata`


### Provided Shapes


Instead of providing all possible statement annotation node shapes for the creation of new statement annotations, this property will limit the list to the selected shapes only.

Used Path: `shui:provideStatementLevelMetadataShapes`
