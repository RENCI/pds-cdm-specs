# pds-cdm-specs
Use these specs in the PDS APIs

# examples

## Guidance
Below includes an array of configs, one each for FHIR, Mapper, and Guidance types.

Example Yaml: (used in specs)
```
            example:
              piid: pdspi-guidance-example
              title: Aminoglycoside dosing guidance
              txid: 38-1
              ptid: smart-7321938
              mapper_piid: pdspi-mapper-example
              fhir_piid: pdspi-fhir-example
              inputs:
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
                      value: 'rxCUI:1723160'
                      title: Amikacin
                modelParameters:
                  - id: 'pdspi-guidance-example:1'
                    title: Extended interval nomogram
                    parameterDescription: >-
                      This calculator uses one of four extended-interval
                      nomograms. Please choose one nomogram.
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
                    certitude: 1
                    how: The value was specified by the end user.
                    title: Age
                    variableValue:
                      value: '.5'
                      units: years
                    why: >-
                      Age is used to calculate the creatinine clearance. Dosing
                      is lower for geriatric patient and contraindicated for
                      pediatric patients
                    legalValues:
                      type: number
                      minimum: '0'
                timestamp: '2019-12-03T13:41:09.942+00:00'
              return:
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
                    parameterDescription: >-
                      This calculator uses one of four extended-interval
                      nomograms. Please choose one nomogram.
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
                    certitude: 1
                    how: The value was specified by the end user.
                    title: Age
                    variableValue:
                      value: '.5'
                      units: years
                    why: >-
                      Age is used to calculate the creatinine clearance. Dosing
                      is lower for geriatric patient and contraindicated for
                      pediatric patients
                    legalValues:
                      type: number
                      minimum: '0'
                timestamp: '2019-12-03T13:41:09.942+00:00'
              cards:
                - detail: some sort of optional GitHub Markdown details
                  id: string
                  indicator: info
                  links:
                    - appContext: string
                      label: SMART Example App
                      type: string
                      url: string
                  selectionBehavior: string
                  source:
                    icon: 'https://example.com/img/icon-100px.png'
                    label: Human-readable source label
                    url: 'https://example.com'
                  suggestions:
                    - actions:
                        - description: Create a prescription for Acetaminophen 250 MG
                          resource: MedicationRequest
                          type: create
                      label: Human-readable suggestion label
                      uuid: e1187895-ad57-4ff7-a1f1-ccf954b2fe46
                  summary: some <140 char Summary Message
                  title: string
              specs:
                - $schema: 'https://vega.github.io/schema/vega-lite/v4.json'
                  autosize:
                    resize: true
                  data:
                    name: data
                  description: Time-series line chart
                  encoding:
                    color:
                      field: group
                      type: nominal
                    x:
                      axis:
                        title: x axis
                      bin: true
                      field: x
                      type: quantitative
                    'y':
                      aggregate: count
                      axis:
                        title: y axis
                      field: 'y'
                      type: quantitative
                  height: container
                  mark: line
                  title: Line chart
                  width: container

```

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
          
```

## Config
Below includes an array of configs, one each for FHIR, Mapper, and Guidance types.

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
