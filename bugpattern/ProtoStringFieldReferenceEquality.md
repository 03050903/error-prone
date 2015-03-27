---
title: ProtoStringFieldReferenceEquality
layout: bugpattern
category: ONE_OFF
severity: ERROR
maturity: EXPERIMENTAL
---

<div style="float:right;"><table id="metadata">
<tr><td>Category</td><td>ONE_OFF</td></tr>
<tr><td>Severity</td><td>ERROR</td></tr>
<tr><td>Maturity</td><td>EXPERIMENTAL</td></tr>
</table></div>

# Bug pattern: ProtoStringFieldReferenceEquality
__Comparing protobuf fields of type String using reference equality__

## The problem
Comparing strings with == is almost always an error, but it is an error 100% of the time when one of the strings is a protobuf field.  Additionally, protobuf fields cannot be null, so Object.equals(Object) is always more correct.

## Suppression
Suppress false positives by adding an `@SuppressWarnings("ProtoStringFieldReferenceEquality")` annotation to the enclosing element.
