# pds-cdm-specs
Use these specs in the PDS APIs

# examples
## Config

```
                example:
                  - piid: pdspi-mapper-example
                    title: Example plugin for mapping the smart-fhir server
                    pluginDependencies:
                      - string
                    pluginType: m
                    pluginTypeTitle: string
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
                          certitude: 1
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
                  - piid: pdspi-guidance-example
                    title: Example plugin for Amikacin dosing guidance
                    pluginDependencies:
                      - string
                    pluginType: g
                    pluginTypeTitle: string
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
                          certitude: 1
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
