# CookFrame
Automated Approach for Constructing Framework Instantiation Documentation

A substantial effort, in general, is required for understanding APIs of application frameworks.  High-quality API documentation may alleviate the effort, but the production of such documentation still poses a major challenge for modern frameworks. To facilitate the production of framework instantiation documentation, we hypothesize that the framework code itself and the code of existing instantiations provide useful information. However, given the size and complexity of existent code, automated approaches are required to assist the documentation production. We propose an automated approach for constructing relevant documentation for framework instantiation based on source code analysis of the framework itself and of existing instantiations. The proposed approach organizes documentation in a Cookbook style, where the recipes are programming activities using the necessary API elements driven by the framework features.  We performed an empirical study, consisting of 3 experiments with 44 human subjects executing real framework instantiations aimed at comparing the use of the proposed Cookbooks to traditional manual framework documentation (baseline). The comparison criteria were time spent and correctness during instantiation activities, information usefulness, complexity of the activity, navigation, satisfaction, information localization and clarity. Our empirical assessment demonstrates that the generated Cookbooks presented better or, at least, non-significant difference when compared to the traditional documentation

## Tools:

1 - TraceExtractor:
 Repository File: TraceExtractor.rar 
    
    We use the TraceExtractor to apply feature location technique based on dynamic analysis where execution traces are used to locate
    the sets of code elements implementing the features of interest in existing applications. These traces are extracted during the
    execution of a scenario that represents adequately the feature. The only need is to know the applications features and know how to
    execute them. A "start" and "end" markings of a feature execution enable the slicing of the differentiation of traces for features
   
    
2- Java2RSF:

   Repository File: Java2rsf.rar
   https://github.com/arend-von-reinersdorff/java2rsf
   
   Static information about the framework  and  existing  application  source  code  are  obtained using the  Java2RSF1tool.  This  tool  returns  the  informa-tion  in  the  Rigi  Standard  Format  (RSF - http://www.rigi.cs.uvic.ca/downloads/rigi/doc/node52.html),  a  suitable  formatfor  further  processing.  The  RSF  format  present  relations  on packages, classes, interface methods, parameters and types.
   
3- Design Pattern detection Tool:

   You can download it from https://users.encs.concordia.ca/~nikolaos/pattern_detection.html
   
   A design pattern detection tool (https://users.encs.concordia.ca/~nikolaos/pattern_detection.html), a static approach created by Tsantalis and colleagues  is used to obtain the design patterns related to the hot-spots.

4- CookFrame:
   Repository Files: CookFrame_FilterRules.ra
                     CookFrame.zip
          

## Outputs generated by the tools:

1- Trace:

   Repository File: 
   
   File generated using: TraceExtractor.
   
2- RSF:

   Repository File: 
   
   File generated using Java2RSF.

3- Cookbook: 

   Repository File: CookbookJHotDraw.rar
   
   File generated using CookFrame_FilterRules and CookFrame. 





