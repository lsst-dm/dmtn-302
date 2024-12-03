# IVOA Identifier Usage at the Rubin Observatory

```{abstract}
The IVOA define a standard URI scheme to reference individual datasets. In this document we will define how these IVOA Identifiers will be formed for Butler datasets and possibly object catalog IDs.
```

## Introduction

The IVOA Identifier (IVOID) standard {cite:p}`2016ivoa.spec.0523D` provides a mechanism for publishers to provide unique identifiers to individual datasets using an `ivo` URI scheme.
The IVOID consists of a registry part that must be registered in VO Registry, and a local part that defines the specific resource.
The registry part consists of a naming authority (effectively an internet location corresponding to the `netloc` field) and a resource key (corresponding to the `path`).
The local part corresponds to the `query` component of a URI and can additional be fine-tuned by the use of a fragment.
This document will address the naming authority, resource key, and query parts of the URI.

## Naming Authority

There is no requirement that the naming authority component correspond to a public web site since the value is looked up in the VO Registry.
Indeed, IVOA recommendation is to deliberately avoid using a website with examples given such as `ivo://org.gavo.dc/` (reversing the internet address) and `ivo://adil.ncsa` (publishing organization and archive).

This suggests Rubin should consider:

* `lsst.rubin`
* `rubin.lsst`
* `org.lsst`
* `org.rubinobservatory`
* `org.rubinobs`

Given that there is potential for a non-LSST survey in the future and given the naming convention we use for Jira hosting we have decided that Rubin will use `org.rubinobs` as the naming authority.

## Resource Key

The resource key allows us to segregate our registry entries.
For example we could do what GAVO does and use `~` to indicate that all our resources are using a single registry entry.
We could also segregate based on type of dataset or data release.

We feel that registry entries per data release are essential.
Given there is also a desire for a IVO ID to indicate which data access center the data come from, we intend to include both the DAC and the data release in the resource key.

Examples are:

* `usdac/lsst-dp1`
* `ukdac/lsst-dr1`

## Query

The query part of the IVOID indicates how a specific dataset should be referenced.
For a Butler dataset we would need the repository label and the dataset UUID.
This may result in duplication of data release information from the resource key but we do not see that as a problem.
The query string can be either a string that should be parsed into components or use the more explicit query string format.
Rather than using something like `?label/UUID` we have decided to use the more explicit form of `?repo=label&id=UUID`.

### Catalog Entries

There is no requirement for us to issue IVOA identifiers for individual catalog entries, but there is nothing to prevent this if we so desire.
Catalog IDs are meant to be unique for a given data release but are not necessarily unique across the entire lifetime of the survey for all ID types.

In a similar way to our handling of query strings for Butler datasets we propose a form of `?type=object&release=dr1&id=OBJECTID` for catalog entries.
Here type can be `object`, `source`, `diaobject`, `diasource`, or `forcedsource`.


## Combined Example

Given the decisions from the previous sections we propose that our IVO identifiers will have the form:

* `ivo://org.rubinobs/usdac/dr1?repo=dr1&id=UUID`
* `ivo://org.rubinobs/usdac/dp1?type=object&release=dp1&id=OBJECTID`


## References

```{bibliography}
  :style: lsst_aa
```
