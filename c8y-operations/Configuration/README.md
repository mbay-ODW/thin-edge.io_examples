#  thin-edge.io Textbased Configuration plugin

To configure a device that runs thin-edge.io, a plugin of the operation plugin concept is used. The tedge_agent is checking for configuration operation and is triggering the particular plugin. You can use the configuration tab in device management to change a text based configuration. The plugin itself currently only receives and acknowledges the config change, but does not do anything with it. The part where this can be included is shown in the code section.

## Requirements

- Working thin-edge.io installation

- Python3 and pip3 installation (will not work on python2)


## Installation 

1. Clone this repo on the thin-edge.io device
2. run pip3 install -r requirements.txt from this Configuration directory
3. Copy c8y_Configuration to the following directory "/etc/tedge/operations/c8y/"
4. Copy c8y_Configuration.py to the following directory "/bin/"
5. Make sure, that both files do have permissions for beeing executed by tedge_mapper ("chmod 644 c8y_Configuration and chmod 555 c8y_Configuration.py")


## Usage

Make sure thin-edge.io is connected to Cumulocity.
If installation is done properly according to the steps above, you hae to disconnect and reconnect thin-edge.io. In that way the suppoerted Operations will be updated.

```shell
sudo tedge disconnect c8y
```

and

```shell
sudo tedge connect c8y
```

However it would also to be sufficient to restart the tedge_mapper service via e.g.:

```shell
sudo systemctl tedge_mapper restart
```

You device within Cumulocity should look similar to this afterwards:


<br/><br/>
<p style="text-indent:30px;">
  <a>
  <center>
    <img width="70%" src="pics/dm.png">
  </center>
  </a>
</p>
<br/>

You can configure now within the configuration tab to what text, variables etc the config should hold.

<br/><br/>
<p style="text-indent:30px;">
  <a>
  <center>
    <img width="70%" src="pics/config.png">
  </center>
  </a>
</p>
<br/>

If you click on "Send configuration to device" thin-edge.io triggers the c8y_Configuration.py script.