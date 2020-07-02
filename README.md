# pds-cdm-specs
Use these specs when constructing a plugin API for the PDS Framework.

# examples
Check out the live documentation at http://pds.renci.org for examples, which are recapitulated below. Below can be used for pasting specs into new API definitions.


## Guidance
Example JSON (used in code):
```
{
  "piid": "pdspi-aminoglycoside-nomogram",
  "title": "Aminoglycoside dosing guidance",
  "txid": "38-1",
  "ptid": "smart-7321938",
  "inputs": {
    "pluginSelectors": [
      {
        "id": "dosing.rxCUI",
        "title": "Drug",
        "legalValues": {
          "type": "string",
          "enum": [
            {
              "value": "rxCUI:1596450",
              "title": "Gentamicin"
            },
            {
              "value": "rxCUI:1723160",
              "title": "Amikacin"
            }
          ]
        },
        "selectorValue": {
          "value": "rxCUI:1596450",
          "title": "Amikacin"
        }
      }
    ],
    "modelParameters": [
      {
        "id": "pdspi-guidance-example:1",
        "title": "Extended interval nomogram",
        "parameterDescription": "This calculator uses one of four extended-interval nomograms. Please choose one nomogram.",
        "legalValues": {
          "type": "string",
          "enum": [
            "Hartford",
            "Urban-Craig",
            "Conventional A",
            "Conventional B"
          ]
        },
        "parameterValue": {
          "value": "Hartford"
        }
      }
    ],
    "patientVariables": [
      {
        "id": "LOINC:30525-0",
        "certitude": 1,
        "how": "The value was specified by the end user.",
        "title": "Age",
        "variableValue": {
          "value": ".5",
          "units": "years"
        },
        "why": "Age is used to calculate the creatinine clearance. Dosing is lower for geriatric patient and contraindicated for pediatric patients",
        "legalValues": {
          "type": "number",
          "minimum": "0"
        }
      }
    ],
    "timestamp": "2019-12-03T13:41:09.942+00:00"
  },
  "return": {
    "pluginSelectors": [
      {
        "id": "dosing.rxCUI",
        "title": "Drug",
        "legalValues": {
          "type": "string",
          "enum": [
            {
              "value": "rxCUI:1596450",
              "title": "Gentamicin"
            },
            {
              "value": "rxCUI:1723160",
              "title": "Amikacin"
            }
          ]
        },
        "selectorValue": {
          "value": "rxCUI:1596450",
          "title": "Amikacin"
        }
      }
    ],
    "modelParameters": [
      {
        "id": "pdspi-guidance-example:1",
        "title": "Extended interval nomogram",
        "parameterDescription": "This calculator uses one of four extended-interval nomograms. Please choose one nomogram.",
        "legalValues": {
          "type": "string",
          "enum": [
            "Hartford",
            "Urban-Craig",
            "Conventional A",
            "Conventional B"
          ]
        },
        "parameterValue": {
          "value": "Hartford"
        }
      }
    ],
    "patientVariables": [
      {
        "id": "LOINC:30525-0",
        "certitude": 1,
        "how": "The value was specified by the end user.",
        "title": "Age",
        "variableValue": {
          "value": ".5",
          "units": "years"
        },
        "why": "Age is used to calculate the creatinine clearance. Dosing is lower for geriatric patient and contraindicated for pediatric patients",
        "legalValues": {
          "type": "number",
          "minimum": "0"
        }
      }
    ],
    "timestamp": "2019-12-03T13:41:09.942+00:00"
  },
  "cards": [
    {
      "id": "string",
      "title": "string",
      "summary": "some <140 char Summary Message",
      "detail": "some sort of optional GitHub Markdown details",
      "indicator": "info",
      "source": {
        "label": "Human-readable source label",
        "url": "https://example.com",
        "icon": "https://example.com/img/icon-100px.png"
      },
      "suggestions": [
        {
          "uuid": "e1187895-ad57-4ff7-a1f1-ccf954b2fe46",
          "label": "Human-readable suggestion label",
          "actions": [
            {
              "type": "create",
              "description": "Create a prescription for Acetaminophen 250 MG",
              "resource": "MedicationRequest"
            }
          ]
        }
      ],
      "selectionBehavior": "string",
      "links": [
        {
          "label": "SMART Example App",
          "url": "string",
          "type": "string",
          "appContext": "string"
        }
      ]
    }
  ],
  "specs": [
    {
      "$schema": "https://vega.github.io/schema/vega-lite/v4.json",
      "title": "Line chart",
      "description": "Time-series line chart",
      "width": "container",
      "height": "container",
      "autosize": {
        "resize": true
      },
      "data": {
        "name": "data"
      },
      "mark": "line",
      "encoding": {
        "x": {
          "bin": true,
          "field": "x",
          "type": "quantitative",
          "axis": {
            "title": "x axis"
          }
        },
        "y": {
          "aggregate": "count",
          "field": "y",
          "type": "quantitative",
          "axis": {
            "title": "y axis"
          }
        },
        "color": {
          "field": "group",
          "type": "nominal"
        }
      }
    }
  ],
  "timeout": 0,
  "fhir_piid": "pdspi-fhir-example",
  "mapper_piid": "pdspi-mapper-example"
}
```

## Config
The Config is comprised of an array. A manual example is required to show more than one element in the array. The Yaml for the example below includes an array of configs, one each for FHIR, Mapper, and Guidance types. These can be pasted into the API end points as examples for each plugin's config.

