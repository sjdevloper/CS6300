
<h4>Team 98 </h4>
<h4>CS6300 Summer 2020</h4>
<h4>Design Discussion Document</h4>
  
This document captures the design discussion for _Job Offer Comparison App_ based on the UML Class diagram and Design Description Document  provided as part of design.pdf file.

---
<h4> Abdulrahman Abdullah A Alnanih </h4>
Design Pros:

- The development of two separate classes “CurrentJob” and “JobOffer”, which inherit the overall attributes and method of the “Job” class, thus providing a level of anonymity in the design and distribution, resulting in a more object oriented design when it comes to modification of the modules.
- The separation of the “CompareSettings” class from the “JobComparison” class illustrates a level of encapsulation for the job comparison by hiding the settings attributes and values from the comparison entry system.

Design Cons:

- Although separating the jobs to different classes provides a more autonomous approach, it does also adds a level of complexity and interdependability between them and the master class “Jobs”.
- The apsense of the UI handler component at this stage of the design might cause some significant rework of the overall structure.
---
<h4> Sianvirath Chea </h4>
Design Pros:

- Our UML class diagram takes into factor all of the design requirements that George wants in this JobCompare application. It is simplified and showcases necessary functions, classes, and attributes that will generate a steady flow of actions for the user to accomplish what they want.
- The class diagram is normalized, especially between the association of JobOffer, CurrentJob, and Job Details. Taking into consideration that both JobOffer and CurrentJob uses Job Details, it is effective to create a general job details class to aggregate the design.

Design Cons:

- There might be some confusion on the design itself that isn’t straight forward, considering some of the function names aren’t necessarily in the list of requirements, but they still help accomplish tasks related to them. Most of the main functions are implemented within those functions, hence why they aren’t shown. Although UML class diagram could be straight forward, the design document should help uncover those function.
- ---
<h4> Shanshan Jiang </h4>
Design Pros:

- Our UML design considers all the factors and requirements mentioned in the project description. The design leverages granularity of all modules as well as complexity of this design in implementation.
- All our project members join the discussion. We follow the steps in the lecture when designing this UML graph. We went through all use cases we can imagine about how actual users will use this tool. We also dive deep into details at code level about how some functions could be coded.
- To define job related classes, we propose to have a general class called Job to contain all class members and functions that are shared across CurrentJob class and JobOffer class. We put as many as possible details and properties that could possibly be shared by CurrentJob and JobOffer to the Job class, so that CurrentJob and JobOffer can just focus on define whatever member function and members specifically needed in each class.
- To enable best flexibility, we create a separate JobScore class as a utility class. Such that it does not need to be instantiated, both CurrentJob and JobOffer can easily call it without any restriction.

Design Cons:

- I didn’t see too much of a disadvantage of our design in terms of achieving required functionality in project description. Something we didn’t consider thoroughly is probably how GUI related modules communicate with proposed classes in our design.
---
<h4> Balaji Prasad </h4>
Design Pros:

- The overall class diagram looks simple and easy to understand.
- Having CurrentJob and JobOffers as two separate classes. If there is a need for change in the business logic for CurrentJob vs JobOffers, it can be implemented without impacting each other. (Low coupling)
- Having the boolean isCurrentJob flag to differentiate between Current Job vs Future Job records.
- Having CalculateJobScore as a utility so that it could be used by any class.
- CurrentJob and JobOffers class inheriting from Job class.

Design Cons: 

- I think there could be still some class relationships missing or not clearly defined.
- I feel the method and variable constraints could’ve been defined well.
- I see the class diagram as more of a conceptual or specification representation which cannot be considered as a complete design and artifact for detailed implementation.
---
<h4> Summary </h4>
  
The team discussion was really useful as it brought multiple perspectives of the design and realizing the fact that there’s no one perfect way to design a system. The discussions were helpful in understanding the design components in detail and their relations better. **The team reached a consensus on the final design through a democtratic approach, where each person presented their own design’s perspective and each team member provided their feedback on the critical components and concepts, afterwhich** the task of putting together all individual designs into one with everyone on board, being respectful and humble during discussions, working towards the common goal of creating a good design, was a great teamwork and learning experience.
