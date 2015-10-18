# About Catmandu & Uses at UTK

Catmandu is increasing in importance, but it is still used relavively little at UTK. We tend to use it when MARCEdit doesn't do 1. what we need 2. what we want on really big datasets, and there already exists in Catmandu something we'd need to write ourselves in Python (like the Fix language).

We rely a lot on Catmandu's Fix language (although I'm still learning more about it all the time), as it is meant to give non-techs/non-developers an easy access point to metadata transformation. Yet, often, it does run into issues that it helps to know a bit about data structures and what Catmandu Fix language is up to (i.e. working with arrays is a big one). So it maybe is not for the complete luddite.

I'm not going to write up my procedures here for using Catmandu; instead, I will point you to the [Catmandu handbook](http://librecat.org/Catmandu/), which has lots of helpful places for getting started. Additionally, Catmandu can be a real pain to install, especially if (like me) you're not a regular Perl user.

I have included here the Fix files and sample output from them that I reference in the presentation. The commands used to generate these reports with these fix files are below:

```bash
$ catmandu convert MARC --type 'USMARC' --fix 'examples/Catmandu/MARCreconReport.fix' to YAML < examples/SampleData/sampleAlmaRecords.mrc > examples/Catmandu/MARCreconReport.yaml
$ catmandu convert MARC --type 'USMARC' --fix 'examples/Catmandu/MARCgeneralReport.fix' to CSV < examples/SampleData/sampleAlmaRecords.mrc > examples/Catmandu/MARCgeneralReport.csv
```
