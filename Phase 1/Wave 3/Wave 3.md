# Wave 3
## Question 1
> Which malicious ﬁlewas downloaded by the user? (Format: CSL{ﬁlename.extention})
>
> Answer: CSL{Rhysida.zip}
>
> ![2](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/408de16e-2d12-417d-8948-beafe4f87e8f)

## Question 2
> What is the identiﬁer of the network interface associated with this capture?
>
> Answer: CSL{5921D940-52C4-4076-A7F7-351C583EC5B7}
>
> ![3](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/e76953cb-aedd-442c-ad0f-1e8a9bc7709e)

## Question 3
> After its launch, Tor.exe initiated which executable and what is its Process ID (PID)? (Format: CSL{ﬁlename_PID})
>
> Answer: CSL{Conhost.exe_4644}
>
> File: LogFile.PML
>
> Method: Filter process name as tor.exe, then open the process tree from Tools and look for what process it initiated along with its PID.
>![4](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/e5c0e445-7842-4288-9cbb-f8564e9485d2)

## Question 4
> What was the timestamp when gpapi.dll got extracted? (Format: (Format: CSL{DD/MM/YYYY_HH:MM:SS})
>
> Answer: CSL{02/29/1980_06:06:58}
> ![5](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/b8f2ecec-1721-4491-9077-63e6726c4516)

## Question 5
> Identify the executable that exploited bcrypt.dll.(Format: CSL{ﬁlename})
>
> Answer: CSL{Articbomb.exe}
>
> File: LogFIle.PML
>
> Method: Look for any process that seems malicious in a normal environment and look if it is using bcrypt.dll for encryption purposes.
>![6](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/bf500b8a-eedf-440d-bc86-30c9ea6f6553)

## Question 6
> A malicious actor generated aﬁle, subsequently utilized in an attack. (Format: CSL{ﬁlename})
>
> Answer: CSL{ Imm32.dll}
>
> File: LogFIle.PML
>
> Method:
> ![7](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/7ceda4dd-dff2-4719-abe8-3f2d3400af6f)

## Question 7
> Identify the legitimate executable utilized by the threat actor to alter their identity. (Format: CSL{ﬁlename})
>
> Answer: CSL{ BackgroundTaskHost.exe}
> ![8](https://github.com/TrojanNinja/Nascon-24-CTF/assets/100431785/cf2707b5-2ede-43b2-9a53-dc3ba7f61be0)

