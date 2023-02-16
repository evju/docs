---
title: Windows
---

# :fontawesome-brands-windows:


## Command Prompt

The Microsoft Command Prompt, also known as cmd, is a powerful tool that is an essential part of the Microsoft operating system. This command-line interface allows users to perform tasks such as executing programs, viewing and manipulating files, and performing system management tasks. Unlike graphical user interfaces (GUIs), which rely on graphical elements and menus, the Command Prompt uses a line-by-line interface and text-based commands to perform tasks. This means that users must type out the commands they want to execute, rather than clicking on graphical buttons.

[CMD Documentation](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cmd) |  <span style="font-size:14px">"Microsoft Docs"</span>

---

### Find IP Address

=== "ipconfig"

    ```yaml
    C:\Windows\System32>ipconfig

    Windows IP Configuration

    Ethernet adapter Ethernet:

    Connection-specific DNS Suffix  . :
    Link-local IPv6 Address . . . . . : fe80::583b:70a1:34f1:49c2%22
    IPv4 Address. . . . . . . . . . . : 192.168.11.109
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . . : 192.168.11.1
    ```

=== "ipconfig /all"

    ```yaml
    C:\Windows\System32>ipconfig /all

    Windows IP Configuration

    Host Name . . . . . . . . . . . . : Example
    Primary Dns Suffix  . . . . . . . :
    Node Type . . . . . . . . . . . . : Hybrid
    IP Routing Enabled. . . . . . . . : No
    WINS Proxy Enabled. . . . . . . . : No

    Ethernet adapter Ethernet:

    Connection-specific DNS Suffix  . :
    Description . . . . . . . . . . . : Example Controller
    Physical Address. . . . . . . . . : A8-A1-59-34-27-60
    DHCP Enabled. . . . . . . . . . . : Yes
    Autoconfiguration Enabled . . . . : Yes
    Link-local IPv6 Address . . . . . : fe80::583b:70a1:34f1:49c2%22(Preferred)
    IPv4 Address. . . . . . . . . . . : 192.168.11.109(Preferred)
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Lease Obtained. . . . . . . . . . : Wednesday, February 8, 2023 17:04:02
    Lease Expires . . . . . . . . . . : Thursday, February 9, 2023 06:29:37
    Default Gateway . . . . . . . . . : 192.168.11.1
    DHCP Server . . . . . . . . . . . : 192.168.11.1
    DHCPv6 IAID . . . . . . . . . . . : 111714649
    DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-29-C6-EE-49-A8-A1-59-34-27-60
    DNS Servers . . . . . . . . . . . : 1.1.1.1
    NetBIOS over Tcpip. . . . . . . . : Enabled
    ```

=== "ipconfig /all | findstr IPv4"

    ``` yaml
    C:\Windows\System32>ipconfig /all | findstr IPv4 # (1)!

    IPv4 Address. . . . . . . . . . . : 192.168.11.109(Preferred)
    ```

    1.  findstr = find string. Removes unwanted information.


### Get a new IP Address

=== "ipconfig /release"

    ```yaml
    C:\Windows\System32>ipconfig /release

    Windows IP Configuration

    Ethernet adapter Ethernet:

    Connection-specific DNS Suffix  . :
    Link-local IPv6 Address . . . . . : fe80::583b:70a1:34f1:49c2%22
    Default Gateway . . . . . . . . . :
    ```

=== "ipconfig /renew"

    ```yaml
    C:\Windows\System32>ipconfig /renew

    Windows IP Configuration

    Ethernet adapter Ethernet:

    Connection-specific DNS Suffix  . :
    Link-local IPv6 Address . . . . . : fe80::583b:70a1:34f1:49c2%22
    IPv4 Address. . . . . . . . . . . : 192.168.11.110
    Subnet Mask . . . . . . . . . . . : 255.255.255.0
    Default Gateway . . . . . . . . . : 192.168.11.1
    ```


<br>

## PowerShell

PowerShell is a powerful scripting and automation tool that is part of the Microsoft Windows operating system. This command-line interface provides users with an efficient and flexible way to manage and automate various aspects of the Windows environment, including system administration, software deployment, and system automation. Unlike Command Prompt, which uses text-based commands, PowerShell uses a combination of text-based commands and a rich scripting language to perform tasks. This allows users to automate complex tasks and perform tasks more efficiently than they could using the Command Prompt.

[PowerShell Documentation](https://learn.microsoft.com/en-us/powershell/) |  Microsoft Docs

---

### Bulk-rename files


```powershell
get-childitem *.file | ForEach { Move-Item -LiteralPath $_.name $_.name.Replace("[xyz]","[abc]")}
```

??? Warning "Renames all files in the current folder with the .file extention from [xyz] to [abc]"
