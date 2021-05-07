# Course

## INDEX


Response
<details>
  <summary>Click to expand!</summary>
  
<p>

    [
    {
        "id": 110,
        "unit_title": "",
        "level": "",
        "no_of_lesson": "1",
        "description": "",
        "design_type_id": 1,
        "created_by": 1,
        "updated_by": 1,
        "is_deleted": 0,
        "created_at": "2021-04-21 16:30:05",
        "updated_at": "2021-04-21 16:30:05",
        "coursetype": 1,
        "is_pin": 0,
        "is_finish": 0,
        "subject": null,
        "school": null,
        "sch_cc_goal": null,
        "technology": null,
        "prior_knowledge": null,
        "highlight": null,
        "reflection": null,
        "permission": 100,
        "createdby": {
            "id": 1,
            "name": "system_admin",
            "school": "system",
            "email": "villa@ilap-sdls.cite.hku.hk",
            "email_verified_at": null,
            "created_at": null,
            "updated_at": null,
            "display_tourguide": 0,
            "is_admin": 1
        },
        "usergroupid": [],
        "tags": []
    },
    {
        "id": 107,
        "unit_title": "Mental Health",
        "level": "Undergradute Students",
        "no_of_lesson": "0",
        "description": "tbc",
        "design_type_id": 4,
        "created_by": 1,
        "updated_by": 1,
        "is_deleted": 0,
        "created_at": "2021-02-22 18:54:30",
        "updated_at": "2021-03-02 16:42:06",
        "coursetype": 1,
        "is_pin": 0,
        "is_finish": 1,
        "subject": "",
        "school": null,
        "sch_cc_goal": null,
        "technology": null,
        "prior_knowledge": null,
        "highlight": null,
        "reflection": null,
        "permission": 100,
        "createdby": {
            "id": 1,
            "name": "system_admin",
            "school": "system",
            "email": "villa@ilap-sdls.cite.hku.hk",
            "email_verified_at": null,
            "created_at": null,
            "updated_at": null,
            "display_tourguide": 0,
            "is_admin": 1
        },
        "usergroupid": [],
        "tags": []
    },
    ...
    ]

</p>

</details>


## GET

Response
<details>
  <summary>Click to expand!</summary>
  
<p>

    {
    "id": 110,
    "unit_title": "Test",
    "level": "Primary",
    "no_of_lesson": "1",
    "description": "Test LD",
    "design_type_id": 4,
    "created_by": 1,
    "updated_by": 1,
    "is_deleted": 0,
    "created_at": "2021-04-21 16:30:05",
    "updated_at": "2021-05-06 11:16:13",
    "coursetype": 1,
    "is_pin": 0,
    "is_finish": 0,
    "subject": "Science",
    "school": "Test School",
    "sch_cc_goal": "Testing",
    "technology": "AI, Programming",
    "prior_knowledge": "C#, ASP .NET, React",
    "highlight": null,
    "reflection": null,
    "test": {
        "id": 1,
        "name": "system_admin",
        "school": "system",
        "email": "villa@ilap-sdls.cite.hku.hk",
        "email_verified_at": null,
        "created_at": null,
        "updated_at": null,
        "display_tourguide": 0,
        "is_admin": 1
    },
    "permission": 100,
    "componentid": [
        {
            "course_id": 110,
            "component_id": 159
        }
    ],
    "components": [
        {
            "id": 159,
            "component_template_id": 12,
            "title": "Strategic Curriculum Component",
            "sequence": 1,
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:07",
            "updated_at": "2021-05-06 11:16:07",
            "laravel_through_key": 110,
            "tasks": [],
            "patterns": [
                {
                    "id": 149,
                    "title": "Blank Task Sequence",
                    "created_by": 1,
                    "updated_by": 1,
                    "is_deleted": 0,
                    "created_at": "2021-05-06 11:16:07",
                    "updated_at": "2021-05-06 11:16:07",
                    "laravel_through_key": 159,
                    "tasks": []
                }
            ],
            "outcomeid": [],
            "patterntaskid": [
                {
                    "task_id": null,
                    "component_id": 159,
                    "pattern_id": 149,
                    "sequence": 1
                }
            ],
            "sdlid": [],
            "dpid": []
        }
    ],
    "outcomes": [],
    "outcomeid": [],
    "lessons": [
        {
            "id": 153,
            "title": "Lesson1",
            "sequence": 1,
            "time": 15,
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:00",
            "updated_at": "2021-05-06 11:16:00",
            "laravel_through_key": 110,
            "tasks": [],
            "tasksid": []
        }
    ],
    "lessonid": [
        {
            "course_id": 110,
            "lesson_id": 153
        }
    ],
    "createdby": {
        "id": 1,
        "name": "system_admin",
        "school": "system",
        "email": "villa@ilap-sdls.cite.hku.hk",
        "email_verified_at": null,
        "created_at": null,
        "updated_at": null,
        "display_tourguide": 0,
        "is_admin": 1
    },
    "tags": [
        {
            "id": 19,
            "name": "error",
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:01",
            "updated_at": "2021-05-06 11:16:01",
            "laravel_through_key": 110
        },
        {
            "id": 20,
            "name": "mirror",
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:01",
            "updated_at": "2021-05-06 11:16:01",
            "laravel_through_key": 110
        }
    ],
    "evidences": []
    }

