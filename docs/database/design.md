# Design

<a href = "./image/course_1.png" >
    <img width="180px" style="width: 80%" bor src="./image/course_1.png">
</a>

> The diagram above simply shows the structure of a learning design. A Learning Design is generally form by three parts, the course itself, curriculum components and the learning outcomes. Each part is also associated with each other.

* course: Store the basic infomation of a course/ learning design. One course can have one or more curriculum component(s), learning outcome(s) and evidence
* course_outcome_relation: Identify the course can achieve which learning outcomes.
* course_component_relation: Identiy the course contains which curriculum component(s).
* evidence_course_relation:  Identiy the course contains which evidence(s).
* lesson_course_relation: Identiy the course contains which evidence(s).


* learningoutcome: Store the basic information of the learning outcome


* evidence: Store the evidence/ sample to have a showcase/ review during this learning design.


* component: Store the basic information of a curriculum component. A component can own one or more pattern(s), learning outcome(s) and learning tasks.
* learningpattern: Store the basic information of a learning pattern. A pattern must belong to a curriculum component and can own a sequence of learning tasks.
* learningtask: Store the basic information of a learning task. A task can be assoicated with a learning outcome if it is an assessment.
* component_outcome_relational: Identify the curriculum component(s) can achieve which learning outcome(s).
* component_pattern_task_relation: Identify the component contains which pattern(s)/ task(s) (one of two in a single record)
* pattern_task_rekational: Identify the relationship between a pattern and a list of learning task(s) which belongs to the parent pattern. 
* learningtask_assessment: Identify the assessment task can assess which learning outcome(s).


* lesson: Store the lesson information.
* lesson_task_lesson: Identify which task(s) is planned to be executed in the lesson.