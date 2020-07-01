# pds-cdm-specs
Use these specs in the PDS APIs

# examples
## Config
Yaml: (used in specs)
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
example Json (used in code):

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
