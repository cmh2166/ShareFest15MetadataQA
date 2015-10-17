# Generating MARCEdit Field and Type Reports
_If you don't have MARCEdit installed, go to http://marcedit.reeset.net/downloads and follow the instructions for your operating system._

## About MARCEdit
MARCEdit displays MARC records using the [MARCBreaker format (.mrc)](http://www.loc.gov/marc/makrbrkr.html). The basics are given below:

### How MARCEdit presents MARC Records:
- Delimiters = $
- Blank indicator = \
- Field terminators in MARCEdit = at the beginning of each line/field
- Record terminators in MARCEdit are 1 blank Line between each MARC record. 
- Always 2 blank spaces between 3 digit field tag and indicator positions 
- In MARCEdit there always has to be $a to begin all variable fields - $a is NOT assumed.
- In MARCEdit there are no spaces between delimiter, subfield letter/number, text data. 

### Example:
=245 00$aText of marc field$h[electronic resource] :$bthe rest of the story /$cMickey Mouse.
=260 
$aCambridge :$bCambridge University Press,$c2011
=651 \0$aEurope$xHistory.
=856 40$uhttp://digital.films.com/PortalPlaylists.aspx?aid=17730&xtid=2669 
MARCEdit text record example: 
=LDR 01258nam a22003378a 4500
=001 CR9780511910616
=003 UkCbUP
=005 20120927050353.0
=006 m||||||||d||||||||
=007 cr||||||||||||
=008 100824s2011||||enk\\\\\s\\\\\||1\0|eng|d
=020 \\ $a 9780511910616 (ebook)
=020 \\ $a 9781107008045 (hardback)
=040 \\ $a UkCbUP$cUkCbUP
=050 00 $a QA248 $b .S4125 2012
=082 00 $a 510223
=245 00 $a Set Theory, Arithmetic, and Foundations of Mathematics $h[electronic resource] :$b Theorems, Philosophies /$cEdited by Juliette Kennedy, Roman Kossak.
=260 \\ $a Cambridge : $b Cambridge University Press, $c 2011
=300 \\ $a 1 online resource (242 p.) : $b digital, PDF file(s).
=490 0\ $a Lecture Notes in Logic $v no. 36
=500 \\ $a Title from publishers bibliographic system (viewed on 27 Sep 2012).
=530 \\ $a Also issued in print format.
=538 \\ $a Mode of access: World Wide Web.
=650 \0 $a Set theory.
=650 \0 $a Logic, Symbolic and mathematical.
=650 \0 $a Mathematics $x Philosophy.
=650 \7 $a MATHEMATICS / Logic. $2 bisacsh
=700 1\ $a Kennedy, Juliette.
=700 1\ $a Kossak, Roman.
=776 08 $i Print version: $z 9781107008045
=856 40 $u http://dx.doi.org/10.1017/CBO9780511910616 $z Access by subscription 

## Import MARC into MARCEdit & Move to UTF-8
1. Records should be binary MARC21 (.mrc) or MARCBreaker (.mrk). MARCEdit does have tools for conversion/transformation of other formats, but we're focusing on MARC files here.
2. If binary MARC (.mrc):
    3. Use MARCEdit to first convert MARC records to MARC21, UTF-8, and make a text file available for review:
    3. Click File > MARC Tools > MARC Breaker.
    4. Browse for your MARC file.
    5. Choose a place for Output file but with the .mrk extension.
    6. Under Functions, the MarcBreaker radio button should be selected by default.
    7. Check "Translate to UTF8" box
    8. Click Execute
    9. Will give a message in results box, such as: 384 records were processed in 0.390004 seconds
    10. Click "Edit Records" Button at bottom to open the file into the MarcEditor.
    11. You're ready to go.
3. If MarcBreaker (.mrk):
    4. Open 'Editor', then File > Open the MARC (.mrk) record.
    5. You're ready to go.

## Generate Reports
In the MARCEdit Editor (opened at the end of the above steps), we now can generate a number of reports.

### Generate a Field Usage Report
1. In the MARCEditor Screen, go to Reports > Field Count.
2. In the dialog box that appears, click Generate Report button.
3. Save the report as .txt file in your chosen directory.
4. This report then allows you to quickly review that all records have the required fields and access points, examine for for inconsistencies, and be mindful of locally-assigned fields that may cause problems.

### Generate an Item Type Report
1. In the MARCEditor Screen, go to Reports > Material Type Report > Generate Report.
2. To save this report locally, unfortunately, you'll need to copy/paste into a new text file.
