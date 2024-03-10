![123](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/d3245697-2aec-4454-840d-f4a02c6aff7e)
> Wave 1
>
> Question 1: Which Windows feature's optimization failed according to
> the log? Answer: CSL{Microsoft-Windows-Defrag}
>
> File: ossec-alerts-07.json
>
> Method: Just Search Windows application error in every json log ﬁle.
> And got this exact feature name stated as providerName.
>
> Log:

||
||
||
||
||

> Question 2: What policy setting's status changed from
> 'notapplicable'tofailed?
>
> Answer: CSL{password}
>
> File: ossec-alerts-14.json
>
> Method: Search 'not applicable' to failed in theabove ﬁleand got that
> the password policy was changed from0 to 24 or more password(s)
>
> Log:

||
||
||
||
||
||

> 2.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930397.314282","decoder":{"name":"sca"},"data":{"sca":{"ty
> pe":"check","scan_id":"221133515","policy":"CIS Microsoft Windows 10
> Enterprise Benchmark v1.12.0","check":{"id":"15500","title":"Ensure
> 'Enforce password history' is set to '24 or more
> password(s)'.","description":"This policy setting determines the
> number of renewed, unique passwords that have to be associated with a
> user account before you can reuse an old password. The value for this
> policy setting must be between 0 and 24 passwords. The default value
> for Windows Vista is 0 passwords, but the default setting in a domain
> is 24 passwords. To maintain the effectiveness of this policy setting,
> use the Minimum password age setting to prevent users from repeatedly
> changing their password. The recommended state for this setting is: 24
> or more password(s). Note: Password Policy settings (section 1.1) and
> Account Lockout Policy settings (section 1.2) must be applied via the
> Default Domain Policy GPO in order to be globally in effect on domain
> user accounts as their default behavior. If these settings are
> configured in another GPO, they will only affect local user accounts
> on the computers that receive the GPO. However, custom exceptions to
> the default password policy and account lockout policy rules for
> specific domain users and/or groups can be defined using Password
> Settings Objects (PSOs), which are completely separate from Group
> Policy and most easily configured using Active Directory
> Administrative Center. Note \#2: As of the publication of this
> benchmark, Microsoft currently has a maximum limit of 24 saved
> passwords. For more information, please visit Enforce password history
> (Windows 10) - Windows security \| Microsoft Docs","rationale":"The
> longer a user uses the same password, the greater the chance that an
> attacker can determine the password through brute force attacks. Also,
> any accounts that may have been compromised will remain exploitable
> for as long as the password is left unchanged. If password changes are
> required but password reuse is not prevented, or if users continually
> reuse a small number of passwords, the effectiveness of a good
> password policy is greatly reduced. If you specify a low number for
> this policy setting, users will be able to use the same small number
> of passwords repeatedly. If you do not also configure the Minimum
> password age setting, users might repeatedly change their passwords
> until they can reuse their original password.","remediation":"To
> establish the recommended configuration via GP, set the following UI
> path to 24 or more password(s): Computer
> Configuration\\Policies\\Windows Settings\\Security Settings\\Account
> Policies\\Password Policy\\Enforce password
> history","compliance":{"cis":"1.1.1","cis_csc":"5.2"},"command":\["net.exe
> accounts"\],"result":"failed","previous_result":"not
> applicable"}}},"location":"sca"}
>
> Question 3: How many unique passwords must beassociated with a user
> account before an old password can bereused, as recommended?
>
> Answer: CSL{24}
>
> File: ossec-alerts-14.json
>
> Method: Look for password policy in ossec logs and ﬁnd the log related
> to password history. After getting the log look for minimum number of
> password that can be set before using a previous password
>
> Log:

||
||
||
||
||
||

> Configuration\\Policies\\Windows Settings\\Security Settings\\Account
> Policies\\Password Policy\\Enforce password
> history","compliance":{"cis":"1.1.1","cis_csc":"5.2"},"command":\["net.exe
> accounts"\],"result":"failed","previous_result":"not
> applicable"}}},"location":"sca"}
>
> Question 4: In the ﬁrst alert of the log ﬁle, which decoder and rule
> were involved in the detection process? (CSLformat:
> CSL{\<decoder\>\_\<rule number\>})
>
> Answer: CSL{rootcheck_510}
>
> File: ossec-alerts-14.json
>
> Method: Talking about decoder, we know that decoders are used in wazuh
> logs. By looking at ﬁrst event or log, we can get decoder’s name and
> rule number which triggered the event.
>
> Log:

||
||
||
||
||
||
||

> Question 5: Which forensic tool was successfully installedon the
> system? (CSL format: CSL{\<system_version\>})
>
> Answer: CSL{DESKTOP-P79AUVL_3.1.2.0}
>
> File: ossec-alerts-14.json
>
> Method: Here, we know that something was installed on the system and
> it is a forensic tool so start searching for keyword install or
> installation.By looking at few logs related to installation, we saw
> that FTK Imager(which is for sure aforensictool) was installed on the
> system with name DESKTOP-P79AUVL and with version 3.1.2.0.
>
> Log:

