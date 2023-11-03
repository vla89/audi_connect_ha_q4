Changes for getting Data from q4 etron
============================================================

I changed a few things to get the data retrieval for my audi q4 etron working. 
![image](https://github.com/moritzwiechers/audi_connect_ha_q4/assets/9558898/86d91c18-8e9e-43ea-9879-5036bc8898e3)

Unfortunately, I know too little about python and the home-assistant structure to customize the integration to still run over the other endpoint. 
The data of the endpoint has a different structure than the other endpoint, so I mapped 3 dates: battery state of charge in %, range in km and milage in km to the predefined entities. 

get_stored_vehicle_data endpoint:

https://emea.bff.cariad.digital/vehicle/v1/vehicles/{vin}/selectivestatus?jobs=all

This endpoint works for me, located in germany. I had to use _bearer_token_json as token to get it work and allow http-status code 207 in the request function and map the endpoint data.
If this information is enough feel free to use it. 

If someone is around with knowledge about pyhton and home-assistant, maybe the information can be useful. 

<details>
  <summary>Endpoint data</summary>
  
```json
{
    "access": {
        "accessStatus": {
            "value": {
                "overallStatus": "safe",
                "carCapturedTimestamp": "2023-11-02T11:33:10.289Z",
                "doors": [
                    {
                        "name": "bonnet",
                        "status": [
                            "closed"
                        ]
                    },
                    {
                        "name": "trunk",
                        "status": [
                            "closed",
                            "locked"
                        ]
                    },
                    {
                        "name": "rearRight",
                        "status": [
                            "closed",
                            "locked"
                        ]
                    },
                    {
                        "name": "rearLeft",
                        "status": [
                            "closed",
                            "locked"
                        ]
                    },
                    {
                        "name": "frontRight",
                        "status": [
                            "closed",
                            "locked"
                        ]
                    },
                    {
                        "name": "frontLeft",
                        "status": [
                            "closed",
                            "locked"
                        ]
                    }
                ],
                "windows": [
                    {
                        "name": "sunRoof",
                        "status": [
                            "unsupported"
                        ]
                    },
                    {
                        "name": "roofCover",
                        "status": [
                            "unsupported"
                        ]
                    },
                    {
                        "name": "sunRoofRear",
                        "status": [
                            "unsupported"
                        ]
                    },
                    {
                        "name": "frontLeft",
                        "status": [
                            "closed"
                        ]
                    },
                    {
                        "name": "frontRight",
                        "status": [
                            "closed"
                        ]
                    },
                    {
                        "name": "rearLeft",
                        "status": [
                            "closed"
                        ]
                    },
                    {
                        "name": "rearRight",
                        "status": [
                            "closed"
                        ]
                    }
                ],
                "doorLockStatus": "locked"
            }
        }
    },
    "automation": {
        "climatisationTimer": {
            "value": {
                "timers": [
                    {
                        "id": 1,
                        "enabled": false,
                        "singleTimer": {
                            "startDateTime": "2023-11-03T05:50:00Z"
                        }
                    },
                    {
                        "id": 2,
                        "enabled": false,
                        "singleTimer": {
                            "startDateTime": "2023-11-03T04:55:00Z"
                        }
                    }
                ],
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "timeInCar": "2023-11-02T12:33:10+01:00"
            }
        },
        "chargingProfiles": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10.119Z",
                "timeInCar": "2023-11-02T12:33:10+01:00",
                "profiles": [
                    {
                        "id": 2,
                        "name": "Home",
                        "maxChargingCurrent": "max",
                        "minSOC_pct": 0,
                        "targetSOC_pct": 100,
                        "options": {
                            "autoUnlockPlugWhenCharged": "off"
                        },
                        "preferredChargingTimes": [
                            {
                                "id": 5,
                                "enabled": false,
                                "startTime": "23:00",
                                "endTime": "23:00"
                            }
                        ],
                        "timers": [],
                        "minSOC_enabled": false
                    }
                ]
            }
        }
    },
    "userCapabilities": {
        "capabilitiesStatus": {
            "value": [
                {
                    "id": "alexa",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "automation",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "batteryChargingCare",
                    "userDisablingAllowed": true
                },
                {
                    "id": "batteryColdWarning",
                    "userDisablingAllowed": true
                },
                {
                    "id": "calendar",
                    "userDisablingAllowed": false
                },
                {
                    "id": "charging",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "chargingProfiles",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "chargingTimers",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "cityModels",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "climatisation",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "climatisationTimers",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "cubicNetwork",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "destinationSync",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "eRoutePlanner",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "emergencyCalling",
                    "userDisablingAllowed": false
                },
                {
                    "id": "fuelStatus",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "hybridRadio",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "ignition",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "localHazards",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "mapUpdate",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "mapUpdateSd",
                    "userDisablingAllowed": false
                },
                {
                    "id": "measurements",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "news",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "onStreetParking",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "onlineBoardBook",
                    "userDisablingAllowed": true
                },
                {
                    "id": "onlineSpeech",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "onlineTraffic",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "onlineTrafficPlus",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "parkingBrake",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "parkingPosition",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "plugAndCharge",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "poiSearch",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "predictiveRouting",
                    "userDisablingAllowed": false
                },
                {
                    "id": "privateEmergencyCall",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "readiness",
                    "userDisablingAllowed": false
                },
                {
                    "id": "satelliteMap",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "songRecognition",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "state",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "theming",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "trafficLights",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "trafficSigns",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "vehicleHealth",
                    "userDisablingAllowed": true
                },
                {
                    "id": "vehicleHealthWarnings",
                    "userDisablingAllowed": false
                },
                {
                    "id": "vehicleLights",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "vehicleWakeUpTrigger",
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": false
                },
                {
                    "id": "weatherInformation",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "webRadio",
                    "status": [
                        2001
                    ],
                    "expirationDate": "2023-10-10T23:59:59Z",
                    "userDisablingAllowed": true
                },
                {
                    "id": "wifiHotspot",
                    "userDisablingAllowed": true
                }
            ]
        }
    },
    "charging": {
        "batteryStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "currentSOC_pct": 63,
                "cruisingRangeElectric_km": 320
            }
        },
        "chargingStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "remainingChargingTimeToComplete_min": 0,
                "chargingState": "notReadyForCharging",
                "chargeMode": "manual",
                "chargePower_kW": 0,
                "chargeRate_kmph": 0,
                "chargeType": "invalid",
                "chargingSettings": "profile"
            }
        },
        "chargingSettings": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "targetSOC_pct": 100
            }
        },
        "plugStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "plugConnectionState": "disconnected",
                "plugLockState": "unlocked",
                "externalPower": "unavailable",
                "ledColor": "none"
            }
        },
        "chargeMode": {
            "value": {
                "preferredChargeMode": "manual",
                "availableChargeModes": [
                    "manual",
                    "timer"
                ]
            }
        },
        "chargingCareSettings": {
            "value": {
                "batteryCareMode": "deactivated"
            }
        }
    },
    "batteryChargingCare": {
        "chargingCareSettings": {
            "value": {
                "batteryCareMode": "deactivated"
            }
        }
    },
    "climatisation": {
        "climatisationSettings": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "targetTemperature_C": 20.5,
                "targetTemperature_F": 69,
                "unitInCar": "celsius",
                "climatizationAtUnlock": false,
                "windowHeatingEnabled": true,
                "zoneFrontLeftEnabled": true,
                "zoneFrontRightEnabled": true
            }
        },
        "climatisationStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:19Z",
                "climatisationState": "off"
            }
        },
        "windowHeatingStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:19Z",
                "windowHeatingStatus": [
                    {
                        "windowLocation": "front",
                        "windowHeatingState": "off"
                    },
                    {
                        "windowLocation": "rear",
                        "windowHeatingState": "off"
                    }
                ]
            }
        }
    },
    "climatisationTimers": {
        "climatisationTimersStatus": {
            "value": {
                "timers": [
                    {
                        "id": 1,
                        "enabled": false,
                        "singleTimer": {
                            "startDateTime": "2023-11-03T05:50:00Z"
                        }
                    },
                    {
                        "id": 2,
                        "enabled": false,
                        "singleTimer": {
                            "startDateTime": "2023-11-03T04:55:00Z"
                        }
                    }
                ],
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "timeInCar": "2023-11-02T12:33:10+01:00"
            }
        }
    },
    "fuelStatus": {
        "rangeStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "carType": "electric",
                "primaryEngine": {
                    "type": "electric",
                    "currentSOC_pct": 63,
                    "remainingRange_km": 320
                },
                "totalRange_km": 320
            }
        }
    },
    "vehicleLights": {
        "lightsStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10.24Z",
                "lights": [
                    {
                        "name": "right",
                        "status": "off"
                    },
                    {
                        "name": "left",
                        "status": "off"
                    }
                ]
            }
        }
    },
    "measurements": {
        "rangeStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10.182Z",
                "electricRange": 320,
                "totalRange_km": 320
            }
        },
        "odometerStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10.241Z",
                "odometer": 12357
            }
        },
        "fuelLevelStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10.21Z",
                "currentSOC_pct": 63,
                "primaryEngineType": "electric",
                "carType": "electric"
            }
        }
    },
    "readiness": {
        "readinessStatus": {
            "value": {
                "connectionState": {
                    "isOnline": true,
                    "isActive": false,
                    "batteryPowerLevel": "comfort",
                    "dailyPowerBudgetAvailable": true
                },
                "connectionWarning": {
                    "insufficientBatteryLevelWarning": false,
                    "dailyPowerBudgetWarning": false
                }
            }
        }
    },
    "vehicleHealthWarnings": {
        "warningLights": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:18:24.434Z",
                "mileage_km": 12357
            }
        }
    },
    "chargingTimers": {
        "chargingTimersStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10Z",
                "timeInCar": "2023-11-02T12:33:10+01:00",
                "timers": [
                    {
                        "id": 1,
                        "enabled": false,
                        "climatisation": false,
                        "recurringTimer": {
                            "departureTime": "11:00",
                            "repetitionDays": [
                                "monday",
                                "tuesday",
                                "wednesday",
                                "thursday",
                                "friday",
                                "saturday",
                                "sunday"
                            ]
                        }
                    },
                    {
                        "id": 2,
                        "enabled": false,
                        "climatisation": false,
                        "recurringTimer": {
                            "departureTime": "11:00",
                            "repetitionDays": [
                                "monday",
                                "tuesday",
                                "wednesday",
                                "thursday",
                                "friday",
                                "saturday",
                                "sunday"
                            ]
                        }
                    },
                    {
                        "id": 3,
                        "enabled": false,
                        "climatisation": false,
                        "recurringTimer": {
                            "departureTime": "11:00",
                            "repetitionDays": [
                                "monday",
                                "tuesday",
                                "wednesday",
                                "thursday",
                                "friday",
                                "saturday",
                                "sunday"
                            ]
                        }
                    },
                    {
                        "id": 4,
                        "enabled": false,
                        "climatisation": false,
                        "recurringTimer": {
                            "departureTime": "11:00",
                            "repetitionDays": [
                                "monday",
                                "tuesday",
                                "wednesday",
                                "thursday",
                                "friday",
                                "saturday",
                                "sunday"
                            ]
                        }
                    },
                    {
                        "id": 5,
                        "enabled": false,
                        "climatisation": false,
                        "recurringTimer": {
                            "departureTime": "11:00",
                            "repetitionDays": [
                                "monday",
                                "tuesday",
                                "wednesday",
                                "thursday",
                                "friday",
                                "saturday",
                                "sunday"
                            ]
                        }
                    }
                ]
            }
        }
    },
    "chargingProfiles": {
        "chargingProfilesStatus": {
            "value": {
                "carCapturedTimestamp": "2023-11-02T11:33:10.119Z",
                "timeInCar": "2023-11-02T12:33:10+01:00",
                "profiles": [
                    {
                        "id": 2,
                        "name": "Home",
                        "maxChargingCurrent": "max",
                        "minSOC_pct": 0,
                        "targetSOC_pct": 100,
                        "options": {
                            "autoUnlockPlugWhenCharged": "off"
                        },
                        "preferredChargingTimes": [
                            {
                                "id": 5,
                                "enabled": false,
                                "startTime": "23:00",
                                "endTime": "23:00"
                            }
                        ],
                        "timers": [],
                        "minSOC_enabled": false
                    }
                ]
            }
        }
    }
}
```
</details>


Audi Connect Integration for Home Assistant
============================================================

[![GitHub Activity][commits-shield]][commits]
[![License][license-shield]](LICENSE.md)
[![Code Style][blackbadge]][black]

[![hacs][hacsbadge]](hacs)

Maintainers Wanted
------------
Due to time limitations this project is not actively maintained anymore. It will continue to work as long as Audi does not change the API again. 
However, I'm open to someone else taking the lead. If you would like to become a maintainer, please contact me.

Description
------------
The `audiconnect` component provides an integration with the Audi Connect cloud service. It adds presence detection, sensors such as range, mileage, and fuel level, and provides car actions such as locking/unlocking and setting the pre-heater.

**Note:** Certain functions require special permissions from Audi, such as position update via GPS. 

Credit for initial API discovery go to the guys at the ioBroker VW-Connect forum, who were able to figure out how the API and the PIN hashing works. Also some implementation credit to davidgiga1993 of the original [AudiAPI](https://github.com/davidgiga1993/AudiAPI) Python package, on which some of this code is loosely based.

Installation
------------

There are two ways this integration can be installed into [Home Assistant](https://www.home-assistant.io).

The easiest and recommended way is to install the integration using [HACS](https://hacs.xyz), which makes future updates easy to track and install.

Alternatively, installation can be done manually by copying the files in this repository into the `custom_components` directory in the Home Assistant configuration directory:
1. Open the configuration directory of your Home Assistant installation.
2. If you do not have a `custom_components` directory, create it.
3. In the `custom_components` directory, create a new directory called `audiconnect`.
4. Copy all files from the `custom_components/audiconnect/` directory in this repository into the `audiconnect` directory.
5. Restart Home Assistant.
6. Add the integration to Home Assistant (see **Configuration**).

Configuration
-------------

Configuration is done through the Home Assistant UI.

To add the integration, go to **Settings ➤ Devices & Services ➤ Integrations**, click **➕ Add Integration**, and search for "Audi Connect".

![Configuration](ha_config.png)

### Configuration Variables

**username**

- (string)(Required) The username associated with your Audi Connect account.

**password**

- (string)(Required) The password for your Audi Connect account.

**S-PIN**

- (string)(Optional) The S-PIN for your Audi Connect account.

**region**

- (string)(Optional) The region where your Audi Connect account is registered. 
   * 'DE' for Europe (or leave unset)
   * 'US' for United States of America
   * 'CA' for Canada
   * 'CN' for China

**scan_interval**

- (number)(Optional) The frequency in minutes for how often to fetch status data from Audi Connect. (Optional. Default is 10 minutes, can be no more frequent than 1 min.)

Services
--------

**audiconnect.refresh_vehicle_data**

Normal updates retrieve data from the Audi Connect service, and don't interact directly with the vehicle. _This_ service triggers an update request from the vehicle itself. When data is retrieved successfully, Home Assistant is automatically updated. The service requires a vehicle identification number (VIN) as a parameter. 

**audiconnect.execute_vehicle_action**

Perform an action on the vehicle. The service takes a VIN and the action to perform as parameters. Possible action values:
- lock
- unlock 
- start_climatisation
- stop_climatisation
- start_charger
- start_timed_charger
- stop_charger
- start_preheater
- stop_preheater
- start_window_heating
- stop_window_heating 

**Note:** Certain action require the S-PIN to be set in the configuration. 

When an action is successfully performed, an update request is automatically triggered. 

Example Dashboard Card
----------------------

Below is an example Dashboard (Lovelace) card illustrating some of the sensors this Home Assistant addon provides. 

![Example Dashboard Card](card_example.png)

The card requires the following front end mods:
- https://github.com/thomasloven/lovelace-card-mod
- https://github.com/custom-cards/circle-sensor-card

These mods can (like this integration) be installed using HACS.

The card uses the following code in `ui-lovelace.yaml` (or wherever your Dashboard is configured).

```yaml
     - type: picture-elements
        image: /local/pictures/audi_sq7.jpeg
        style: | 
          ha-card {
            border-radius: 10px;
            border: solid 1px rgba(100,100,100,0.3);
            box-shadow: 3px 3px rgba(0,0,0,0.4);
            overflow: hidden;
          } 
        elements:
        - type: image
          image: /local/pictures/cardbackK.png
          style:
            left: 50%
            top: 90%
            width: 100%
            height: 60px

        - type: icon
          icon: mdi:car-door
          entity: sensor.doors_trunk_sq7
          tap_action: more_info
          style: {color: white, left: 10%, top: 86%}
        - type: state-label
          entity: sensor.doors_trunk_sq7
          style: {color: white, left: 10%, top: 95%}

        - type: state-icon
          entity: sensor.windows_sq7
          tap_action: more_info
          style: {color: white, left: 30%, top: 86%}
        - type: state-label
          entity: sensor.windows_sq7
          style: {color: white, left: 30%, top: 95%}

        - type: icon
          icon: mdi:oil
          entity: sensor.audi_sq7_oil_level
          tap_action: more_info
          style: {color: white, left: 50%, top: 86%}
        - type: state-label
          entity: sensor.audi_sq7_oil_level
          style: {color: white, left: 50%, top: 95%}

        - type: icon
          icon: mdi:room-service-outline
          entity: sensor.audi_sq7_service_inspection_time
          tap_action: more_info
          style: {color: white, left: 70%, top: 86%}
        - type: state-label
          entity: sensor.audi_sq7_service_inspection_time
          style: {color: white, left: 70%, top: 95%}

        - type: icon
          icon: mdi:speedometer
          entity: sensor.audi_sq7_mileage
          tap_action: more_info
          style: {color: white, left: 90%, top: 86%}
        - type: state-label
          entity: sensor.audi_sq7_mileage
          style: {color: white, left: 90%, top: 95%}

        - type: custom:circle-sensor-card
          entity: sensor.audi_sq7_tank_level
          max: 100
          min: 0
          stroke_width: 15
          gradient: true
          fill: '#aaaaaabb'
          name: tank
          units: ' '
          font_style:
            font-size: 1.0em
            font-color: white
            text-shadow: '1px 1px black'
          style:
            top: 5%
            left: 80%
            width: 4em
            height: 4em
            transform: none

        - type: custom:circle-sensor-card
          entity: sensor.audi_sq7_range
          max: 630
          min: 0
          stroke_width: 15
          gradient: true
          fill: '#aaaaaabb'
          name: range
          units: ' '
          font_style:
            font-size: 1.0em
            font-color: white
            text-shadow: '1px 1px black'
          style:
            top: 5%
            left: 5%
            width: 4em
            height: 4em
            transform: none
```

[buymecoffee]: https://buymeacoff.ee/arjenvrh
[buymecoffeebadge]: https://img.shields.io/badge/buy%20me%20a%20beer-donate-yellow.svg?style=for-the-badge
[commits-shield]: https://img.shields.io/github/commit-activity/y/arjenvrh/audi_connect_ha?style=for-the-badge
[commits]: https://github.com/arjenvrh/audi_connect_ha/commits/master
[hacs]: https://github.com/custom-components/hacs
[hacsbadge]: https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge
[license-shield]: https://img.shields.io/github/license/arjenvrh/audi_connect_ha?style=for-the-badge
[maintenance-shield]: https://img.shields.io/badge/maintainer-Arjen%20van%20Rhijn%20%40arjenvrh-blue.svg?style=for-the-badge
[blackbadge]: https://img.shields.io/badge/code%20style-black-000000.svg?style=for-the-badge
[black]: https://github.com/ambv/black
