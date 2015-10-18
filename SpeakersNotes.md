# Metadata Quality Analysis: Speakers Notes

## Slide one
Welcome to this presentation: Metadata Quality Analysis, tools and scripts to check your data.

I'm Christina Harlow, Cataloging and Metadata Librarian at the University of Tennessee, Knoxville, and I'm happy to be presenting to you today.

## Slide two
Everything I present today, including the slides, sample data, links to the scripts I use, and some instructions for how to generate the examples I show, are available in a GitHub repository available at that link on the slide. 

The link is bit.ly/metadataQA, and I'll show that link again at the end of this presentation.

## Slide three
What I am discussing today is for metadata quality analysis and metadata quality control. So we're not talking about metadata creation, updating, or data munging of any sort. These are ways we've found at UTK for reviewing our metadata before metadata munging.

Metadata review has become more important as the number of migrations we are or have done has increased. So a lot of the use cases, which then became examples for this presentation, are born from the need to review metadata before we move it to new platform or data model.

I'm going to present a range of tools that has to do with metadata quality and analysis review. They will go from the more user-friendly graphical user interface or GUI tools, to straight scripting with available libraries and modules. 

I will not talk about working with just one particular metadata format, model, encoding, standard or other; instead, this presentation touches on a range, including MARC (for work with our ILS), XML (used in many different platforms), and JSON (primarily used when reviewing external data from APIs or in preparation for Tennessee data showing up in the DPLA). Metadata schemas include at least basic and qualified Dublin Core, MODS, and the DPLA Metadata Application Profile version 4. We are working across a number of content standards.

## Slide four

So the first tool I'm going to talk about today is MARCEdit. MARCEdit is a freely available, but not open source, tool you can use for working with MARC records. It has a lot of helpful functions beyond what I will be talking about today, so I recommend that you check out the MARCEdit website which is on slide.

## Slide five

Here is a screenshot of the MARCEdit interface. You'll note MARCEdit uses a number of smaller windows. 

Here we have the MARCEdit editor open, with a MARC file loaded. We have the MARC validator tool open, and we have the MARCEdit start screen, which shows the core tools available.

Note that MARCEdit, in particular, the editor displays MARC in the MARCbreaker format. This makes it easier to review MARC records when editing. MARCEdit deals with a number of MARC serializations, but we will primarily be focused on working with binary MARC.

## Slide six
MARCEdit for metadata review has a number of pros and cons. 

1. MARCEdit is very easy to learn and install generally. It is meant to be an out of the box tool. 
2. MARCEdit can work with binary MARC, MARCbreaker, or MARC/XML, among other formats you might want converted to MARC. 
3. On that note, MARCEdit it comes with a number of standard conversions and transformations, including many of the MARC transformations written by the Library of Congress. 
4. MARCEdit has a number of helpful tools built in, including MARC validation, RDA helper, and a few new Linked Data tools. 
5. It generates many reports out of the box, which is very helpful for those who just need to run a report and not take the time to write the report for yourself. 
6. Some of the cons of working with MARCEdit is that it can have performance issues for larger data sets - and this is heavily dependent on the environment in which MARCEdit is installed. My work computer installation of MARCEdit, usually starts to slow down or choke on MARC sets larger than 50k record, depending on what I'm asking MARCEdit to do.
7. MARCEdit also is not well documented for trying to customize parts of the tool outside of using the interface - it is not open source. 

## Slide seven
At UTK, we use MARCEdit for metadata quality analysis primarily when reviewing vendor-supplied MARC records pre-ILS-ingest, and when working with/enhancing legacy MARC data. 

One of the things we want to do with both of those sets is to generate Field usage reports. These can show us very quickly the possible outliers for a data set, as well as help us know that our discovery interface indexing methods are optimized for our data. 

Another thing we want to do is to generate item type report. With these reports, we can get a better feeling for collection analysis, as well as what MARC catalog procedures we really need to focus on. We often used item type reports as well to target further metadata quality analysis. 

Some of the catalog staff uses MARCEdit quite a bit to generate CSV reports for a dataset, which offers another way to view and review MARC data and find outliers.

