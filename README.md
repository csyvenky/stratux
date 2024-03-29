# Stratux
Splunk App to process data from Stratux ADS-B Receiver.

This is __not__ the codebase for the ADS-B receiver Stratux, that can be found [here](https://github.com/cyoung/stratux).

*This is a work in progress.*

# Setup
1. Create an index on your Splunk instance, I called mine "*stratux*". If you plan to store and process a lengthy timeframe of data then this should be set to 3-5 GB in size.
2. Pull your Stratux Receiver logs.
    ```
    scp pi@192.168.10.1:/var/log/stratux.log <directory_of_your_inputs.conf_monitor>.
    ```
3. Point your file input monitor at your data folder; select "*Stratux*" as the sourcetype. This can be done directly to indexes.conf.
    ```
    [monitor://<your>\<path>\<to logs>\stratux.log]
    ```
4. Install the app.

# Install
1. Navigate to $SPLUNK_HOME/etc/apps
2. Execute: `git clone https://github.com/csyvenky/stratux.git`
3. Restart Splunk: via Splunk Web or any other way you know how. Alternatively, you can use the Ansible Playbook 
*restart_splunk.yml* - a quick and dirty restart tool for splunkd.
    ```
    ansible-playbook -i hosts restart_splunk.yml --ask-pass
    ```

# Use
1. Access the main [Dashboard](http://your-splunk-ip:8000/en-GB/app/stratux/stratux?form.field1.earliest=-24h%40h&form.field1.latest=now)