# Home Assistant integration for Husqvarna Automower

![Maintenance](https://img.shields.io/maintenance/yes/2020.svg)


Custom component to support Automower.


- [About](#about)
- [Installation](#installation)
  - [Installation through HACS](#installation-through-hacs)
  - [Manual installation](#manual-installation)
- [Configuration](#configuration)
  - [Gardena Application Key / Client ID](#gardena-application-key--client-id)
  - [Home Assistant](#home-assistant)
- [Usage](#usage)
- [TODO](#todo)

## About

The idea for this component ist coming from the https://github.com/walthowd/ha-automower integration. As this integration doesn't use the offical API, I decided to create a
integration, which is based on the offical API: https://developer.husqvarnagroup.cloud/
There are some disatvanteges between, the offical API and the unoffical API:

- Offical API doesn't support GSP data
- Offical API is limited is limited to 10,000 accesses per 30 days
- API-Key is needed

But the adavantage is, that Husqvarna won't close the offical API suddenly


## Installation

Requires Home Assistant 0.113 or newer.

### Installation through HACS

Not provided yet.

### Manual installation

Copy the sub-path `/custom_components/husqvarna_automower` of this repo into the path `/config/custom_components/husqvarna_automower` of your HA installation. 

## Configuration


### Husqvarna API-Key

In order to use this integration you must get a API-Key from Husqvarna.

1. Go to https://developer.husqvarnagroup.cloud/

2. Create an account if needed, otherwise sign in with your Husqvarna account.

3. After signing in you will be automatically redirected to "Your
   applications". (Otherwise go to: https://developer.husqvarnagroup.cloud/apps)

4. Create an new application, name it for example "My Home Assistant"
   (doesn't matter), leave the other fields empty.

5. Click on "+Connect new API" and connect the Authentication API and
   the Husqvarna Automower API.

6. Copy your Application Key, this is what you need when you add the integration in Home Assistant.

### Home Assistant

Setup under Integrations in Home Assistant, search for "husqvarna_automower". You need to enter e-mail, password and your API-Key.
If the integration is not shown, try to refresh your browser (F5) or (Shift+F5). Maybe you need to reopen your browser.

## Usage

`vacuum.pause`  
Pauses the mower until a new command

`vacuum.stop`  
The mower returns to the base and parks ther until the next scheduled start

`vacuum.return_to_base`  
The mower returns to the base and parks ther until it gets a new start command

`vacuum.start`  
The mower continues to mow, within the specifed schedule


### TODO

- If you enter the wrong credentials in the Home Assistant config flow, it will not be recongnized
- Out-source the communitcation to the API from Home Assistant to get away the warning `Detected I/O inside the event loop. This is causing stability issues.`
- General code improvement
- The integration only supports one mower