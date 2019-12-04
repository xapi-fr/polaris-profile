# Profil Polaris : Statements

---

- [Règles communes](#rules)
- [Sessions au sol](#ground-sessions)
- [Sessions en simulateur ou vol avion](#flight-sessions)
- [Level Report](#level-report)
- [Skills Test](#skills-test)
- [Compétences](#competencies)
- [Annulation](#voiding)


<a name="rules"></a>
## Règles communes

### Tous les Statements

- Le `type` des activités DOIT être précisé.
- Le profil Polaris DOIT être indiqué dans la propriété `context.contextActivities.category`. 
- La propriété `context.platform` DOIT être précisée et avoir pour valeur `POLARIS`.
- La propriété `timestamp` DOIT être précisée.


### Statements de niveau principal (Learning Unit)

- La propriété `object.definition.name` DOIT être précisée. Elle indique le code de l'unité d'apprentissage.
- La propriété `object.definition.description` DOIT être précisée. Elle indique le nom de l'unité d'apprentissage.
- La propriété `context.contextActivities.parent` DOIT mentionner le module concerné.
- La propriété `context.contextActivities.grouping` DOIT mentionner la phase concernée.
- La propriété `context.contextActivities.grouping` DOIT mentionner le programme concerné.
- La propriété `context.contextActivities.grouping` DOIT mentionner la formation concernée.
- La propriété `context.contextActivities.category` DOIT mentionner le niveau de granularité en utilisant comme ID : `http://vocab.xapi.fr/categories/learning-unit`.
- La propriété `context.instructor` DOIT être présente et préciser l'instructeur concerné.


### Statements internes (Inside Learning Unit)

- La propriété `context.contextActivities.parent` DOIT mentionner l'unité concernée.
- La propriété `context.contextActivities.grouping` DOIT mentionner le module concerné.
- La propriété `context.contextActivities.grouping` DOIT mentionner la phase concernée.
- La propriété `context.contextActivities.grouping` DOIT mentionner le programme concerné.
- La propriété `context.contextActivities.grouping` DOIT mentionner la formation concernée.
- La propriété `context.contextActivities.category` DOIT mentionner le niveau de granularité en utilisant comme ID : `http://vocab.xapi.fr/categories/inside-learning-unit`.


<a name="ground-sessions"></a>
## Sessions au sol

### EXP-GRD-C - L’apprenant a assisté à un cours au sol.

- L'extension d'activité `remedial` DOIT être présente et avoir pour valeur `false`.
- L'extension d'activité `assessment` DOIT être présente et avoir pour valeur `false`.
- La propriété `result.completion` DOIT être présente et avoir pour valeur `true`.
- L'extension de contexte `location` DOIT être présente et préciser le lieu de la séance.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "f2b0adcb-a696-3c5f-aed9-ebca5b7aae91",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/0e032b33-83d4-3b8a-acfc-613a63cdb70c",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/face-to-face",
            "name": {
                "en": "GRD"
            },
            "description": {
                "en": "GRD name"
            },
            "extensions": {
                "http://vocab.xapi.fr/extensions/remedial": false,
                "http://vocab.xapi.fr/extensions/assessment": false
            }
        }
    },
    "result": {
        "completion": true
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/d539b903-cda9-34a2-8ed3-8307e7245b87",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/68083774-ef4e-3d53-95cb-6dc7e01a7092",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/9d1e38c9-9bc6-3df9-a059-193737111aa4",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/a7594730-3c60-3168-8df1-97ab586e24c5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "instructor": {
            "objectType": "Agent",
            "account": {
                "name": "b1f6a84b-de23-3e28-9f34-48344e2f20df",
                "homePage": "https://polaris.enac.fr"
            }
        },
        "platform": "POLARIS",
        "extensions": {
            "http://vocab.xapi.fr/extensions/location": {
                "id": "a34b46ea-629a-3641-94a2-3ad0ec085717",
                "name": "ENAC Biscarrosse"
            }
        }
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```


### EXP-GRD-S - L’apprenant a réussi/raté une évaluation au sol.

- La propriété `verb.id` DOIT avoir la valeur `http://adlnet.gov/expapi/verbs/passed` ou `http://adlnet.gov/expapi/verbs/failed`.
- L'extension d'activité `remedial` DOIT être présente et avoir pour valeur `false`.
- L'extension d'activité `assessment` DOIT être présente et avoir pour valeur `true`.
- La propriété `result.completion` DOIT être présente et avoir pour valeur `true`.
- La propriété `result.success` DOIT être précisée (`true` ou `false`).
- L'extension de résultat `abnormal-procedure` PEUT être présente avec pour valeur `true` afin d'indiquer une procédure ATP. En cas d'absence de procédure, cette extension n'est tout simplement pas présente.
- L'extension de contexte `location` DOIT être présente et préciser le lieu de la séance.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/passed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/4f36a19c-91d7-3071-a946-e3bb2044746c",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/face-to-face",
            "name": {
                "en": "GRD-PC"
            },
            "description": {
                "en": "GRD-PC name"
            },
            "extensions": {
                "http://vocab.xapi.fr/extensions/remedial": false,
                "http://vocab.xapi.fr/extensions/assessment": true
            },
        }
    },
    "result": {
        "success": true,
        "completion": true,
        "extensions": {
            "https://polaris.enac.fr/xapi/vocab/extensions/abnormal-procedure": true
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/d539b903-cda9-34a2-8ed3-8307e7245b87",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/68083774-ef4e-3d53-95cb-6dc7e01a7092",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/9d1e38c9-9bc6-3df9-a059-193737111aa4",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/a7594730-3c60-3168-8df1-97ab586e24c5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "instructor": {
            "objectType": "Agent",
            "account": {
                "name": "b1f6a84b-de23-3e28-9f34-48344e2f20df",
                "homePage": "https://polaris.enac.fr"
            }
        },
        "platform": "POLARIS",
        "extensions": {
            "http://vocab.xapi.fr/extensions/location": {
                "id": "7ac18a93-1759-3b5e-b984-773b6d50a935",
                "name": "ENAC Biscarrosse"
            }
        }
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```


<a name="flight-sessions"></a>
## Sessions en simulateur ou vol avion

### Règles communes

- La propriété `object.definition.type` DOIT être présente et avoir pour valeur `http://vocab.xapi.fr/activities/flight` ou `http://adlnet.gov/expapi/activities/simulation`.
- L'extension d'activité `remedial` DOIT être précisée (`true` ou `false`).
- L'extension d'activité `duration` DEVRAIT être présente et définir la durée prévue de la séance (ISO 8601).
- L'extension d'activité `aircraft-type` DEVRAIT être présente et définir le type d'avion prévu (`type_tb10`, `type_tb20`, `type_da40`, `type_da42`, `type_pa28r_arrow`, `type_pa28_warrior`, `type_cap10`, `type_sf260`, `type_extra300`, `type_be58`, `type_be90`, `type_be200`, `type_a320`, `type_b737`).
- L'extension d'activité `aircraft-category` DEVRAIT être présente et définir la catégorie d'avion prévue (`cat_hpa`, `cat_sep`, `cat_sepc`, `cat_mepc`, `cat_fnpt1sep`, `cat_fnpt2sep`, `cat_fnpt2mep`, `cat_fnpt2mcc`, `cat_ffs`).
- L'extension d'activité `pilot-function` DEVRAIT être présente et définir le type d'équipage (`dual`, `spic`, `solo`, `pm`, `pf`).
- L'extension d'activité `flight-type` DEVRAIT être présente et définir le type de vol (`ifr`, `vfr`).
- L'extension d'activité `flight-conditions` DEVRAIT être présente et définir les conditions de vol (`day`, `night`).
- L'extension d'activité `flight-objective` DEVRAIT être présente et définir l'objectif pédagogique du vol (`maneuverability`, `navigation`, `if`, `uprt`).
- L'extension d'activité `flight-mcc` DOIT être présente et définir s'il s'agit d'un vol MCC ou non (`true` ou `false`).
- La propriété `result.completion` DOIT être présente et avoir pour valeur `true`.
- La propriété `result.duration` DOIT être présente et préciser la durée effective de la séance (ISO 8601).
- L'extension de résultat `tag-landing` DOIT être présente et indiquer le nombre de touch-and-go et atterrissages.
- L'extension de résultat `abnormal-procedure` PEUT être présente avec la valeur `true` pour indiquer une procédure ATP. En cas d'absence de procédure, cette extension n'est tout simplement pas présente.
- La propriété `context.instructor` DOIT être présente et préciser l'instructeur concerné. S'il s'agit d'un vol à 3, alors cette propriété prend la forme d'un groupe pour préciser les 2 instructeurs présents à bord.
- L'extension de contexte `aircraft-type` DOIT être présente et définir le type d'avion utilisé.
- L'extension de contexte `aircraft-category` DOIT être présente et définir la catégorie de l'avion utilisé.
- L'extension de contexte `location` DOIT être présente et préciser le lieu de la séance.


### EXP-FLT-C - L’apprenant a réalisé une session de simulateur ou vol avion.

- L'extension d'activité `assessment` DOIT être présente et avoir pour valeur `false`.
- La propriété `result.score` DOIT être présente et préciser la note obtenue en détaillant les propriétés `raw`, `min`, `max` et `scaled`.
- Ce Statement est généralement accompagné de Statements de type `EXP-CMP` précisant les compétences satisfaites ou non.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/54097802-3dc0-39b0-a700-33fe4c3490be",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/flight",
            "name": {
                "en": "FLT"
            },
            "description": {
                "en": "FLT name"
            },
            "extensions": {
                "http://vocab.xapi.fr/extensions/remedial": false,
                "http://vocab.xapi.fr/extensions/assessment": false,
                "http://vocab.xapi.fr/extensions/duration": "PT1H",
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-mcc": true,
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-type": "ifr",
                "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-type": "type_tb10",
                "https://polaris.enac.fr/xapi/vocab/extensions/pilot-function": "dual",
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-objective": "maneuverability",
                "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-category": "cat_hpa",
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-conditions": "day"
            }
        }
    },
    "result": {
        "completion": true,
        "duration": "PT1H",
        "score": {
            "max": 5,
            "min": 1,
            "raw": 3,
            "scaled": 0.5
        },
        "extensions": {
            "https://polaris.enac.fr/xapi/vocab/extensions/tag-landing": 3,
            "https://polaris.enac.fr/xapi/vocab/extensions/abnormal-procedure": true
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/d539b903-cda9-34a2-8ed3-8307e7245b87",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/68083774-ef4e-3d53-95cb-6dc7e01a7092",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/9d1e38c9-9bc6-3df9-a059-193737111aa4",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/a7594730-3c60-3168-8df1-97ab586e24c5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "instructor": {
            "objectType": "Group",
            "member": [
                {
                    "objectType": "Agent",
                    "account": {
                        "name": "e1002439-9407-3cf3-b8c3-0828c9c14435",
                        "homePage": "https://polaris.enac.fr"
                    }
                },
                {
                    "objectType": "Agent",
                    "account": {
                        "name": "347dcf08-3883-38f9-9903-71025fce7153",
                        "homePage": "https://polaris.enac.fr"
                    }
                }
            ]
        },
        "platform": "POLARIS",
        "extensions": {
            "http://vocab.xapi.fr/extensions/location": {
                "id": "7ac18a93-1759-3b5e-b984-773b6d50a935",
                "name": "ENAC Biscarrosse"
            },
            "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-type": "type_tb10",
            "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-category": "cat_hpa"
        }
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```


### EXP-FLT-S - L’apprenant a réussi/raté une évaluation en simulateur ou vol avion.

- La propriété `verb.id` DOIT avoir la valeur `http://adlnet.gov/expapi/verbs/passed` ou `http://adlnet.gov/expapi/verbs/failed`.
- L'extension d'activité `assessment` DOIT être présente et avoir pour valeur `true`.
- La propriété `result.success` DOIT être précisée (`true` ou `false`).
- Ce Statement est généralement accompagné de Statements de type `EXP-CMP` précisant les compétences satisfaites ou non.
- Ce Statement est toujours accompagné de Statements de type `EXP-ASS` précisant les capacités évaluées.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/passed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/54097802-3dc0-39b0-a700-33fe4c3490be",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/flight",
            "name": {
                "en": "FLT-PC"
            },
            "description": {
                "en": "FLT-PC name"
            },
            "extensions": {
                "http://vocab.xapi.fr/extensions/remedial": false,
                "http://vocab.xapi.fr/extensions/assessment": false,
                "http://vocab.xapi.fr/extensions/duration": "PT1H",
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-mcc": true,
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-type": "ifr",
                "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-type": "type_tb10",
                "https://polaris.enac.fr/xapi/vocab/extensions/pilot-function": "dual",
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-objective": "maneuverability",
                "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-category": "cat_hpa",
                "https://polaris.enac.fr/xapi/vocab/extensions/flight-conditions": "day"
            }
        }
    },
    "result": {
        "completion": true,
        "success": true,
        "duration": "PT1H",
        "extensions": {
            "https://polaris.enac.fr/xapi/vocab/extensions/tag-landing": 3,
            "https://polaris.enac.fr/xapi/vocab/extensions/abnormal-procedure": true
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/d539b903-cda9-34a2-8ed3-8307e7245b87",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/68083774-ef4e-3d53-95cb-6dc7e01a7092",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/9d1e38c9-9bc6-3df9-a059-193737111aa4",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/a7594730-3c60-3168-8df1-97ab586e24c5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "instructor": {
            "objectType": "Group",
            "member": [
                {
                    "objectType": "Agent",
                    "account": {
                        "name": "e1002439-9407-3cf3-b8c3-0828c9c14435",
                        "homePage": "https://polaris.enac.fr"
                    }
                },
                {
                    "objectType": "Agent",
                    "account": {
                        "name": "347dcf08-3883-38f9-9903-71025fce7153",
                        "homePage": "https://polaris.enac.fr"
                    }
                }
            ]
        },
        "platform": "POLARIS",
        "extensions": {
            "http://vocab.xapi.fr/extensions/location": {
                "id": "7ac18a93-1759-3b5e-b984-773b6d50a935",
                "name": "ENAC Biscarrosse"
            },
            "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-type": "type_tb10",
            "https://polaris.enac.fr/xapi/vocab/extensions/aircraft-category": "cat_hpa"
        }
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```


<a name="level-report"></a>
## Level Report

### EXP-LR - L’apprenant a réussi/raté un Level Report.

- La propriété `verb.id` DOIT avoir la valeur `http://adlnet.gov/expapi/verbs/passed` ou `http://adlnet.gov/expapi/verbs/failed`.
- L'extension d'activité `remedial` DOIT être précisée (`true` ou `false`).
- La propriété `result.completion` DOIT être présente et avoir pour valeur `true`.
- La propriété `result.success` DOIT être précisée (`true` ou `false`).
- L'extension de résultat `abnormal-procedure` PEUT être présente avec pour valeur `true` afin d'indiquer une procédure ATP. En cas d'absence de procédure, cette extension n'est tout simplement pas présente.
- L'extension de contexte `location` DOIT être présente et préciser le lieu de la séance.
- Ce Statement est généralement accompagné de Statements de type `EXP-CMP` précisant les compétences satisfaites ou non.
- Ce Statement est toujours accompagné de Statements de type `EXP-ASS` précisant les capacités évaluées.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/passed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/54097802-3dc0-39b0-a700-33fe4c3490be",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/level-report",
            "name": {
                "en": "LR"
            },
            "description": {
                "en": "LR name"
            },
            "extensions": {
                "http://vocab.xapi.fr/extensions/remedial": false
            }
        }
    },
    "result": {
        "completion": true,
        "success": true,
        "extensions": {
            "https://polaris.enac.fr/xapi/vocab/extensions/abnormal-procedure": true
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/d539b903-cda9-34a2-8ed3-8307e7245b87",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/68083774-ef4e-3d53-95cb-6dc7e01a7092",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/9d1e38c9-9bc6-3df9-a059-193737111aa4",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/a7594730-3c60-3168-8df1-97ab586e24c5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "instructor": {
            "objectType": "Agent",
            "account": {
                "name": "e1002439-9407-3cf3-b8c3-0828c9c14435",
                "homePage": "https://polaris.enac.fr"
            }
        },
        "platform": "POLARIS",
        "extensions": {
            "http://vocab.xapi.fr/extensions/location": {
                "id": "7ac18a93-1759-3b5e-b984-773b6d50a935",
                "name": "ENAC Biscarrosse"
            }
        }
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```

<a name="skills-test"></a>
## Skills Test

### EXP-SKL - L’apprenant a réussi/raté un Skills Test.

- L'extension d'activité `remedial` DOIT être précisée (`true` ou `false`).
- La propriété `result.completion` DOIT être présente et avoir pour valeur `true`.
- L'extension de résultat `abnormal-procedure` PEUT être présente avec pour valeur `true` afin d'indiquer une procédure ATP. En cas d'absence de procédure, cette extension n'est tout simplement pas présente.
- Ce Statement est toujours accompagné de Statements de type `EXP-SKL-ATT` précisant les tentatives associées.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/54097802-3dc0-39b0-a700-33fe4c3490be",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/skills-test",
            "name": {
                "en": "SKL"
            },
            "description": {
                "en": "SKL name"
            },
            "extensions": {
                "http://vocab.xapi.fr/extensions/remedial": false
            }
        }
    },
    "result": {
        "completion": true,
        "extensions": {
            "https://polaris.enac.fr/xapi/vocab/extensions/abnormal-procedure": true
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/d539b903-cda9-34a2-8ed3-8307e7245b87",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/68083774-ef4e-3d53-95cb-6dc7e01a7092",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/9d1e38c9-9bc6-3df9-a059-193737111aa4",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/a7594730-3c60-3168-8df1-97ab586e24c5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "instructor": {
            "objectType": "Agent",
            "account": {
                "name": "e1002439-9407-3cf3-b8c3-0828c9c14435",
                "homePage": "https://polaris.enac.fr"
            }
        },
        "platform": "POLARIS"
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```

### EXP-SKL-ATT - L’apprenant a réussi/partiellement réussi/raté une tentative de Skills Test.

- La propriété `verb.id` DOIT avoir la valeur `http://adlnet.gov/expapi/verbs/passed`, `http://vocab.xapi.fr/verbs/partially-passed` ou `http://adlnet.gov/expapi/verbs/failed`.
- La propriété `result.completion` DOIT être présente et avoir pour valeur `true`.
- La propriété `result.success` DOIT être présente si la tentative est réussie ou ratée, et avoir pour valeur `true` ou `false`. Elle n'est pas présente lorsque la tentative est partiellement réussie.
- La propriété `result.duration` DOIT être présente et préciser la durée effective de la séance (ISO 8601).
- L'extension de résultat `abnormal-procedure` PEUT être présente avec pour valeur `true` afin d'indiquer une procédure ATP. En cas d'absence de procédure, cette extension n'est tout simplement pas présente.
- L'extension de contexte `location` DOIT être présente et préciser le lieu de la séance.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://vocab.xapi.fr/verbs/partially-passed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/training-items/b9ebf313-a35e-3fcc-9279-0e9e64b4d6e7/attempts/1",
        "definition": {
            "type": "http://adlnet.gov/expapi/activities/attempt"
        }
    },
    "result": {
        "completion": true,
        "duration": "PT1H",
        "extensions": {
            "https://polaris.enac.fr/xapi/vocab/extensions/abnormal-procedure": true
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-items/b9ebf313-a35e-3fcc-9279-0e9e64b4d6e7",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/skills-test"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/506bfb88-ac60-3b8e-b2bb-ba2a094eeda3",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/ee24d8b1-c6f8-3b78-9b78-1a86e832d74f",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/4efc48e2-9392-379d-aa68-5da132a0f81b",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/b89483c5-145c-3b87-a1c5-7075bde6edc5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/inside-learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "platform": "POLARIS",
        "extensions": {
            "http://vocab.xapi.fr/extensions/location": {
                "id": "7ac18a93-1759-3b5e-b984-773b6d50a935",
                "name": "ENAC Biscarrosse"
            }
        }
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```


<a name="competencies"></a>
## Compétences

### EXP-CMP - L’apprenant a satisfait/partiellement satisfait/non satisfait une compétence.

- La propriété `verb.id` DOIT avoir la valeur `https://w3id.org/xapi/adl/verbs/satisfied`, `http://vocab.xapi.fr/verbs/partially-satisfied` ou `http://vocab.xapi.fr/verbs/dissatisfied`.
- La propriété `result.success` DOIT être présente si la compétences est satisfaite ou non satisfaite, et avoir pour valeur `true` ou `false`. Elle n'est pas présente lorsque la compétence est partiellement satisfaite.
- L'extension de résultat `satisfactory-indicators` liste des indicateurs de compétences considérés comme satisfaits (IRIs).
- L'extension de résultat `unsatisfactory-indicators` liste des indicateurs de compétences considérés comme non satisfaits (IRIs).

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "https://w3id.org/xapi/adl/verbs/satisfied"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/competency-domains/general-criteria/tem",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/competency-domain"
        }
    },
    "result": {
        "success": true,
        "extensions": {
            "http://vocab.xapi.fr/extensions/satisfactory-indicators": [
                "https://polaris.enac.fr/xapi/activities/competency-items/1c435563-b52e-35e2-99fb-32d878c02193"
            ],
            "http://vocab.xapi.fr/extensions/unsatisfactory-indicators": [
                "https://polaris.enac.fr/xapi/activities/competency-items/8bab7325-0a08-3206-86e1-1110cfbdcd45",
                "https://polaris.enac.fr/xapi/activities/competency-items/ff8b7f3b-b46d-3c0c-aca0-763ef58fc6e0"
            ]
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-items/b9ebf313-a35e-3fcc-9279-0e9e64b4d6e7",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/flight"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/506bfb88-ac60-3b8e-b2bb-ba2a094eeda3",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/ee24d8b1-c6f8-3b78-9b78-1a86e832d74f",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/4efc48e2-9392-379d-aa68-5da132a0f81b",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/b89483c5-145c-3b87-a1c5-7075bde6edc5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/inside-learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "platform": "POLARIS"
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```


### EXP-ASS - L’apprenant a été évalué sur une compétence.

- La propriété `result.success` DOIT être présente si la compétences est satisfaite ou non satisfaite, et avoir pour valeur `true` ou `false`. Elle n'est pas présente lorsque la tentative est partiellement satisfaite.
- La propriété `result.score` DOIT être présente et préciser le total des points obtenus pour la compétence (`raw`), ainsi que les valeurs `min`, `max` et `scaled`.
- L'extension de résultat `assessment-items` liste les points évalués en précisant pour chacun d'eux leur IRI et la note obtenue.

``` json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "416cc887-dc97-3496-98b7-b800342107d3",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://vocab.xapi.fr/verbs/was-assessed"
    },
    "object": {
        "objectType": "Activity",
        "id": "https://polaris.enac.fr/xapi/activities/competency-domains/behavioural-indicator/flight-preparation",
        "definition": {
            "type": "http://vocab.xapi.fr/activities/competency-domain"
        }
    },
    "result": {
        "score": {
                "max": 10,
                "min": 2,
                "raw": 3,
                "scaled": 0.13
        },
        "extensions": {
            "http://vocab.xapi.fr/extensions/assessment-items": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/assessment-items/69a29369-0946-3777-94d1-8db8762f4da0",
                    "value": 1
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/assessment-items/ef73fc17-db93-3a96-b10f-34ebea6cc140",
                    "value": 2
                }
            ]
        }
    },
    "context": {
        "contextActivities": {
            "parent": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-items/b9ebf313-a35e-3fcc-9279-0e9e64b4d6e7",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/flight"
                    }
                }
            ],
            "grouping": [
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-modules/506bfb88-ac60-3b8e-b2bb-ba2a094eeda3",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-module"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-phases/ee24d8b1-c6f8-3b78-9b78-1a86e832d74f",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-phase"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/training-programs/4efc48e2-9392-379d-aa68-5da132a0f81b",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/training-program"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/activities/registrations/b89483c5-145c-3b87-a1c5-7075bde6edc5",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/registration"
                    }
                }
            ],
            "category": [
                {
                    "id": "http://vocab.xapi.fr/categories/inside-learning-unit",
                    "definition": {
                        "type": "http://vocab.xapi.fr/activities/granularity-level"
                    }
                },
                {
                    "id": "https://polaris.enac.fr/xapi/vocab/categories/profile",
                    "definition": {
                        "type": "http://adlnet.gov/expapi/activities/profile"
                    }
                }
            ]
        },
        "platform": "POLARIS"
    },
    "timestamp": "2019-03-25T00:00:00+00:00"
}
```

<a name="voiding"></a>
## Annulation

L'annulation de Statements peut se produire, notamment lorsqu'une fiche de suivi est débloquée (signature annulée). Dans ce cas, tous les Statements concernés par la fiche, au niveau de granularité principal et aux niveaux inférieurs, sont annulés.

```json
{
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "e1002439-9407-3cf3-b8c3-0828c9c14435",
            "homePage": "https://polaris.enac.fr"
        }
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/voided"
    },
    "object": {
        "objectType": "StatementRef",
        "id": "e08b435b-846b-3f03-a95f-d5792b0176ef"
    },
    "timestamp": "2019-03-26T11:32:20+00:00"
}
```



