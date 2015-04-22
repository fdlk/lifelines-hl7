# lifelines-hl7
HL7 classes for lifelines web services

This is the 2009 normative edition HL7v3 XML schema.

It contains class ED that has mixed content and extends class BIN.
This is problematic. See [Handling extended mixed content in JAXB](https://blogs.oracle.com/mgrebac/entry/handling_extended_mixed_content_in).
Therefore the schema needs to be compiled with the customization `generateMixedExtensions="true"`.

The content field in the ED type gets annotated with annotation `@OverrideAnnotationOf`.
This annotation unfortunately is broken in the JAXB implementation embedded in the JDK since its xjc compiler writes out the standard package name for the annotation but the JDK has moved the annotation to a different internal package.

Therefore we *must* compile with an explicit version of JAXB-RI.