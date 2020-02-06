# GHG


You may include the 'ghg' key in the include array. When this is requested, the 'ghg' key will be populated in the results. 

The format of this result contains data for all emissions sources and is converted to standard units  (liter, kg and MJ) (see How To Higg for more data on this). 

If no verified data is available, the verified  score will not be populated.

Format:

```json
"ghg": {
                "self": {
                    "ghg": 2527641.2991990526,
                    "ghgSources": [
                        {
                            "name": "electricpurch",
                            "ghg": 1780349.1121944
                        },
                        {
                            "name": "diesel",
                            "ghg": 120239.03088
                        },
                        {
                            "name": "natgaslpg",
                            "ghg": 50132.329166955555
                        },
                        {
                            "name": "biomassother",
                            "ghg": 576920.826957697
                        },
                        {
                            "name": "biomasssliverwood",
                            "ghg": 0
                        }
                    ],
                    "sipfacilityannualprodvolquant": 8280786,
                    "sitecountry": 243,
                    "sitecountrytext": "Vietnam"
                },
                "verified": {
                    "ghg": 2527641.2991990526,
                    "ghgSources": [
                        {
                            "name": "electricpurch",
                            "ghg": 1780349.1121944
                        },
                        {
                            "name": "diesel",
                            "ghg": 120239.03088
                        },
                        {
                            "name": "natgaslpg",
                            "ghg": 50132.329166955555
                        },
                        {
                            "name": "biomassother",
                            "ghg": 576920.826957697
                        },
                        {
                            "name": "biomasssliverwood",
                            "ghg": 0
                        },
                        {
                            "name": 251,
                            "ghg": 0
                        }
                    ],
                    "sipfacilityannualprodvolquant": 8280786,
                    "sitecountry": 243,
                    "sitecountrytext": "Vietnam"
                }
            }
```