</p>

</details>

## POST

Request
<details>
  <summary>Click to expand!</summary>

 <p>

NAME | TYPE | REQUIRED | REMARK
--- | --- | --- | ---
unit_title	| string | N | 
level	| string| N |
subject |  string | N | 
no_of_lesson | /int	| N | 
description | string | N |
is_finish | boolean | N| 
coursetype | int | N | 
school | string | N |
sch_cc_goal | string | N |
technology| string | N |
prior_knowledge | string | N |
highlight | string | N |
reflection | string | N |
usergroup | array | N | array of user group id object
tag | array | N | array of tag object 
</p>

</details>

Response
<details>
  <summary>Click to expand!</summary>
  
<p>

    {
    "id": 110,
    "unit_title": "Test",
    "level": "Primary",
    "no_of_lesson": "1",
    "description": "Test LD",
    "design_type_id": 4,
    "created_by": 1,
    "updated_by": 1,
    "is_deleted": 0,
    "created_at": "2021-04-21 16:30:05",
    "updated_at": "2021-05-06 11:16:13",
    "coursetype": 1,
    "is_pin": 0,
    "is_finish": 0,
    "subject": "Science",
    "school": "Test School",
    "sch_cc_goal": "Testing",
    "technology": "AI, Programming",
    "prior_knowledge": "C#, ASP .NET, React",
    "highlight": null,
    "reflection": null,
    "test": {
        "id": 1,
        "name": "system_admin",
        "school": "system",
        "email": "villa@ilap-sdls.cite.hku.hk",
        "email_verified_at": null,
        "created_at": null,
        "updated_at": null,
        "display_tourguide": 0,
        "is_admin": 1
    },
    "permission": 100,
    "componentid": [
        {
            "course_id": 110,
            "component_id": 159
        }
    ],
    "components": [
        {
            "id": 159,
            "component_template_id": 12,
            "title": "Strategic Curriculum Component",
            "sequence": 1,
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:07",
            "updated_at": "2021-05-06 11:16:07",
            "laravel_through_key": 110,
            "tasks": [],
            "patterns": [
                {
                    "id": 149,
                    "title": "Blank Task Sequence",
                    "created_by": 1,
                    "updated_by": 1,
                    "is_deleted": 0,
                    "created_at": "2021-05-06 11:16:07",
                    "updated_at": "2021-05-06 11:16:07",
                    "laravel_through_key": 159,
                    "tasks": []
                }
            ],
            "outcomeid": [],
            "patterntaskid": [
                {
                    "task_id": null,
                    "component_id": 159,
                    "pattern_id": 149,
                    "sequence": 1
                }
            ],
            "sdlid": [],
            "dpid": []
        }
    ],
    "outcomes": [],
    "outcomeid": [],
    "lessons": [
        {
            "id": 153,
            "title": "Lesson1",
            "sequence": 1,
            "time": 15,
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:00",
            "updated_at": "2021-05-06 11:16:00",
            "laravel_through_key": 110,
            "tasks": [],
            "tasksid": []
        }
    ],
    "lessonid": [
        {
            "course_id": 110,
            "lesson_id": 153
        }
    ],
    "createdby": {
        "id": 1,
        "name": "system_admin",
        "school": "system",
        "email": "villa@ilap-sdls.cite.hku.hk",
        "email_verified_at": null,
        "created_at": null,
        "updated_at": null,
        "display_tourguide": 0,
        "is_admin": 1
    },
    "tags": [
        {
            "id": 19,
            "name": "error",
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:01",
            "updated_at": "2021-05-06 11:16:01",
            "laravel_through_key": 110
        },
        {
            "id": 20,
            "name": "mirror",
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:01",
            "updated_at": "2021-05-06 11:16:01",
            "laravel_through_key": 110
        }
    ],
    "evidences": []
    }

