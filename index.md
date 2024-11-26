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

If `lsst` is in the authority name that implies we would change the authority name in the future for some potential non-LSST survey in the late 2030s.

## Resource Key

The resource key allows us to segregate our registry entries.
For example we could do what GAVO does and use `~` to indicate that all our resources are using a single registry entry.
Alternatively we could segregate by butler datasets vs catalog content or have a resource per data release.

* `~`
* `butler`
* `datasets`
* `lsst`
* `lsst-dr1`
* `catalog`

## Query

The query part of the IVOID indicates how a specific dataset should be referenced.
In theory this could be the Butler dataset UUID or the source/object catalog ID without any other information.
In practice we would not want to look in all possible butler repositories for a matching dataset ID and so the Butler label should be included (assuming we aren't encoding the butler repository in the resource key section).

* `?dr1/UUID`
* `?/repo/main/UUID`
* `?butler/dp1/UUID`

As can be seen from the previous section it is still unclear whether `butler?dr1/UUID`, `butler/dr1?UUID` or `lsst?butler/dr1/UUID` are preferred.

All our catalog IDs encode the data release and the catalog entry type (source vs object vs DIA variants) within them so there is no requirement for a data release to be explicitly included or to note whether it is a source or not.
From a readability perspective it would help if that information was included.

* `?object/dr1/1234567890`
* `?source/dr1/1234567890`

An alternative is to explicitly use keyword/value form:

* `?repo=/repo/main&id=UUID`
* `?type=object&release=dr1&id=OBJECT_ID`

## Putting it All Together

The previous sections would suggest that a butler IVOID could look like:

* `ivo://rubin.lsst/datasets?dr1/UUID`
* `ivo://rubin.lsst/catalog?source/dr1/SOURCE_ID`

## References

```{bibliography}
  :style: lsst_aa
```