Finally, for metadata review, we use MARCEdit quite a bit for validation reports, including using our own targeted validation for groups of records - such as ebooks MARC records.

## Slide eight
Here is an example of the output of a Field Usage Report, generated in MARCEdit and opened then as a CSV in Google drive. In the GitHub repository for this presentation, you'll find a file where I go through just how we generated this report in MARCEdit.

Note how MARCEdit divides up the fields then subfields, then gives us numbers of usage. We can skim a report to see that all fields have things like creators, titles, and other dataset-specific fields.

## Slide nine
Here is the output of a MARCEdit Item Type report. This isn't as easy to pull out of MARCEdit and make into a spreadsheet or other, but is still helpful for us to check a set.

This report gets Item Types based off of the LDR position 6, then uses content type designators (245 subfield h in AACR2, 33* fields in RDA) to gather further information. You can easily spot here some typos in those fields.

## Slide ten

Here we have a CSV generated from chosen MARC fields - again, the procedure for doing this is in this presentation's GitHub repo at the file listed on the slide.

We pulled out the Record ID (001), the 007 posiion 00 (which you indicate in the MARCEdit CSV generation tool as if the position was a subfield), then a number of other fields. Note you can ask for a full field or a particular subfield of a field. These can helpful, like here, for reviewing things like RDA conversion (or preparation for that).

## Slide eleven
MARCEdit has built in the ability to do MARC validation - show is the MARC validation report output, which shows invalid records and why. This checks against a generic MARC validation file written for MARCEdit.

However, you can make your own MARC validation file, though you'll be working, like us, through trial and error to figure out the exact way it works in MARCEdit. This touches on the fact that MARCEdit is meant to be (and is) helpful out of the box. We do have a MARC Ebooks validation file, however, that checks for particular local fields we require pre-ingest into Alma.

## Slide twelve 
The next tool I want to mention in the context of metadata quality analysis is OpenRefine (formerly Google Refine). OpenRefine is a freely available, open source tool for working with all kinds of data. It has grown in popularity for libraries use in the past few years. The link to learn more and download OpenRefine is up on the slide.

## Slide thirteen
Here is a screenshot of the OpenRefine interface. OpenRefine takes your data and then works with in a tabular format - think of working in something like Excel but data-munging-focused. There are a lot of additional functionalities in OpenRefine, including many that we use at UTK, but I'm not going to talk about those here.

## Slide fourteen
Some of the pros of working with OpenRefine are:

1. OpenRefine gives a user-friendly GUI for working in.
2. It can handle importing and exporting a number of data types, though I have to warn you it is better for working with flatter data (heavily nested XML, for one example, is an issue).
3. There are a number of helpful ways to review, edit, and update your data in OpenRefine - including faceting, clustering, the Google Refine Expression Language or GREL, and reconciliation - or matching your data with an external data set.
4. Like mentioned above, it does export to a number of formats/document structures/encodings, though this is not always straight forward if you want something other than a CSV.
5. OpenRefine, like MARCEdit, can run into performance issues with bigger datasets, particularly as OpenRefine holds everything in memory while you're working. So the performance issues are dependent on your work environment as well.

## Slide fifteen
OpenRefine is used for metadata quality analysis at UTK as well as with our for work the Digital Library of Tennessee (our DPLA service hub) to review primarily non-MARC Metadata for mapping, normalization, and enhancement. We can get a very good idea of what is going on with a dataset before mapping, which is often necessary given that non-MARC metadata schema usage is often decided by the metadata creator for that collection and not always consistent across collections/projects.

OpenRefine allows us to Facet and Cluster fields, which is helpful for visual review; then target particular facets or filters for a field in that dataset and export just a subset; and review what fields are used how.

## Slide sixteen
In this screenshot, we see a slide of OpenRefine using both the facets and filters functions on a dataset. On the subject field/column, we have applied a facet that returns only the fields with the term 'Knoxville' present, then faceted to see all the possible values for that subject field/column that then fit that filter. We can quickly review to get a feeling for what the field has stored - corporate names, LCSH terms with typos or mis-applied, Publisher statements in the wrong field, etc.

