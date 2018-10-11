This test belongs to [[3.1.2 Language of Parts]].
## Status
{{status|1|666}}
[[Category:Completed]]

## Description

This test checks that `lang` attributes within the body of a web page are correct.

## Background
- [http://www.w3.org/TR/2014/NOTE-WCAG20-TECHS-20140408/H58  H58: Using language attributes to identify changes in the human language]
- [http://wiki.egovmon.no/wiki/SC3.1.2#Element_descendent-or-self::body.5B.40lang.5D_or_descendent-or-self::body.5B.40xml:lang.5D eGovMon test for SC3.1.2]
- [http://www.rfc-editor.org/rfc/bcp/bcp47.txt BCP 47: Tags for the Identification of Languages]

## Assumptions
- The comparison of language-code does not look for exact matches. Technique H57 states: "Use of the primary code is important for this technique." which means that region subtags can be ignored in the comparison, i.e. "en-GB" is the same as "en".
- This test checks the `lang` attributes. The `xml:lang` attributes are not taken into account because tests have shown, that `xml:lang` is ignored by screenreaders. (Both Jaws 15 with FF and IE and NVDA with FF go by lang attribute, xml:lang is ignored.) The `xml:lang` attributes are checked by a separate test: [[SC3-1-2-xml-lang]].

## Test properties

| Property         | Value
|------------------|----
|Test name         |Languages within the body
|Success Criterion |[[3.1.2 Language of Parts]]
|Test mode         |automatic
|Test environment  |DOM
|Test subject      |single web page


## Test procedure

### Selector
Test method: [semi-automatic]
 descendent-or-self::body[@lang]

This test is applied to all elements with `lang` attribute in the body of the web page (including the body element itself).

### Step 1
Test method: [semi-automatic]
L1 = value of `lang` attribute.

Compare L1 to BCP 47.

If L1 is not on the list, return

{{Failed
|testcase = SC312-lang
|id = SC312-lang-fail1
|error = Unknown language code.
|info = L1
}}
*Note that this step also fails if L1 contains only whitespace or is empty.*

Else, return

{{Passed
|testcase = SC312-lang
|id = SC312-lang-pass1
}}