||
||
||
||
||

||
||
||
||
||
||
||
||
||

> Question 6: Identify the boot ﬁle modiﬁed by the user with onthe
> Ubuntusystem. (format: CSL{ﬁlename_size})
>
> Answer: CSL{BOOTX64.CSV_108_bytes}
>
> File: ossec-alerts-14.json
>
> Method: Start searching for keyword boot in log ﬁles and by
> goingthrough few logs we can exactlysee the exact name and directory
> of boot ﬁle named BOOTX64.CSV that was modiﬁed. We can also get its
> size withthe key size_after.
>
> Log:

||
||
||
||
||
||
||

<img src="./123.png"
style="width:5.89667in;height:1.39333in" />

> ,"event":"modified"},"decoder":{"name":"syscheck_integrity_changed"},"location
> ":"syscheck"}
>
> Question7: How many registry modiﬁcations were executed by the
> Administrator role in ossec-alerts? (Answer format: CSL{number})
>
> Answer:CSL{9}
>
> File: ossec-alerts-07.json
>
> Method: By searching registry key and Administrator in the ﬁrst log
> ﬁle, we can count the number of time administrators changed the
> registry key which is 9
>
> Question8: What is the timestamp of the initial Windows activation
> update failure,and what is the size of the .textvirtual section?
> (Answer format: CSL{timestamp_size})
>
> Answer: CSL{2024-02-16T22:51:16.979_321502}
>
> File: ossec-alerts-16.json
>
> Method: We need to lookfor activation failure in logs then after
> ﬁnding it.We can get the exact timestampof the event and the .exe ﬁle
> that failed execution which is slui.exe. After getting the ﬁle name,
> we need its hash fromonline tools like echotrail
> (<u>https://www.echotrail.io/insights/search/slui.exe</u>). After
> searching this hash in virustotal, we can get the .text section size
> under the details tab.
>
> Log:

||
||
||
||
||
||
||
||

> failed with the following error code:\r\nhr=0x803F7001\r\nCommand-line
> arguments:\r\nRuleId=31e71c49-8da7-4a2f-ad92-45d98a1c79ba;Action=AutoActivate;AppId=55c92734-d682-4d71-983e-d6ec3f16059f;SkuId=4de7cb65-cdf1-4de9-8ae8-e3cce27b9f2c;NotificationInterval=1440;Trigger=TimerEvent\\"},"eventdata":{"da
> ta":"hr=0x803F7001,
> RuleId=31e71c49-8da7-4a2f-ad92-45d98a1c79ba;Action=AutoActivate;AppId=55c92734-d682-4d71-983e-d6ec3f16059f;SkuId=4de7cb65-cdf1-4de9-8ae8-e3cce27b9f2c;NotificationInterval=1440;Trigger=TimerEvent"}}},"location":"Even
> tChannel"}
>
> Question 9: Identify the attribute utilized for time modiﬁcation.
> (Answer format: CSL{attribute})
>
> Answer: CSL{Mtime}
>
> File: ossec-alerts-14.json
>
> Method: Start searching time attribute in log ﬁles. There are many
> searchresults as time is also part ofthe word timestamp, search for
> exact word.After ﬁnding log containing changing attribute of time.
> Look forattribute that is utilized to changetime which is Mtime.
>
> Log:

||
||
||
||
||

> Question 10: Name the modiﬁed ﬁlewithin the Ubuntu system. (Answer
> format: CSL{ﬁlename})
>
> Answer: CSL{grub.cfg}
>
> File: ossec-alerts-14.json
>
> Method:

||
||
||
||
||

> Wave 2
>
> Question 11: Which registry value integrity checksum change was
> detected in the W32Time service? (Format: CSL{valueName})
>
> Answer: CSL{SecureTimeLow}
>
> File: ossec-alerts-14.json
>
> Method: Start searching W32Time in ossec logs and look for registry
> value integrity checksum changed log and note thevalue that was
> changed in the event full_log and you will get the exact value that
> was modiﬁed in the registry.
>
> Log:
>
> {"timestamp":"2024-02-14T22:06:18.736+0500","rule":{"level":5,"description":"Registry
> Value Integrity Checksum
> Changed","id":"750","mitre":{"id":\["T1565.001","T1112"\],"tactic":\["Impact","De
> fense Evasion"\],"technique":\["Stored Data Manipulation","Modify
> Registry"\]},"firedtimes":16,"mail":false,"groups":\["ossec","syscheck","syschec
> k_entry_modified","syscheck_registry"\],"pci_dss":\["11.5"\],"gpg13":\["4.13"\],"gd
> pr":\["II_5.1.f"\],"hipaa":\["164.312.c.1","164.312.c.2"\],"nist_800_53":\["SI.7"\],