## Slide seventeen
For the Digital Library of Tennessee, something we were really focused on was geographic normalization and enhancement for places of regional importance. To do this, we'd review each local institutions metadata in OpenRefine, then target the geographic terms by filtering and faceting. Here, we have a similar set up to the last slide, but we're looking for everything that has the term 'Tenn' in it. We can then sort the facets by count, review the top terms used, and write the normalization and enhancement of those into the DLTN aggregation transforms.

How to do what I'm discussing now is detailed in the GitHub repository for this presentation at the file listed on the slide.

## Slide eighteen
From that OpenRefine interface with facets and filters applied, we can export just that targeted subset of data for further review if needed. Here is an example of the CSV file generated from that group of records that have 'Tenn' in the subject field.

## Slide nineteen
Moving from the tools to the scripts now, python is what I'll discuss next. Python is a popular programming language used in all kinds of domains. Yet, we see python used quite a bit in libraries, archives and museums. For example, PyMARC is a popular python library for working with MARC records, and something we use some for MARC transformations and conversion work at UTK.

If you're completely new to python, there is also a decent code academy course on Python that is free and can get you started.

## Slide twenty
With python scripting, there are a number of pros:

1. You can generate the specific reports you need for all kinds (and all states) of data
2. There are many different python libraries, or sets of functionalities, available for library use (like PyMARC)
3. Python scripting runs way more quickly through large datasets - you won't run into the performance issues seen in tools like MARCEdit and OpenRefine.

The cons of using python though, are that:

1. You need to know some programming to get started. Often we start by modifying scripts that already exist, but this does require knowing how to read scripts and run in a Command Line Interface
2. Often, you also need to have the time to properly (or improperly but just for the sake of getting something done) build python scripts yourself.

## Slide twenty-one
For a lot of the UTK use of python in metadata quality analysis, we built our scripts off of work done already by Mark Phillips at the University of North Texas. A link to his work that we primarily worked off of are on the slide.

## Slide twenty-two
With that place to start, I've used python to run extended OAI review scripts to check our metadata feeds from a variety of platforms (for both UTK and for the Digital Library of Tennessee), and, in preparation for reviewing the DLTN data once it appears in the DPLA and thus is made available as JSON through the DPLA API.

