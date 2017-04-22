
VAST Release Notes
===================
4.0.5
-----
* Updated tracking events to match spec (Issue #5)
* UniversalAdId attributes are required
* Multiple updates on Icon, MediFile, etc (Issue #6)


4.0.4
-----
* Reorganize XSD element order for alphabetical within a type.
* Sync to validate against all sample VAST xmls.
* Adjust to process Extensions correctly


4.0.3
-----
* Minimum occurrance of MediaFile updated to agree with latest VAST 4.0 spec.
* Github #2 -> Addition of missing Extension element under Extensions
* Attribute casing issue
* Github #3 -> Missing Verification element for Inline elements
* Github #1 -> Creatives changed to not be required element under Wrapper


4.0.2
-----
* Changes to address cardinality issues in some elements (change 0-1 to 0+)
* Update to require an Impression element

4.0.1
-----
* Updated schema to work with code generation tools JAXB (Java) and xsd.exe (.Net)
* Change id attributes to be strings instead of xs:ID type

4.0.0
-----
Initial release of the vast 4 XSD schema.



