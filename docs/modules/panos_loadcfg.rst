.. _panos_loadcfg:

panos_loadcfg
``````````````````````````````

Synopsis
--------


Load configuration on PAN-OS device


Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
        <tr style="text-align:center">
    <td style="vertical-align:middle">username</td>
    <td style="vertical-align:middle">no</td>
    <td style="vertical-align:middle">admin</td>
        <td style="vertical-align:middle;text-align:left"><ul style="margin:0;"></ul></td>
        <td style="vertical-align:middle;text-align:left">
      username for authentication<br></td>
    </tr>
        <tr style="text-align:center">
    <td style="vertical-align:middle">commit</td>
    <td style="vertical-align:middle">no</td>
    <td style="vertical-align:middle">True</td>
        <td style="vertical-align:middle;text-align:left"><ul style="margin:0;"></ul></td>
        <td style="vertical-align:middle;text-align:left">
      commit if changed<br></td>
    </tr>
        <tr style="text-align:center">
    <td style="vertical-align:middle">password</td>
    <td style="vertical-align:middle">yes</td>
    <td style="vertical-align:middle"></td>
        <td style="vertical-align:middle;text-align:left"><ul style="margin:0;"></ul></td>
        <td style="vertical-align:middle;text-align:left">
      password for authentication<br></td>
    </tr>
        <tr style="text-align:center">
    <td style="vertical-align:middle">ip_address</td>
    <td style="vertical-align:middle">yes</td>
    <td style="vertical-align:middle"></td>
        <td style="vertical-align:middle;text-align:left"><ul style="margin:0;"></ul></td>
        <td style="vertical-align:middle;text-align:left">
      IP address (or hostname) of PAN-OS device<br></td>
    </tr>
        <tr style="text-align:center">
    <td style="vertical-align:middle">file</td>
    <td style="vertical-align:middle">no</td>
    <td style="vertical-align:middle">None</td>
        <td style="vertical-align:middle;text-align:left"><ul style="margin:0;"></ul></td>
        <td style="vertical-align:middle;text-align:left">
      configuration file to load<br></td>
    </tr>
        </table><br>


.. important:: Requires pan-python


Examples
--------

 ::

    
    # Import and load config file from URL
      - name: import configuration
        panos_import:
          ip_address: "192.168.1.1"
          password: "admin"
          url: "{{ConfigURL}}"
          category: "configuration"
        register: result
      - name: load configuration
        panos_loadcfg:
          ip_address: "192.168.1.1"
          password: "{{password}}"
          file: "{{result.filename}}"
