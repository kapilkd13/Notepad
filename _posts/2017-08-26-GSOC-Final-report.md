---
layout: post
title: "CWL: A Great Experience!!"
description: Why this Blog!
headline: 
modified: 2017-08-26
category: GSOC
tags: [GSOC cwltool schema-salad CWL]
imagefeature: cwl-logo.svg
comments: true
mathjax: 
---

Final report of my GSOC'17 project with Common Workflow Language Organization


Official coding period for GSOC'17 has just ended and its time to sum up my work and present a final report on it. 

Aim of our project was to make cwltool and schema-salad windows compatible and work on other bugs and features. [Common Workflow Language](http://www.commonwl.org/v1.0/UserGuide.html) is a specification which is used to describe command line tools and workflows, providing benefits like flexibility, scalability and portability. [Cwltool](https://github.com/common-workflow-language/cwltool) is a reference implementation of the Common Workflow Language. It is intended to feature complete and provide comprehensive validation of CWL files as well as provide other tools related to working with CWL. [Salad](https://github.com/common-workflow-language/schema_salad) is a Apache Avro based schema language for describing JSON or YAML structured linked data documents. Cwltool depends on schema-salad for object creation, reference resolution and validation of CWL files. Since workflows and tool definitions can use unix tools, we decided to allow workflow execution inside a docker container when working with windows operating system.

We started our work with making schema-salad compatible with windows operating system. here is the merged [PR](https://github.com/common-workflow-language/schema_salad/pull/110). After that we started working on windows compatible cwltool. Some ofthe issues that we came across were unsupported scheme, Symliks on windows and windows path separator relatedd issues. We choose appeveyor CI for tsting cwltool implementation on windows OS. Once we passed all units tests on windows, we started working on passing conformance tests on windows and ensuring docker support for cwltool on windows. After resolving some time consuming issues like `Non blocking I/O operation`, `default docker container on windows`, we achieved widnows compatibility for cwltool. Here is the merged [PR](https://github.com/common-workflow-language/cwltool/pull/419).

After the windows compatible cwltool, I worked on the following bugs and features:

* **Python 3 support on Windows**: Once we made cwltool windows os compatible we found that it is having some issues with python 3 on windows. We fixed those errors and here is the final [PR](https://github.com/common-workflow-language/cwltool/pull/511).
* **Adding documentation file for windows compatibility**: Adding [documentation for windows](https://github.com/common-workflow-language/cwltool/pull/486) users of cwltool.
* **Allowing Http/Https files as input**: Earlier we used to load workflows over http but input files were still needed to be present locally. In this PR we added a feature to load inputs over http. File caching is used to avoid downloading files again. Here is the [PR](https://github.com/common-workflow-language/cwltool/pull/507).
* **Adding Testsuite to cwltest**: Cwltest repository is lacking a test suite to make sure that any new PR do not break the codebase. This PR aims at adding a test suite to the cwltest repo and is currently work-in-progress. see [PR](https://github.com/common-workflow-language/cwltest/pull/36) 
* **Adding --docker-pull flag to force pull latest docker image**: We [added a feature](https://github.com/common-workflow-language/cwltool/pull/506) to force pull latest docker image mentioned with dockerpull variable even if a image is locally present. We can do this using a --docker-pull command line argument. 
* **Using stdout field in cachekey calculation**: Taking account of [stdout field while calculating cachekey](https://github.com/common-workflow-language/cwltool/pull/532) for better cache results.
* **Removing unnecessary warning due to generation field**: Due to regression, unnecessary warning was being generated which we fixed in this [PR](https://github.com/common-workflow-language/cwltool/pull/525).
* **[Future module] Harcoded tmp folder prevent windows compatibilty of past module**: Since we are using `past module (part of future)` to run `avro-cwl` on python 3. This module has some hardcoded paths and is not compatible with windows OS. We [made a PR](https://github.com/PythonCharmers/python-future/pull/296) to fix that.

Some minor PR's like `avoiding use of exception.message in python 3` see [[here](https://github.com/common-workflow-language/cwltest/pull/30)], `fixing Nonetype not iterable error` [[here](https://github.com/common-workflow-language/cwltest/pull/23)], `Adding Build Badges to cwltool and schema-salad` [[here](https://github.com/common-workflow-language/cwltool/pull/413)] and `adding warning when default docker container is used` refer [[here](https://github.com/common-workflow-language/cwltool/pull/506)] were also made.


I would like to thank my mentors [Anton Khodak](https://github.com/anton-khodak), [Janneke van der Zwaan](https://github.com/jvdzwaan) and [Michael R. Crusoe](https://github.com/mr-c) for being cool and helping me on almost every step of this project. Also a big thanks to [Peter Amstutz](https://github.com/tetron) for his constant help. It was a great experience, working with all of you.

Overall, we met all the requirements and I consider it to be a successfull GSOC
. I hope my small contribution will help some people :)