## Slide twenty-three
Here is an excerpt of the script we use for review an OAI DC metadata set (this OAI-DC is the script we least edited from Mark Phillips' original). You can see here the options we offer for running this script - gather a full stats report, or target review of particular elements, among other options.

The full script is available at the link I've given on the slide - this is a GitHub repository containing the scripts I've pulled together for this presentation, as well as a preliminary document explaining how to use the ones mentioned here.

## Slide twenty-four
This is the output from running the OAI-DC python script against a dataset and request a stats review. We see each field in the dublin core namespace (whether it is valid or not) used in the dataset listed, then the percentage that field is used in comparison to the full dataset and other elements. 

This is extremely helpful for checking that 1. required elements are there 2. valid elements are used and 3. seeing what shouldn't be there (see our MODS test element at the bottom?).

We've also added a DPLA completeness ranking at the bottom that checks for the DPLA required fields, as part of the DLTN work.

## Slide twenty-five
However, at UTK we are more often working with MODS. So here is the output of using the OAI MODS analysis script against a MODS dataset - you can see (barely) that the MODS nested elements are captured.

This particular report is a review of our DLTN full MODS phase 1 feed exposed to the DPLA for ingest. Some interesting things pop up, like that mods:name/mods:namePart (or the name/creator/contributor) field is used very little, which is not suprising if you think about the content (special collections materials, photographs, etc.)

## Slide twenty-six
Here I show the start of a OAI DC field report, with the CLI command I put in to generate it (sorry for the weird colors, I tried to reset my client to colors that made better presentation screenshots). 

Here, I'm looking at all the *unique* dc:format fields in my dataset, then sort alphabetically, then adding the count (or number of times that particular field value appears in the set) before it. This is heavily indebted to the work done by Mark Phillips, and a great article he wrote on Metadata Quality Analysis at the command line - I link to his article at the top of the README in the MetadataQA github repository.

This allows us to get a feeling for how a field is used and find outliers.

## Slide twenty-seven
Better, though, is this method for doing quick review of things like encoding.

Here, I used the OAI MODS analysis script to pull a particular XPath query (something I added for better use with nested metadata). This query generates a list of all the unique mods:dateCreated values that are flagged (have an attribute) as EDTF encoding. I can then quickly review to see if any non-EDTF encoding fields are present.

## Slide twenty-eight
Here is an excerpt of the DPLA Json analysis script. The part I've screenshot here shows one of the difficulties in making review reports with the DPLA Json - you're not always sure of how fields are nested, and as the DPLA stores a lot of metadata from different sources and with different underlying schema, this varies quite a bit.

Yet, we were able to cobble together this script in preparation for the DLTN data showing up in DPLA soon-ish, so that we could review the data on both ends of the process and have a fuller picture.

## Slide twenty-nine
For example, with the DPLA analysis script, we can target particular fields using 'ObjectPath' - think XPath but for Json. This screenshot shows me reviewing the unique dataProvider field values from a DPLA dataset of objects that have creation dates after 2020. 

We've created a DPLA harvest script - also available in that GitHub repo - that can target the data you pull from the DPLA API to dates, providers to then run analysis on.

## Slide thirty
The final method for metadata review that I'm going to talk about today is Catmandu. Catmandu is a set of perl modules and a command line client for working with data. It was made as part of the LibreCat project, which aims to build interoperability and better tools for library data work. I'd recommend that you check out the Catamndu site, listed on the slide.

## Slide thirty-one
Catmandu is the newest thing we've been using at UTK, and its the one I know the least about at present. From my work with it, there are a number of pros:

1. Catmandu is highly customizable...
2. And it works with a lot of different data types.
3. It can make many different ETL - or extract, transform, load - processes. Think of metadata review and work between platforms, but as one command. This means that Catmandu comes with a lot of helpful data review functionalities already built in.
4. Catmandu, like python and other scripting, works well with the larger datasets that can make OpenRefine or MARCEdit choke.

Yet, like python...
1. Catmandu requires some programming knowledge to get started. However, I will say that the Catmandu team have done great work in writing documentation that helps completely newbies get started.
2. Catmandu also can be a pain to install, especially if you're new to Perl. 

## Slide thirty-two
At UTK for metadata review, we primarily use the Catmandu Fix language - a language built for easier transformation of data by non-programmers - for creating metadata reports we cannot do already in Python or with datasets too big for MARCEdit.

We have a number of 'fix routines' we used to generated MARC reports as needed.

## Slide thirty-three
For example, this is a Fix routine that checks if the controlled access points in each MARC record have URIs or identifiers in the $0 field. We'd run this before running any sort of reconciliation script, or to justify work done on adding URIs.

You can see here that the Fix language is meant to be easy to understand to non-programmers.

## Slide thirty-four
Here is the start of the YAML output (which I've also saved along with the fix routine to the GitHub repository for this presentation) from that report on a sample dataset of Alma records. You can see that only the fields we wanted are presented, along with the fields we created - nameRecon and subjectRecon (which checks to see if any of the name or Subject fields contains $0 URIs).

## Slide thirty-five
Here is a portion of the fix routine we used to generate CSV reports from vendor records. Again, the fix languages is meant to be easy to understand.

## Slide thirty-six
And this would be the start of the CSV file generated from that routine, opened in a spreadsheet program. You can see the fields that have multiple values - the 035 field for example, which we mapped to sysNumbers - need to be joined in some way, because if you don't, Catmandu leaves it as an array, and CSV output isn't sure what to do with that array.

We often run these reports both for metadata review on big sets as well as to generate collection development reports for sets of metadata we have to suppress or have other issues with.

## Slide thirty-seven
I hope this was a good start and introduction to metadata quality analysis and review, and my slides, notes, examples, etc. are all given or linked to in the GitHub repository, linked there.

If you have any questions or follow-up, you can ask me now or get in touch with me - my email address and Twitter handle are on the slide.

Thanks.
