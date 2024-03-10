Wave 1
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
> 1054: {"timestamp":"2024-02-07T15:24:54.862+0500","rule":{"level":9,"description":"Windows application error event.","id":"60602","firedtimes":1,"mail":false,"groups":["windows","windows_application","system_error"],"gdpr":["IV_35.7.d"],"gpg13":["4.3"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707301494.3773656","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"Microsoft-Windows-Defrag", "eventID":"264","version":"0","level":"2","task":"0","opcode":"0","keywords":"0x80000000000000","systemTime":"2024-02-07T10:24:54.9244187Z","eventRecordID":"1545","processID":"0","threadID":"0","channel":"Application","computer":"DESKTOP-P79AUVL","severityValue":"ERROR","message":"\"The storage optimizer couldn't complete retrim on (C:) because: The operation requested is not supported by the hardware backing the volume. (0x8900002A)\""},"eventdata":{"binary":"2A000089800200008D0000009000000022B63823DBB1BD381B0700000000000000000000","data":"retrim, (C:), The operation requested is not supported by the hardware backing the volume. (0x8900002A)"}}},"location":"EventChannel"}


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
> 342: {"timestamp":"2024-02-14T22:06:37.782+0500","rule":{"level":9,"description":"CIS Microsoft Windows 10 Enterprise Benchmark v1.12.0: Ensure 'Enforce password history' is set to '24 or more password(s)'.: Status changed from 'not applicable' to failed","id":"19014","firedtimes":1,"mail":false,"groups":["sca"],"gdpr":["IV_35.7.d"],"pci_dss":["2.2"],"nist_800_53":["CM.1"],"tsc":["CC7.1","CC7.2"],"cis":["1.1.1"],"cis_csc":["5.2"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930397.314282","decoder":{"name":"sca"},"data":{"sca":{"type":"check","scan_id":"221133515","policy":"CIS Microsoft Windows 10 Enterprise Benchmark v1.12.0","check":{"id":"15500","title":"Ensure 'Enforce password history' is set to '24 or more password(s)'.","description":"This policy setting determines the number of renewed, unique passwords that have to be associated with a user account before you can reuse an old password. The value for this policy setting must be between 0 and 24 passwords. The default value for Windows Vista is 0 passwords, but the default setting in a domain is 24 passwords. To maintain the effectiveness of this policy setting, use the Minimum password age setting to prevent users from repeatedly changing their password. The recommended state for this setting is: 24 or more password(s). Note: Password Policy settings (section 1.1) and Account Lockout Policy settings (section 1.2) must be applied via the Default Domain Policy GPO in order to be globally in effect on domain user accounts as their default behavior. If these settings are configured in another GPO, they will only affect local user accounts on the computers that receive the GPO. However, custom exceptions to the default password policy and account lockout policy rules for specific domain users and/or groups can be defined using Password Settings Objects (PSOs), which are completely separate from Group Policy and most easily configured using Active Directory Administrative Center. Note #2: As of the publication of this benchmark, Microsoft currently has a maximum limit of 24 saved passwords. For more information, please visit Enforce password history (Windows 10) - Windows security | Microsoft Docs","rationale":"The longer a user uses the same password, the greater the chance that an attacker can determine the password through brute force attacks. Also, any accounts that may have been compromised will remain exploitable for as long as the password is left unchanged. If password changes are required but password reuse is not prevented, or if users continually reuse a small number of passwords, the effectiveness of a good password policy is greatly reduced. If you specify a low number for this policy setting, users will be able to use the same small number of passwords repeatedly. If you do not also configure the Minimum password age setting, users might repeatedly change their passwords until they can reuse their original password.","remediation":"To establish the recommended configuration via GP, set the following UI path to 24 or more password(s): Computer Configuration\\Policies\\Windows Settings\\Security Settings\\Account Policies\\Password Policy\\Enforce password history","compliance":{"cis":"1.1.1","cis_csc":"5.2"},"command":["net.exe accounts"],"result":"failed","previous_result":"not applicable"}}},"location":"sca"}

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
> 342: {"timestamp":"2024-02-14T22:06:37.782+0500","rule":{"level":9,"description":"CIS Microsoft Windows 10 Enterprise Benchmark v1.12.0: Ensure 'Enforce password history' is set to '24 or more password(s)'.: Status changed from 'not applicable' to failed","id":"19014","firedtimes":1,"mail":false,"groups":["sca"],"gdpr":["IV_35.7.d"],"pci_dss":["2.2"],"nist_800_53":["CM.1"],"tsc":["CC7.1","CC7.2"],"cis":["1.1.1"],"cis_csc":["5.2"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930397.314282","decoder":{"name":"sca"},"data":{"sca":{"type":"check","scan_id":"221133515","policy":"CIS Microsoft Windows 10 Enterprise Benchmark v1.12.0","check":{"id":"15500","title":"Ensure 'Enforce password history' is set to '24 or more password(s)'.","description":"This policy setting determines the number of renewed, unique passwords that have to be associated with a user account before you can reuse an old password. The value for this policy setting must be between 0 and 24 passwords. The default value for Windows Vista is 0 passwords, but the default setting in a domain is 24 passwords. To maintain the effectiveness of this policy setting, use the Minimum password age setting to prevent users from repeatedly changing their password. The recommended state for this setting is: 24 or more password(s). Note: Password Policy settings (section 1.1) and Account Lockout Policy settings (section 1.2) must be applied via the Default Domain Policy GPO in order to be globally in effect on domain user accounts as their default behavior. If these settings are configured in another GPO, they will only affect local user accounts on the computers that receive the GPO. However, custom exceptions to the default password policy and account lockout policy rules for specific domain users and/or groups can be defined using Password Settings Objects (PSOs), which are completely separate from Group Policy and most easily configured using Active Directory Administrative Center. Note #2: As of the publication of this benchmark, Microsoft currently has a maximum limit of 24 saved passwords. For more information, please visit Enforce password history (Windows 10) - Windows security | Microsoft Docs","rationale":"The longer a user uses the same password, the greater the chance that an attacker can determine the password through brute force attacks. Also, any accounts that may have been compromised will remain exploitable for as long as the password is left unchanged. If password changes are required but password reuse is not prevented, or if users continually reuse a small number of passwords, the effectiveness of a good password policy is greatly reduced. If you specify a low number for this policy setting, users will be able to use the same small number of passwords repeatedly. If you do not also configure the Minimum password age setting, users might repeatedly change their passwords until they can reuse their original password.","remediation":"To establish the recommended configuration via GP, set the following UI path to 24 or more password(s): Computer 


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
> 1: {"timestamp":"2024-02-07T14:35:38.274+0500","rule":{"level":7,"description":"Host-based anomaly detection event (rootcheck).","id":"510","firedtimes":1,"mail":false,"groups":["ossec","rootcheck"],"pci_dss":["10.6.1"],"gdpr":["IV_35.7.d"]},"agent":{"id":"000","name":"socwazuh-virtual-machine"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707298538.0","full_log":"Trojaned version of file '/bin/diff' detected. Signature used: 'bash|^/bin/sh|file\\.h|proc\\.h|/dev/[^n]|^/bin/.*sh' (Generic).","decoder":{"name":"rootcheck"},"data":{"title":"Trojaned version of file detected.","file":"/bin/diff"},"location":"rootcheck"}


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
> {"timestamp":"2024-02-14T22:37:05.589+0500","rule":{"level":3,"description":"Application installed AccessData FTK Imager, 3.1.2.0, 1033, 0, AccessData.","id":"60612","firedtimes":2,"mail":false,"groups":["windows","windows_application"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707932225.385221","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"MsiInstaller","eventID":"1033","version":"0","level":"4","task":"0","opcode":"0","keywords":"0x80000000000000","systemTime":"2024-02-14T17:37:05.2607969Z","eventRecordID":"1583","processID":"0","threadID":"0","channel":"Application","computer":"DESKTOP-P79AUVL","severityValue":"INFORMATION","message":"\"Windows Installer installed the product. Product Name: AccessData FTK Imager. Product Version: 3.1.2.0. Product Language: 1033. Manufacturer: AccessData. Installation success or error status: 0.\""},"eventdata":{"binary":"7B30414443383334302D344139342D344345332D413732312D4235353846333635463844307D3030303038333465643839643534623833376339393763636630373832373639363935383030303030393034","data":"AccessData FTK Imager, 3.1.2.0, 1033, 0, AccessData"}}},"location":"EventChannel"}


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
> {"timestamp":"2024-02-14T22:02:34.461+0500","rule":{"level":7,"description":"Integrity checksum changed.","id":"550","mitre":{"id":["T1565.001"],"tactic":["Impact"],"technique":["Stored Data Manipulation"]},"firedtimes":1,"mail":false,"groups":["ossec","syscheck","syscheck_entry_modified","syscheck_file"],"pci_dss":["11.5"],"gpg13":["4.11"],"gdpr":["II_5.1.f"],"hipaa":["164.312.c.1","164.312.c.2"],"nist_800_53":["SI.7"],"tsc":["PI1.4","PI1.5","CC6.1","CC6.8","CC7.2","CC7.3"]},"agent":{"id":"000","name":"socwazuh-virtual-machine"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930154.2696","full_log":"File '/boot/efi/EFI/ubuntu/BOOTX64.CSV' modified\nMode: scheduled\nChanged attributes: inode\nOld inode was: '15', now it is '31'\n","syscheck":{"path":"/boot/efi/EFI/ubuntu/BOOTX64.CSV","mode":"scheduled","size_after":"108","perm_after":"rwx------","uid_after":"0","gid_after":"0","md5_after":"57f787de3cb850c0bbe040e2df1c80b5","sha1_after":"9f77c73907a0083f5b4b95d887ad217b7f0f05e7","sha256_after":"6add06de471015ad4460964f30fb115e7fdc286da6a527d0643fc7815b728fbf","uname_after":"root","gname_after":"root","mtime_after":"2024-02-05T23:59:40","inode_before":15,"inode_after":31,"changed_attributes":["inode"],"event":"modified"},"decoder":{"name":"syscheck_integrity_changed"},"location":"syscheck"}


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
>![123](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/d24595bb-b2c3-46c2-ab0c-c31287f5b5ef)
>
> Log:
>
> {"timestamp":"2024-02-16T22:51:16.979+0500","rule":{"level":5,"description":"License activation (slui.exe) failed.","id":"60646","firedtimes":1,"mail":false,"groups":["windows","windows_application"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1708105876.18105","decoder":{"name":"windows_eventchannel"},"data":{"win":{"system":{"providerName":"Microsoft-Windows-Security-SPP","providerGuid":"{E23B33B0-C8C9-472C-A5F9-F2BDFEA0F156}","eventSourceName":"Software Protection Platform Service","eventID":"8198","version":"0","level":"2","task":"0","opcode":"0","keywords":"0x80000000000000","systemTime":"2024-02-16T17:51:07.4746785Z","eventRecordID":"1626","processID":"0","threadID":"0","channel":"Application","computer":"DESKTOP-P79AUVL","severityValue":"ERROR","message":"\"License Activation (slui.exe) failed with the following error code:\r\nhr=0x803F7001\r\nCommand-line arguments:\r\nRuleId=31e71c49-8da7-4a2f-ad92-45d98a1c79ba;Action=AutoActivate;AppId=55c92734-d682-4d71-983e-d6ec3f16059f;SkuId=4de7cb65-cdf1-4de9-8ae8-e3cce27b9f2c;NotificationInterval=1440;Trigger=TimerEvent\""},"eventdata":{"data":"hr=0x803F7001, RuleId=31e71c49-8da7-4a2f-ad92-45d98a1c79ba;Action=AutoActivate;AppId=55c92734-d682-4d71-983e-d6ec3f16059f;SkuId=4de7cb65-cdf1-4de9-8ae8-e3cce27b9f2c;NotificationInterval=1440;Trigger=TimerEvent"}}},"location":"EventChannel"}

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
> {"timestamp":"2024-02-14T22:02:42.127+0500","rule":{"level":7,"description":"Integrity checksum changed.","id":"550","mitre":{"id":["T1565.001"],"tactic":["Impact"],"technique":["Stored Data Manipulation"]},"firedtimes":3,"mail":false,"groups":["ossec","syscheck","syscheck_entry_modified","syscheck_file"],"pci_dss":["11.5"],"gpg13":["4.11"],"gdpr":["II_5.1.f"],"hipaa":["164.312.c.1","164.312.c.2"],"nist_800_53":["SI.7"],"tsc":["PI1.4","PI1.5","CC6.1","CC6.8","CC7.2","CC7.3"]},"agent":{"id":"000","name":"socwazuh-virtual-machine"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930162.6437","full_log":"File '/etc/init.d/vmware-tools' modified\nMode: scheduled\nChanged attributes: inode,mtime\nOld modification time was: '1707205016', now it is '1707324720'\nOld inode was: '2359469', now it is '2359796'\n","syscheck":{"path":"/etc/init.d/vmware-tools","mode":"scheduled","size_after":"45893","perm_after":"rwxr-xr-x","uid_after":"0","gid_after":"0","md5_after":"ff8ad3b57d9ae079a7e5c8fd521b540c","sha1_after":"c828705139d88c2675db11947fcfda249c556053","sha256_after":"a99fc063cdfa3e5bf25118f6af0e434a3727ad53a99dee91321fe207a6172715","uname_after":"root","gname_after":"root","mtime_before":"2024-02-06T12:36:56","mtime_after":"2024-02-07T21:52:00","inode_before":2359469,"inode_after":2359796,"changed_attributes":["inode","mtime"],"event":"modified"},"decoder":{"name":"syscheck_new_entry"},"location":"syscheck"}

> Question 10: Name the modiﬁed ﬁlewithin the Ubuntu system. (Answer
> format: CSL{ﬁlename})
>
> Answer: CSL{grub.cfg}
>
> File: ossec-alerts-14.json
>
> Method:
> {"timestamp":"2024-02-14T22:02:34.859+0500","rule":{"level":7,"description":"Integrity checksum changed.","id":"550","mitre":{"id":["T1565.001"],"tactic":["Impact"],"technique":["Stored Data Manipulation"]},"firedtimes":2,"mail":false,"groups":["ossec","syscheck","syscheck_entry_modified","syscheck_file"],"pci_dss":["11.5"],"gpg13":["4.11"],"gdpr":["II_5.1.f"],"hipaa":["164.312.c.1","164.312.c.2"],"nist_800_53":["SI.7"],"tsc":["PI1.4","PI1.5","CC6.1","CC6.8","CC7.2","CC7.3"]},"agent":{"id":"000","name":"socwazuh-virtual-machine"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930154.3469","full_log":"File '/boot/efi/EFI/ubuntu/grub.cfg' modified\nMode: scheduled\nChanged attributes: inode\nOld inode was: '16', now it is '32'\n","syscheck":{"path":"/boot/efi/EFI/ubuntu/grub.cfg","mode":"scheduled","size_after":"126","perm_after":"rwx------","uid_after":"0","gid_after":"0","md5_after":"fd5c645ff5612a311d7ae0bb726e50a0","sha1_after":"64644dfa3d8b785cb23cb9943f7c02d77959a664","sha256_after":"b4790638ef11283284c3914d82b1940fe41d4e136480314444eb754377c0c529","uname_after":"root","gname_after":"root","mtime_after":"2024-02-05T23:59:40","inode_before":16,"inode_after":32,"changed_attributes":["inode"],"event":"modified"},"decoder":{"name":"syscheck_integrity_changed"},"location":"syscheck"}