Example Yaml: (used in specs)
```
                example:
                  - piid: pdspi-fhir-example
                    title: Example plugin for fhir smart-fhir server
                    pluginType: f
                    settingsDefaults:
                      pluginSelectors:
                        - id: 'FHIR.URI'
                          title: FHIR Server URL
                          legalValues:
                            type: string
                            enum:
                              - value: 'urn://cdwh.nctracs.v1'
                                title: NCTraCS Carolina Data Warehouse
                              - value: 'http://hapi.fhir.org/baseR4'
                              - value: 'https://open-ic.epic.com/FHIR/api/FHIR/DSTU2'
                          selectorValue:
                            value: 'http://hapi.fhir.org/baseR4'
                            title: Hapi FHIR base URL
                      modelParameters:
                      patientVariables:
                  - piid: pdspi-mapper-example
                    title: Example plugin for mapping the smart-fhir server
                    pluginDependencies:
                      - pdsph-fhir-example
                    pluginType: mD
                    settingsDefaults:
                      pluginSelectors:
                      modelParameters:
                      patientVariables:
                        - id: 'LOINC:30525-0'
                          how: 
                          title: Age
                          legalValues:
                            type: number
                            minimum: '0'
                  - piid: pdspi-guidance-example
                    title: Example plugin for Amikacin dosing guidance
                    pluginDependencies:
                      - string
                    pluginType: g
                    pluginTypeTitle: guidance
                    settingsDefaults:
                      pluginSelectors:
                        - id: dosing.rxCUI
                          title: Drug
                          legalValues:
                            type: string
                            enum:
                              - value: 'rxCUI:1596450'
                                title: Gentamicin
                              - value: 'rxCUI:1723160'
                                title: Amikacin
                          selectorValue:
                            value: 'rxCUI:1596450'
                            title: Amikacin
                      modelParameters:
                        - id: 'pdspi-guidance-example:1'
                          title: Extended interval nomogram
                          parameterDescription: This calculator uses one of four extended-interval nomograms. Please choose one nomogram.
                          legalValues:
                            type: string
                            enum:
                              - Hartford
                              - Urban-Craig
                              - Conventional A
                              - Conventional B
                          parameterValue:
                            value: Hartford
                      patientVariables:
                        - id: 'LOINC:30525-0'
                          certitude: 2
                          how: The value was specified by the end user.
                          title: Age
                          variableValue:
                            value: '.5'
                            units: years
                          why: Age is used to calculate the creatinine clearance. Dosing is lower for geriatric patient and contraindicated for pediatric patients
                          legalValues:
                            type: number
                            minimum: '0'
                      timestamp: '2019-12-03T13:41:09.942+00:00'
```

Example JSON (used in code):

```
[
  {
    "piid": "pdspi-fhir-example",
    "title": "Example plugin for fhir smart-fhir server",
    "pluginType": "f",
    "settingsDefaults": {
      "pluginSelectors": [
        {
          "id": "FHIR.URI",
          "title": "FHIR Server URL",
          "legalValues": {
            "type": "string",
            "enum": [
              {
                "value": "urn://cdwh.nctracs.v1",
                "title": "NCTraCS Carolina Data Warehouse"
              },
              {
                "value": "http://hapi.fhir.org/baseR4"
              },
              {
                "value": "https://open-ic.epic.com/FHIR/api/FHIR/DSTU2"
              }
            ]
          },
          "selectorValue": {
            "value": "http://hapi.fhir.org/baseR4",
            "title": "Hapi FHIR base URL"
          }
        }
      ],
      "modelParameters": null,
      "patientVariables": null
    }
  },
  {
    "piid": "pdspi-mapper-example",
    "title": "Example plugin for mapping the smart-fhir server",
    "pluginDependencies": [
      "pdsph-fhir-example"
    ],
    "pluginType": "mD",
    "settingsDefaults": {
      "pluginSelectors": null,
      "modelParameters": null,
      "patientVariables": [
        {
          "id": "LOINC:30525-0",
          "how": null,
          "title": "Age",
          "legalValues": {
            "type": "number",
            "minimum": "0"
          }
        }
      ]
    }
  },
  {
    "piid": "pdspi-guidance-example",
    "title": "Example plugin for Amikacin dosing guidance",
    "pluginDependencies": [
      "string"
    ],
    "pluginType": "g",
    "pluginTypeTitle": "guidance",
    "settingsDefaults": {
      "pluginSelectors": [
        {
          "id": "dosing.rxCUI",
          "title": "Drug",
          "legalValues": {
            "type": "string",
            "enum": [
              {
                "value": "rxCUI:1596450",
                "title": "Gentamicin"
              },
              {
                "value": "rxCUI:1723160",
                "title": "Amikacin"
              }
            ]
          },
          "selectorValue": {
            "value": "rxCUI:1596450",
            "title": "Amikacin"
          }
        }
      ],
      "modelParameters": [
        {
          "id": "pdspi-guidance-example:1",
          "title": "Extended interval nomogram",
          "parameterDescription": "This calculator uses one of four extended-interval nomograms. Please choose one nomogram.",
          "legalValues": {
            "type": "string",
            "enum": [
              "Hartford",
              "Urban-Craig",
              "Conventional A",
              "Conventional B"
            ]
          },
          "parameterValue": {
            "value": "Hartford"
          }
        }
      ],
      "patientVariables": [
        {
          "id": "LOINC:30525-0",
          "certitude": 2,
          "how": "The value was specified by the end user.",
          "title": "Age",
          "variableValue": {
            "value": ".5",
            "units": "years"
          },
          "why": "Age is used to calculate the creatinine clearance. Dosing is lower for geriatric patient and contraindicated for pediatric patients",
          "legalValues": {
            "type": "number",
            "minimum": "0"
          }
        }
      ],
      "timestamp": "2019-12-03T13:41:09.942+00:00"
    }
  }
]
```
