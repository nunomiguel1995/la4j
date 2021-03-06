#Report 5: Software Maintenance/Evolution

##Index
1. [Introduction](#Intro)
2. [Software maintainability](#Maint)
3. [Evolution process](#Evolution)
4. [Pull Request](#Pull)

##Introduction  <a name="Intro"></a>

In this report we tried to discuss about software maintainability and evolution process of la4j. Software maintainability is defined as the degree to which an application is understood, repaired, or enhanced. Software maintainability is important because it is approximately 75% of the cost related to a project.And software evolution is the term used in software engineering (specifically software maintenance) to refer to the process of developing software initially, then repeatedly updating it for various reasons.

##Software maintainability  <a name="Maint"></a>

Software maintenance is the process of changing the software after it has been delivered, may be to correct coding or design errors or even to fulfil new requirements. Along comes software maintainability which is how easy a system can be modified and maintained. A good maintainability is a characteristic of software quality, since hardly no software stays unchangeable after its delivery.

Maintenance can be distinguished in four types: **corrective maintenance**, where bugs discovered are fixed, **adaptive maintenance** used to upgrade the system to adapted to environment changes, **perfective maintenance** where the software is changed to meet new requirements and, finally, **preventive maintenance** has the purpose to increase software quality in order to prevent future bugs from occurring. 

Software maintainability should be one of the main objectives when developing a new software. According to 'Building Maintainable Software' by Joost Visser "maintainability is a quality characteristic on a scale, it signifies different degrees of being able to maintain".  Software maintainability is an important characteristic of the system, because it can subsequently have a business and other quality characteristics impact.

By using the SIG metrics, we can establish if a given software is easy or hard to maintain. 


|SIG metric 	| Description
|---	        |---	
|Write short units of code 	  |  small units are easy to understand, easy to test and easy to reuse	
|Write simple units of code   |  keeping the number of branch points low makes units easier to modify and test	
|Write code once              |copied code makes that bugs need to be fixed at multiple places, which is inefficient and error-prone
|Keep unit interfaces small   |  keeping the number of parameters low makes units easier to understand and reuse 	
|Separate concerns in modules | changes in a loosely coupled codebase are much easier to oversee and execute than changes in a tightly coupled code‐ base	
|Couple architecture components loosely  	| isolated maintenance it’s easier with independent components
|Keep architecture components balanced 	  |   	balanced components makes it easier to locate code and allow for isolated maintenance
|Keep your codebase small  	  |   	keeping product, project and team size small is a crucial point for a successful software
|Automate tests             	| automated testing makes development foreseeable and less dangerous
|Write clean code             |clean code makes a maintainable software 


To test la4j SIG metrics it was used Better Code Hub at https://bettercodehub.com where the project score a three out of ten. This is not a good grade, since it means that this software it is going to be hard to maintain and it will affect its quality. The only metric that la4j follows are couple architecture components loosely, a small codebase and clean code. Next follows the link to the Better Code Hub analysis.

[![BCH compliance](https://bettercodehub.com/edge/badge/nunomiguel1995/ESOF-la4j)](https://bettercodehub.com)

##Evolution process  <a name="Evolution"></a>

Evolution is a stage that is present throughout all the system’s life cycle, in which it is developing and changing as new requirements are propose and implemented into the system.

No software stays unchangeable since it always needs to adapt to new requirements emerging, business environment changes, errors that need to be repaired and so on. Organizations spend the majority of the software investment, time and effort to maintain and evolve software, rather than creating new systems, since it will impact its business value. La4j is an open project with no economic interest, however the ability to evolve it’s crucial to its success.

Change identification and evolution continues throughout the system lifetime. Proposals for change are the drivers for the system evolution, they require the link with components that are going to be affected by the change, thus allowing the estimation of the cost and impact. The next stage it’s change implementation, which brings the major problem of software evolution and maintenance: program understanding. In other words, to successfully change the software and implement new feature we need to understand how the program is structured, how it delivers functionality and how the proposed change might affect the program. However, sometimes this could be a very hard task, especially if the system developers are not responsible for the change implementation.  A well organized, simple and well documented code will always make this task easier.

The main goal to this assignment it’s to understand how la4j is structured, how it delivers functionality and how a proposed change might affect the program. Since la4j is a library for advanced linear algebra, and implementing a new functionality or change one was going to be a task we couldn’t complete in a two-week assignment, as the professor suggested, we proposed to change some critical parts of the code that generate problems exposed in Better Code Hub. In order to try to improve the la4j score in Better Code Hub, we focused on the point “Write short units of code”.  This point is especially important since by having short units of code it becomes easier for new contributors to understand what was done and its objective. We chose this point because we believe that being able to join an ongoing project and easily understand what was done is very important and that for future developments of la4j it would help them to have smaller units of code so that new contributors wouldn't have a hard time understanding the code. Regarding that point we found various methods that had more than 100 lines of code. This lead us to the functions **select** in **CCSMatrix** and **CRSMatrix** classes. Both these classes use the same overloaded function so it would be simple to work around them. We then proceeded to understand the main points of those functions and how we could reduce their size because by doing this we would be able to know if it was possible to divide them into more functions. It was possible so we created two auxiliary functions: **getCardinality** and **constructSparseMatrix**. With that out of the way, we reduced the **select** to around 15 lines, while keeping the new functions with roughly the same size. There were other options but these would force us to change a lot of code in other parts of the project including other packages and tests, and because of that we concluded that la4j has a very strange structure regarding code organization: if something changes a great part of the project has to change as well and this isn't optimal.

##Pull Request  <a name="Pull"></a>

https://github.com/vkostyukov/la4j/pull/284

