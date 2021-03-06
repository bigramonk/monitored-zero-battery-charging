# monitored-zero-battery-charging
Monitor Zero battery charging from within Home Assistant with an old/unused Android phone

## Getting Started

### Prerequisites
Install the Zero Motorcycle app on your old Android phone and get it connected to the bike.
Then install ZeroSpy.

## ZeroSpy home screen
Connect ZeroSpy to your bike using Bluetooth and you should soon see your bike data appear on the screen:
<br><img src="./images/zerospy_main_menu.jpg" width="200" />

## ZeroSpy configuration

### ZeroSpy general settings
In the settings, I left everything unchecked except <i>Keep Screen On</i>:
<br><img src="./images/zerospy_settings_general_1.jpg" width="200" />

### ZeroSpy auto connect
In the auto connect menu, I checked both <i>Auto Connect</i> and <i>Connect After Boot</i>: 
<br><img src="./images/zerospy_settings_auto_connect.jpg" width="200" />

## The triggers
When the trigger condition is met, a URL can be called along with a JSON body.
I set 4 different triggers:
<br><img src="./images/zerospy_triggers.jpg" width="200" />

### Publish battery state change event
<br><img src="./images/zerospy_webhook_trigger_every_percent.jpg" width="200" />
### Publish battery full event
<br><img src="./images/zerospy_webhook_trigger_battery_full.jpg" width="200" />
### Publish connection failure event
<br><img src="./images/zerospy_webhook_trigger_connection_failure.jpg" width="200" />
### Publish connection change event
<br><img src="./images/zerospy_webhook_trigger_connection_state_change.jpg" width="200"/>

# Home Assistant webhooks
Home assistant webhooks hace to be called using the following URL type:<br>
https://<i>your home assistant instance</i>:<i>port</i>:/api/webhook/<i>webhook id</i>
<br>where:
<pre>port: 8123 by default</pre>
<pre>webhook id: random hex number, up to 64 characters that will be used as trigger in an automation</pre>
  trigger:
    platform: webhook
    webhook_id: abcdef
