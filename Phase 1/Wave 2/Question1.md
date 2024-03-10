# Wave 2
## Question 1:
> Which registry value integrity checksum change was detected in the W32Time service? (Format: CSL{valueName})
>
> Answer: CSL{SecureTimeLow}
>
> File: ossec-alerts-14.json
>
> Method: Start searching W32Time in ossec logs and look for registry value integrity checksum changed log and note the value that was changed in the event full_log and you will get the exact value that was modiﬁed in the registry.
>
> Log:
>
> {"timestamp":"2024-02-14T22:06:18.736+0500","rule":{"level":5,"description":"Registry Value Integrity Checksum Changed","id":"750","mitre":{"id":["T1565.001","T1112"],"tactic":["Impact","Defense Evasion"],"technique":["Stored Data Manipulation","Modify Registry"]},"firedtimes":16,"mail":false,"groups":["ossec","syscheck","syscheck_entry_modified","syscheck_registry"],"pci_dss":["11.5"],"gpg13":["4.13"],"gdpr":["II_5.1.f"],"hipaa":["164.312.c.1","164.312.c.2"],"nist_800_53":["SI.7"],"tsc":["PI1.4","PI1.5","CC6.1","CC6.8","CC7.2","CC7.3"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930378.293912","full_log":"Registry Value '[x32] HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Services\\W32Time\\SecureTimeLimits\\SecureTimeLow' modified\nMode: scheduled\nChanged attributes: md5,sha1,sha256\nOld md5sum was: '2318d41e07825337556aa533478be005'\nNew md5sum is : '77b97c4f02ffcc200dbcdbcf39059f4c'\nOld sha1sum was: '5e7b48ae86109e02046ec5d374e0855fa76dbf90'\nNew sha1sum is : 'e08b737b166db3519098dd29345479d935fe2998'\nOld sha256sum was: '2889c0a6d63eb56f7a20a27b5a9a7f9ac64e7b74ee24126563f136211df6fa14'\nNew sha256sum is : 'd62dab43fc5de05e7480e696bf65ff8dbf053cbf19cb72f7f4a967fc4d89e45a'\n","syscheck":{"path":"HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Services\\W32Time\\SecureTimeLimits","mode":"scheduled","arch":"[x32]","value_name":"SecureTimeLow","value_type":"REG_QWORD","size_after":"8","md5_before":"2318d41e07825337556aa533478be005","md5_after":"77b97c4f02ffcc200dbcdbcf39059f4c","sha1_before":"5e7b48ae86109e02046ec5d374e0855fa76dbf90","sha1_after":"e08b737b166db3519098dd29345479d935fe2998","sha256_before":"2889c0a6d63eb56f7a20a27b5a9a7f9ac64e7b74ee24126563f136211df6fa14","sha256_after":"d62dab43fc5de05e7480e696bf65ff8dbf053cbf19cb72f7f4a967fc4d89e45a","changed_attributes":["md5","sha1","sha256"],"event":"modified"},"decoder":{"name":"syscheck_registry_value_modified"},"location":"syscheck"}

## Question 2:
> What is the name of the user mode service that had its registry key modiﬁed? (Format: CSL{serviceName})
>
> Answer: CSL{bam}
>
> File: ossec-alerts-14.json
>
> Method:
>
> {"timestamp":"2024-02-14T22:06:01.209+0500","rule":{"level":5,"description":"Registry Value Integrity Checksum Changed","id":"750","mitre":{"id":["T1565.001","T1112"],"tactic":["Impact","Defense Evasion"],"technique":["Stored Data Manipulation","Modify Registry"]},"firedtimes":1,"mail":false,"groups":["ossec","syscheck","syscheck_entry_modified","syscheck_registry"],"pci_dss":["11.5"],"gpg13":["4.13"],"gdpr":["II_5.1.f"],"hipaa":["164.312.c.1","164.312.c.2"],"nist_800_53":["SI.7"],"tsc":["PI1.4","PI1.5","CC6.1","CC6.8","CC7.2","CC7.3"]},"agent":{"id":"001","name":"Employee1","ip":"192.168.23.3"},"manager":{"name":"socwazuh-virtual-machine"},"id":"1707930361.228338","full_log":"Registry Value '[x32] HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Services\\bam\\State\\UserSettings\\S-1-5-21-1572141609-1480394228-1013454401-1001\\SequenceNumber' modified\nMode: scheduled\nChanged attributes: md5,sha1,sha256\nOld md5sum was: 'df512eeeb534603f898c6239f2cd2917'\nNew md5sum is : '770b5505bab85eb2e2b4793da0a4fa11'\nOld sha1sum was: '55c21b19cbc1e08e9eb3d94247b5f0abec618485'\nNew sha1sum is : '6db82df400e40b4910ffaf507cf446ed8c69f161'\nOld sha256sum was: 'c1f739acdf29f741077d4e9141607de09212ad7656b9757e410b84d01cded607'\nNew sha256sum is : '708cd84bf319f7785f77388abe094cc19136fc25f6878e950f6cabe630e79a7b'\n","syscheck":{"path":"HKEY_LOCAL_MACHINE\\System\\CurrentControlSet\\Services\\bam\\State\\UserSettings\\S-1-5-21-1572141609-1480394228-1013454401-1001","mode":"scheduled","arch":"[x32]","value_name":"SequenceNumber","value_type":"REG_DWORD","size_after":"4","md5_before":"df512eeeb534603f898c6239f2cd2917","md5_after":"770b5505bab85eb2e2b4793da0a4fa11","sha1_before":"55c21b19cbc1e08e9eb3d94247b5f0abec618485","sha1_after":"6db82df400e40b4910ffaf507cf446ed8c69f161","sha256_before":"c1f739acdf29f741077d4e9141607de09212ad7656b9757e410b84d01cded607","sha256_after":"708cd84bf319f7785f77388abe094cc19136fc25f6878e950f6cabe630e79a7b","changed_attributes":["md5","sha1","sha256"],"event":"modified"},"decoder":{"name":"syscheck_registry_value_modified"},"location":"syscheck"}

## Question 3:
> What is the machine type identiﬁer discovered during the memory dump analysis of the Tor session? (Format: CSL{MachineType})
>
> Answer: CSL{34404}
>
> File: memdump.mem
>
> Method: Open .mem ﬁle in memory dump analysis tool like volatility. Start by listing processes and go to windows.info.info and look for machinetype ﬁeld:
>
![1](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/29ba564c-c952-4b16-9243-ee5dfbd97c36)
![2](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/c3e2f44c-e363-4cff-afbd-fac77185dc9a)

## Question 4:
> What is the o set for the user's ﬁle, where "UsmanNaeem" is the username? (Format: CSL{o set})
>
> Answer:CSL{0xa58bcb6ed000}
>
> File: Memdump.mem
>
![3](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/1f353062-1aaa-4583-b783-b56e79aa0441)
![4](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/07a3d94d-2db1-46de-ab2a-e2b632a2900c)

## Question 5:
> What is the operating system and the number of processors of the computer where FTK Imager.exe was executed? (Format: CSL{OS_processorCount})
>
> Answer: CSL{Windows_NT_2}
>
> File: Memdump.mem
>
> Command Info:
![5](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/cb04f8b8-c8e0-4f7e-afb3-36c4c8c2a32c)
![6](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/78ff1896-9d1c-4a38-ac4a-3d550dbf032c)

## Question 6:
> what is ﬁle hash of WMIPRVSE.EXE? (Format: CSL{hash})
>
> Answer: CSL{E8B8DD29}
> Method: 
![7](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/c11d244f-7761-45c1-8171-0c63c4f8993e)
![8](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/d5676e8d-18f4-4a2e-853b-85d24ed9295a)

## Question 7:
> When is CMD.EXE last run time? (Format: CSL{DD/MM/YYYY_HH:MM:SS})
>
> Answer: CSL{28/02/2024_12:48:58}

## Question 8:
> How many times does REG.EXE executed? (Format: CSL{times})
>
> Answer: CSL{12}
![9](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/aa482834-0b4b-4efa-a929-bee7100dfc7e)
