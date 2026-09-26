# Steps to integrate Sysmon in Splunk Enterprise for event logs

1. Open Windows Powershell as Administrator.
2. Go to the following path:

```
cd "C:\Program Files\SplunkUniversalForwarder\etc\system\local"

```

3. Create the **inputs.conf** file there

```
notepad inputs.conf

```

4. Add the following lines in **inputs.conf**

```
[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
renderXml = true
index = main

```

5. Restart the forwarder

```
Restart-Service SplunkForwarder

```

6. Then verify

```
Get-Service SplunkForwader

```
You should see **Running**

7. Goto the **Splunk Dashboard > Apps > Search & Report** and type in the searchbar

```
index=main host="<your-hostname>" sourcetype="WinEventLog:Microsoft-Windows-Sysmon/Operational"

```
8. You should see the sourcetype eventually
