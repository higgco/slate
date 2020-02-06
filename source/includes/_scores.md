# Scores


You may include the 'scores' key in the include array. When this is requested, the 'scores' key will be populated in the results. 

The format of this result contains data for overall score, section level scores, and per question scores. 

If no verified data is available, the verified  score will not be populated.

Format:

```json
"scores": {
        "self": {
            "site": {
                "scores": {},
                "levels": {
                    "1": 0,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": null,
                "total": 0
            },
            "water": {
                "scores": {
                    "watsources": {
                        "score": 25,
                        "level": 1
                    },
                    "watbaselineopt": {
                        "score": 10,
                        "level": 2
                    },
                    "wathighestuse": {
                        "score": 10,
                        "level": 2
                    },
                    "wattargetopt": {
                        "score": 10,
                        "level": 2
                    },
                    "watimproveplan": {
                        "score": 10,
                        "level": 2
                    },
                    "watimproveopt": {
                        "score": 10,
                        "level": 2
                    },
                    "watbalanceanalysis": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25,
                    "2": 50,
                    "3": 0
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1,
                    2
                ],
                "applicability": "AppWater001",
                "total": 75
            },
            "energy": {
                "scores": {
                    "ensourcetrackopt": {
                        "score": 25,
                        "level": 1
                    },
                    "enbaselinesource": {
                        "score": 10,
                        "level": 2
                    },
                    "enhighestuse": {
                        "score": 10,
                        "level": 2
                    },
                    "entargetssource": {
                        "score": 5,
                        "level": 2
                    },
                    "enimproveplan": {
                        "score": 10,
                        "level": 2
                    },
                    "enimprovesource": {
                        "score": 5,
                        "level": 2
                    },
                    "enscope3ghg": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25,
                    "2": 40,
                    "3": null
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1,
                    2
                ],
                "applicability": null,
                "total": 65
            },
            "waste": {
                "scores": {
                    "wstsourcenh": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstsourceh": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstsegregatestreams": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wsthstorage": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstnhstorage": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstpolhtml": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wsthtrain": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstbaseline": {
                        "score": 7.142857142857143,
                        "level": 2
                    },
                    "wstbaselinedisp": {
                        "score": 7.142857142857143,
                        "level": 2
                    },
                    "wsttarget": {
                        "score": 7.142857142857143,
                        "level": 2
                    },
                    "wsttargetdisp": {
                        "score": 7.142857142857143,
                        "level": 2
                    },
                    "wstredimpplan": {
                        "score": 7.142857142857143,
                        "level": 2
                    },
                    "wstredimp2018": {
                        "score": 0,
                        "level": 2
                    },
                    "wstredimpdisp": {
                        "score": 7.142857142857143,
                        "level": 2
                    },
                    "wsthazdispvalidate": {
                        "score": 8.333333333333334,
                        "level": 3
                    },
                    "wstdispzerowaste": {
                        "score": 0,
                        "level": 3
                    },
                    "wstdispupcycle": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25.000000000000004,
                    "2": 42.85714285714286,
                    "3": 8.333333333333334
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1
                ],
                "applicability": null,
                "total": 76.1904761904762
            },
            "wastewater": {
                "scores": {
                    "wwtrack": {
                        "score": 8.333333333333334,
                        "level": 1
                    },
                    "wwoffsitetreatplant": {
                        "score": 8.333333333333334,
                        "level": 1
                    },
                    "wwemergplan": {
                        "score": 8.333333333333334,
                        "level": 1
                    },
                    "wwstandard": {
                        "score": 25,
                        "level": 2
                    },
                    "wwqualitytest": {
                        "score": 25,
                        "level": 2
                    },
                    "wwrecycle": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25,
                    "2": 50,
                    "3": 0
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1,
                    2
                ],
                "applicability": "AppWW002",
                "total": 75
            },
            "chemicals": {
                "scores": {
                    "chemtrack": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemsds": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemtraining": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chememergplan": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemsafetyequip": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemhazardsign": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chempurchasereq": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemhealthprogram": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemstorage": {
                        "score": 0.96,
                        "level": 1
                    },
                    "chemtrainingRSL": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemprocessidentifyRSL": {
                        "score": 0,
                        "level": 1
                    },
                    "chemprocessmonitorRSL": {
                        "score": 0,
                        "level": 1
                    },
                    "chemtraceinventory": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemimproveplan": {
                        "score": 0,
                        "level": 2
                    },
                    "chemreduceplan": {
                        "score": 0,
                        "level": 2
                    },
                    "chemsourcelist": {
                        "score": 0,
                        "level": 2
                    },
                    "chemcollabalternatives": {
                        "score": 0,
                        "level": 3
                    },
                    "chemtracelotnumber": {
                        "score": 0,
                        "level": 3
                    },
                    "chemanalysishumanenv": {
                        "score": 0,
                        "level": 3
                    },
                    "chemanalysislifecycle": {
                        "score": 0,
                        "level": 3
                    },
                    "chemdocumentedqa": {
                        "score": 0,
                        "level": 3
                    },
                    "chemcontractorsRSL": {
                        "score": 0,
                        "level": 3
                    },
                    "chemdocumentedgoals": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 20.160000000000004,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": "AppChem001",
                "total": 20.160000000000004
            },
            "airemissions": {
                "scores": {
                    "airsourceopstrack": {
                        "score": 5,
                        "level": 1
                    },
                    "airsourceprodtrack": {
                        "score": 5,
                        "level": 1
                    },
                    "airsourcerefrignew": {
                        "score": 5,
                        "level": 1
                    },
                    "aircontroldevopshtml": {
                        "score": 5,
                        "level": 1
                    },
                    "aircontroldevprodhtml": {
                        "score": 5,
                        "level": 1
                    },
                    "airbeyondpermit": {
                        "score": 0,
                        "level": 2
                    },
                    "airimplementprocess": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25,
                    "2": 0,
                    "3": 0
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1
                ],
                "applicability": "AppAir005",
                "total": 25
            },
            "ems": {
                "scores": {
                    "emsmgmt": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsstrategy": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsopsimpact": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emspermitstatus": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsregulationsystem": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsequipmaintain": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsstrategyreview": {
                        "score": 25,
                        "level": 2
                    },
                    "emsmgmtcompetence": {
                        "score": 25,
                        "level": 2
                    },
                    "emsstrategyawareness": {
                        "score": 6.25,
                        "level": 3
                    },
                    "emshiggindexsubcontract": {
                        "score": 6.25,
                        "level": 3
                    },
                    "emsengagelocal": {
                        "score": 6.25,
                        "level": 3
                    },
                    "emshiggindexupstream": {
                        "score": 6.25,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25.000000000000004,
                    "2": 50,
                    "3": 25
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1,
                    2,
                    3
                ],
                "applicability": "AppEMS001",
                "total": 100
            },
            "finalScore": 62.335782312925176,
            "averageLevelAchieved": 0.42857142857142855,
            "sipvalidoperatinglicense": true
        },
        "verified": {
            "site": {
                "scores": {},
                "levels": {
                    "1": 0,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": null,
                "total": 0
            },
            "water": {
                "scores": {
                    "watsources": {
                        "score": 12.5,
                        "level": 1
                    },
                    "watbaselineopt": {
                        "score": 0,
                        "level": 2
                    },
                    "wathighestuse": {
                        "score": 0,
                        "level": 2
                    },
                    "wattargetopt": {
                        "score": 10,
                        "level": 2
                    },
                    "watimproveplan": {
                        "score": 0,
                        "level": 2
                    },
                    "watimproveopt": {
                        "score": 0,
                        "level": 2
                    },
                    "watbalanceanalysis": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 12.5,
                    "2": 10,
                    "3": 0
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1
                ],
                "applicability": "AppWater001",
                "total": 22.5
            },
            "energy": {
                "scores": {
                    "ensourcetrackopt": {
                        "score": 25,
                        "level": 1
                    },
                    "enbaselinesource": {
                        "score": 10,
                        "level": 2
                    },
                    "enhighestuse": {
                        "score": 0,
                        "level": 2
                    },
                    "entargetssource": {
                        "score": 5,
                        "level": 2
                    },
                    "enimproveplan": {
                        "score": 0,
                        "level": 2
                    },
                    "enimprovesource": {
                        "score": 5,
                        "level": 2
                    },
                    "enscope3ghg": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 25,
                    "2": 20,
                    "3": null
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    1
                ],
                "applicability": null,
                "total": 45
            },
            "waste": {
                "scores": {
                    "wstsourcenh": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstsourceh": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstsegregatestreams": {
                        "score": 0,
                        "level": 1
                    },
                    "wsthstorage": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstnhstorage": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstpolhtml": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wsthtrain": {
                        "score": 3.5714285714285716,
                        "level": 1
                    },
                    "wstbaseline": {
                        "score": 0,
                        "level": 2
                    },
                    "wstbaselinedisp": {
                        "score": 0,
                        "level": 2
                    },
                    "wsttarget": {
                        "score": 0,
                        "level": 2
                    },
                    "wsttargetdisp": {
                        "score": 0,
                        "level": 2
                    },
                    "wstredimpplan": {
                        "score": 0,
                        "level": 2
                    },
                    "wstredimp2018": {
                        "score": 0,
                        "level": 2
                    },
                    "wstredimpdisp": {
                        "score": 0,
                        "level": 2
                    },
                    "wsthazdispvalidate": {
                        "score": 0,
                        "level": 3
                    },
                    "wstdispzerowaste": {
                        "score": 0,
                        "level": 3
                    },
                    "wstdispupcycle": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 21.42857142857143,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": null,
                "total": 21.42857142857143
            },
            "wastewater": {
                "scores": {
                    "wwtrack": {
                        "score": 0,
                        "level": 1
                    },
                    "wwoffsitetreatplant": {
                        "score": 8.333333333333334,
                        "level": 1
                    },
                    "wwemergplan": {
                        "score": 0,
                        "level": 1
                    },
                    "wwstandard": {
                        "score": 25,
                        "level": 2
                    },
                    "wwqualitytest": {
                        "score": 25,
                        "level": 2
                    },
                    "wwrecycle": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 8.333333333333334,
                    "2": 50,
                    "3": 0
                },
                "levelsOpen": [
                    1,
                    2,
                    3
                ],
                "levelsAchieved": [
                    2
                ],
                "applicability": "AppWW002",
                "total": 58.333333333333336
            },
            "chemicals": {
                "scores": {
                    "chemtrack": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemsds": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemtraining": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chememergplan": {
                        "score": 0.96,
                        "level": 1
                    },
                    "chemsafetyequip": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemhazardsign": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chempurchasereq": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemhealthprogram": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemstorage": {
                        "score": 0.96,
                        "level": 1
                    },
                    "chemtrainingRSL": {
                        "score": 0.96,
                        "level": 1
                    },
                    "chemprocessidentifyRSL": {
                        "score": 0,
                        "level": 1
                    },
                    "chemprocessmonitorRSL": {
                        "score": 0,
                        "level": 1
                    },
                    "chemtraceinventory": {
                        "score": 1.92,
                        "level": 1
                    },
                    "chemimproveplan": {
                        "score": 0,
                        "level": 2
                    },
                    "chemreduceplan": {
                        "score": 0,
                        "level": 2
                    },
                    "chemsourcelist": {
                        "score": 0,
                        "level": 2
                    },
                    "chemcollabalternatives": {
                        "score": 0,
                        "level": 3
                    },
                    "chemtracelotnumber": {
                        "score": 0,
                        "level": 3
                    },
                    "chemanalysishumanenv": {
                        "score": 0,
                        "level": 3
                    },
                    "chemanalysislifecycle": {
                        "score": 0,
                        "level": 3
                    },
                    "chemdocumentedqa": {
                        "score": 0,
                        "level": 3
                    },
                    "chemcontractorsRSL": {
                        "score": 0,
                        "level": 3
                    },
                    "chemdocumentedgoals": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 18.240000000000002,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": "AppChem001",
                "total": 18.240000000000002
            },
            "airemissions": {
                "scores": {
                    "airsourceopstrack": {
                        "score": 5,
                        "level": 1
                    },
                    "airsourceprodtrack": {
                        "score": 0,
                        "level": 1
                    },
                    "airsourcerefrignew": {
                        "score": 2.5,
                        "level": 1
                    },
                    "aircontroldevopshtml": {
                        "score": 5,
                        "level": 1
                    },
                    "aircontroldevprodhtml": {
                        "score": 0,
                        "level": 1
                    },
                    "airbeyondpermit": {
                        "score": 0,
                        "level": 2
                    },
                    "airimplementprocess": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 12.5,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": "AppAir005",
                "total": 12.5
            },
            "ems": {
                "scores": {
                    "emsmgmt": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsstrategy": {
                        "score": 0,
                        "level": 1
                    },
                    "emsopsimpact": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emspermitstatus": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsregulationsystem": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsequipmaintain": {
                        "score": 4.166666666666667,
                        "level": 1
                    },
                    "emsstrategyreview": {
                        "score": 0,
                        "level": 2
                    },
                    "emsmgmtcompetence": {
                        "score": 0,
                        "level": 2
                    },
                    "emsstrategyawareness": {
                        "score": 0,
                        "level": 3
                    },
                    "emshiggindexsubcontract": {
                        "score": 0,
                        "level": 3
                    },
                    "emsengagelocal": {
                        "score": 0,
                        "level": 3
                    },
                    "emshiggindexupstream": {
                        "score": 0,
                        "level": 3
                    }
                },
                "levels": {
                    "1": 20.833333333333336,
                    "2": null,
                    "3": null
                },
                "levelsOpen": [
                    1
                ],
                "levelsAchieved": [],
                "applicability": "AppEMS001",
                "total": 20.833333333333336
            },
            "finalScore": 28.405034013605444,
            "averageLevelAchieved": 0,
            "sipvalidoperatinglicense": true
        }
    }
```