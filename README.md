# CookFrame
**Automated Approach for Constructing Framework Instantiation Documentation**

A substantial effort, in general, is required for understanding APIs of application frameworks.  High-quality API documentation may alleviate the effort, but the production of such documentation still poses a major challenge for modern frameworks. To facilitate the production of framework instantiation documentation, we hypothesize that the framework code itself and the code of existing instantiations provide useful information. However, given the size and complexity of existent code, automated approaches are required to assist the documentation production. We propose an automated approach for constructing relevant documentation for framework instantiation based on source code analysis of the framework itself and of existing instantiations. The proposed approach organizes documentation in a Cookbook style, where the recipes are programming activities using the necessary API elements driven by the framework features.  We performed an empirical study, consisting of 3 experiments with 44 human subjects executing real framework instantiations aimed at comparing the use of the proposed Cookbooks to traditional manual framework documentation (baseline). The comparison criteria were time spent and correctness during instantiation activities, information usefulness, complexity of the activity, navigation, satisfaction, information localization and clarity. Our empirical assessment demonstrates that the generated Cookbooks presented better or, at least, non-significant difference when compared to the traditional documentation.

## Tools:

- **1 - TraceExtractor:**

 *Repository File:* TraceExtractor.rar 
 
 *Output:* Traces

 We use the TraceExtractor to apply feature location technique based on dynamic analysis where execution traces are used to
 locate the sets of code elements implementing the features of interest in existing applications. These traces are extracted
 during the execution of a scenario that represents adequately the feature. The only need is to know the applications features
 and know how to execute them. A "start" and "end" markings of a feature execution enable the slicing of the differentiation 
 of traces for features.
   
    
- **2- Java2RSF:**

 *Repository File:* Java2rsf.rar
 
 *You can download it from:* https://github.com/arend-von-reinersdorff/java2rsf
   
 *Output:* RSF
      
Static information about the framework  and  existing  application  source  code  are  obtained using the  Java2RSF1tool.  This  tool
returns  the  informa-tion  in  the  Rigi  Standard  Format  (RSF - http://www.rigi.cs.uvic.ca/downloads/rigi/doc/node52.html),  a
suitable  formatfor  further  processing.  The  RSF  format  present  relations  on packages, classes, interface methods, parameters and 
types.
   
- **3- Design Pattern detection Tool:**

*You can download it from:* https://users.encs.concordia.ca/~nikolaos/pattern_detection.html
   
A design pattern detection tool (https://users.encs.concordia.ca/~nikolaos/pattern_detection.html), a static approach created by Tsantalis and colleagues  is used to obtain the design patterns related to the hot-spots.

- **4- CookFrame:**
   
*Repository Files:* CookFrame_FilterRules.ra
                     CookFrame.zip
   
*Output:* Cookbook
                     
CookFrame tool different filters on the input to obtain the hot-spots and activities related to a feature 
instantiation about classes and methods. Its inputs are the RSF relations and the traces for selected features. 

Once the activities are obtained, the CookFrame organize the information about all hot-spot classes and methods that could be used to 
instantiate the features into tables that organize the information for create the recipes in HTML format.
          

## Outputs generated by the tools:

- **1- Trace:**

 *Repository File:* 
   
 *File generated using:* TraceExtractor.
   
- **2- RSF:**

 *Repository File:* 
   
 *File generated using:* Java2RSF.
 
"The RSF files contain information such as actual software artifacts (and are described below). Domain-model files specify the valid verbs for these token-level RSF files. An RSF triple can represent an arc between two nodes to the graph editor: 
arcType startNodeName endNodeName. For example, using a domain model that has Function and Data type nodes interconnected by call and data access arcs, a token-level RSF stream then contains triples like:"

 
    call    main          printf  
    call    main          listcreate  
    data    main          FILE  
    data    listcreate    List  
    ...

- **3- Cookbook:** 

 *Repository File:* CookbookJHotDraw.rar
   
 *File generated using:* CookFrame_FilterRules and CookFrame. 

A Cookbook is composed of several recipes (item B), one for each desired feature of the instantiated application. The recipes are
composed of activities for implementing the respective feature (item C). There are four main activities organized within an index for
each one of them: (C1) implementation of hot-spot interfaces; (C2) direct subclassing of hot-spot classes; (C3) creation of
collaborations with hot-spot classes; (C4) indirect subclassing  of hot-spot classes by transitive inheritance.
This information is complemented by activities that occur within methods (item D), such as: (D1)  a list of methods from the hot-spot
class to invoke;  (D2) a list of methods from the hot-spot class to override; and/or (D3) instantiation of hot-spot class; These
activities (C) and methods (D) are enriched with documentation items (item E) about hot-spot classes or methods: (E1) signature of one
class declaration example that uses the hotspot; (E2) code comments on the hot-spot or;  (E3) occurring design patterns; and, (E4) code
examples of classes in existing instantiations that use those hot-spots classes or methods

Table I presents an excerpt of  the recipe **Remove a Figure**. This is a real recipe content of the JHotdraw framework
(http://www.jhotdraw.org/), and  one of the features of this framework is the possibility to define a new type of geometric figure and
remove them.

*TABLE I: CONTENT OF RECIPE Remove Figure FOR THE SUBCLASSING ACTIVITY*

**Activity: Extends StandardDrawing.**

          | Type of Information                          |  Information
          |----------------------------------------------|--------------------------------------------------------------------------|
          | C)- C2) Activity and hot-spot:               | Extends StandardDrawing                                                  |
          |----------------------------------------------|--------------------------------------------------------------------------|
          | E1) Signature of hot-spot class declaration: | public class StandardDrawing extends Composite-Figure implements Drawing |
          |----------------------------------------------|--------------------------------------------------------------------------|
          | E2) Code comments (class):                   | The standard implementation of the Drawing interface. @see Drawing       |
          |----------------------------------------------|--------------------------------------------------------------------------|
          | E3) Design Pattern (Class):                  |  Design Patterm: Observer                                                |
          |                                              |  Subject: ch.ifa.draw.standard.StandardDrawing                           |
          |                                              |  observers: Vector fListeners.                                           |
          |                                              |  Attach(Observer):addDrawingChangeListener.                              |
          |                                              |  Detach(Observer): removeDrawingChangeListener.                          |
          |                                              |  Notify(): figureInvalidated, figureRequestUpdate                        |
          |                                              |  Observer: ch.ifa.draw.framework.DrawingChangeListener                   |
          |                                              |  Update(): drawingInvalidated, drawingRequestUpdate                      |
          |----------------------------------------------|--------------------------------------------------------------------------|
          | D) - D1) Hotspot methods:                    |  remove(Figure figure)                                                   |
          |----------------------------------------------|--------------------------------------------------------------------------|
          | E2) Comments (methods):                      | Removes the figure from the drawing and releases it.                     |
          |----------------------------------------------|--------------------------------------------------------------------------|
          | E4) Usage examples (methods):                |  public synchronized Figure remove(Figure figure) {                      |
          |                                              |         Figure f = super.remove(figure);                                 |
          |                                              |              if (f instanceof AnimationDecorator)                        |
          |                                              |                  return ((AnimationDecorator)                            |
          |                                              |              f).peelDecoration();                                        |
          |                                              |                   return f; }                                            |
          |----------------------------------------------|--------------------------------------------------------------------------|
          
          
          

          



