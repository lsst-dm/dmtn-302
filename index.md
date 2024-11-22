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
* `org.lsst`
* `org.rubinobservatory`
* `org.rubinobs`

## Resource Key

The resource key allows us to segregate our registry entries.
For example we could do what GAVO does and use `~` to indicate that all our resources are using a single registry entry.
Alternatively we could segregate by butler vs catalog content or have a resource per data release.

* `~`
* `butler`
* `lsst`
* `lsst-dr1`

## Query

The query part of the IVOID indicates how a specific dataset should be referenced.
In theory this could be the Butler dataset UUID or the source/object catalog ID without any other information.
In practice we would not want to look in all possible butler repositories for a matching dataset ID and so the Butler label should be included (assuming we aren't encoding the butler repository in the resource key section).

* `?dr1/UUID`
* `?/repo/main/UUID`
* `?butler/dp1/UUID`

As can be seen from the previous section it is still unclear whether `butler?dr1/UUID`, `butler/dr1?UUID` or `lsst?butler/dr1/UUID` are preferred.

All our catalog IDs encode the data release within them so there is no requirement for a data release to be explicitly included.

* `?object/1234567890`
* `?source/1234567890`

## Putting it All Together

The previous sections would suggest that a butler IVOID could look like:

* `ivo://rubin.lsst/butler?dr1/UUID`

## References

```{bibliography}
  :style: lsst_aa
```