</p>

</details>


## PUT
Request
<details>
  <summary>Click to expand!</summary>

 <p>

NAME | TYPE | REQUIRED | REMARK
--- | --- | --- | ---
unit_title	| string | N | 
level	| string| N |
subject |  string | N | 
no_of_lesson | /int	| N | 
description | string | N |
is_finish | boolean | N| 
coursetype | int | N | 
school | string | N |
sch_cc_goal | string | N |
technology| string | N |
prior_knowledge | string | N |
highlight | string | N |
reflection | string | N |
usergroup | array | N | array of user group id object
tag | array | N | array of tag object 
</p>

</details>

Response
<details>
  <summary>Click to expand!</summary>
  
<p>

    {
    "id": 110,
    "unit_title": "Test",
    "level": "Primary",
    "no_of_lesson": "1",
    "description": "Test LD",
    "design_type_id": 4,
    "created_by": 1,
    "updated_by": 1,
    "is_deleted": 0,
    "created_at": "2021-04-21 16:30:05",
    "updated_at": "2021-05-06 11:16:13",
    "coursetype": 1,
    "is_pin": 0,
    "is_finish": 0,
    "subject": "Science",
    "school": "Test School",
    "sch_cc_goal": "Testing",
    "technology": "AI, Programming",
    "prior_knowledge": "C#, ASP .NET, React",
    "highlight": null,
    "reflection": null,
    "test": {
        "id": 1,
        "name": "system_admin",
        "school": "system",
        "email": "villa@ilap-sdls.cite.hku.hk",
        "email_verified_at": null,
        "created_at": null,
        "updated_at": null,
        "display_tourguide": 0,
        "is_admin": 1
    },
    "permission": 100,
    "componentid": [
        {
            "course_id": 110,
            "component_id": 159
        }
    ],
    "components": [
        {
            "id": 159,
            "component_template_id": 12,
            "title": "Strategic Curriculum Component",
            "sequence": 1,
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:07",
            "updated_at": "2021-05-06 11:16:07",
            "laravel_through_key": 110,
            "tasks": [],
            "patterns": [
                {
                    "id": 149,
                    "title": "Blank Task Sequence",
                    "created_by": 1,
                    "updated_by": 1,
                    "is_deleted": 0,
                    "created_at": "2021-05-06 11:16:07",
                    "updated_at": "2021-05-06 11:16:07",
                    "laravel_through_key": 159,
                    "tasks": []
                }
            ],
            "outcomeid": [],
            "patterntaskid": [
                {
                    "task_id": null,
                    "component_id": 159,
                    "pattern_id": 149,
                    "sequence": 1
                }
            ],
            "sdlid": [],
            "dpid": []
        }
    ],
    "outcomes": [],
    "outcomeid": [],
    "lessons": [
        {
            "id": 153,
            "title": "Lesson1",
            "sequence": 1,
            "time": 15,
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:00",
            "updated_at": "2021-05-06 11:16:00",
            "laravel_through_key": 110,
            "tasks": [],
            "tasksid": []
        }
    ],
    "lessonid": [
        {
            "course_id": 110,
            "lesson_id": 153
        }
    ],
    "createdby": {
        "id": 1,
        "name": "system_admin",
        "school": "system",
        "email": "villa@ilap-sdls.cite.hku.hk",
        "email_verified_at": null,
        "created_at": null,
        "updated_at": null,
        "display_tourguide": 0,
        "is_admin": 1
    },
    "tags": [
        {
            "id": 19,
            "name": "error",
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:01",
            "updated_at": "2021-05-06 11:16:01",
            "laravel_through_key": 110
        },
        {
            "id": 20,
            "name": "mirror",
            "created_by": 1,
            "updated_by": 1,
            "is_deleted": 0,
            "created_at": "2021-05-06 11:16:01",
            "updated_at": "2021-05-06 11:16:01",
            "laravel_through_key": 110
        }
    ],
    "evidences": []
    }

</p>

</details>

## DELETE
Request
<details>
  <summary>Click to expand!</summary>

 <p>

verb | endpoint | action
--- | --- | ---
GET	| /test | index
GET	| /test/{id} | show
POST |  /test | store
PUT/PATCH | /test/{id}	| update
DELETE | /test/{id} | destroy

</p>

</details>

Response
<details>
  <summary>Click to expand!</summary>
  
<p>

    success

</p>

</details>