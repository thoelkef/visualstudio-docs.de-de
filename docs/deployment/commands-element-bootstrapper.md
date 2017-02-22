---
title: "&lt;Commands&gt;-Element (Bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Commands>-Element [Bootstrapper]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;Commands&gt;-Element (Bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das `Commands`\-Element implementiert Tests, die durch die Elemente beschrieben werden, die dem `InstallChecks`\-Element untergeordnet sind. Ferner deklariert es das Paket, das der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bootstrapper installieren soll, falls der Test negativ ausfällt.  
  
## Syntax  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## Elemente und Attribute  
 Das `Commands`\-Element ist erforderlich.  Das Element verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Reboot`|Optional.  Bestimmt, ob das System neu gestartet werden soll, wenn Pakete einen Neustartexitcode zurückgeben.  Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Defer`.  Der Neustart wird bis zu einem späteren Zeitpunkt verzögert.<br /><br /> `Immediate`.  Bewirkt einen unmittelbaren Neustart, wenn eines der Pakete einen Neustartexitcode zurückgibt.<br /><br /> `None`.  Bewirkt, dass Neustartanforderungen ignoriert werden.<br /><br /> Der Standardwert ist `Immediate`.|  
  
## Befehl  
 Das `Command`\-Element ist ein untergeordnetes Element des `Commands`\-Elements.  Ein `Commands`\-Element kann über ein oder mehrere `Command`\-Elemente verfügen.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`PackageFile`|Erforderlich.  Der Name des Pakets, das installiert werden soll, wenn eine oder mehrere der durch `InstallConditions` angegebenen Bedingungen false zurückgeben.  Das Paket muss in derselben Datei mit einem `PackageFile`\-Element definiert werden.|  
|`Arguments`|Optional.  Befehlszeilenargumente, die an die Paketdatei übergeben werden sollen.|  
|`EstimatedInstallSeconds`|Optional.  Der geschätzte Zeitaufwand für die Installation des Pakets in Sekunden.  Dieser Wert bestimmt die Größe der Statusanzeige, die der Bootstrapper dem Benutzer anzeigt.  Der Standardwert ist 0 \(null\), d. h., es wird keine Zeitschätzung angegeben.|  
|`EstimatedDiskBytes`|Optional.  Der geschätzte Speicherplatz in Bytes, den das Paket nach Abschluss der Installation einnehmen wird.  Dieser Wert bestimmt den erforderlichen Festplattenspeicher, den der Bootstrapper dem Benutzer anzeigt.  Der Standardwert ist 0 \(null\), d. h., der Bootstrapper zeigt keinen erforderlichen Festplattenspeicher an.|  
|`EstimatedTempBytes`|Optional.  Der geschätzte, für das Paket erforderliche temporäre Speicherplatz in Bytes.|  
|`Log`|Optional.  Der Pfad der durch das Paket generierten Protokolldatei, relativ zum Stammverzeichnis des Pakets.|  
  
## InstallConditions  
 Das `InstallConditions`\-Element ist ein untergeordnetes Element des `Command`\-Elements.  Jedes `Command`\-Element kann über höchstens ein `InstallConditions`\-Element verfügen.  Wenn kein `InstallConditions`\-Element vorhanden ist, wird immer das durch `Condition` angegebene Paket ausgeführt.  
  
## BypassIf  
 Das `BypassIf`\-Element ist ein untergeordnetes Element des `InstallConditions`\-Elements. Es beschreibt eine positive Bedingung, bei deren Erfüllung der Befehl nicht ausgeführt werden soll.  Jedes `InstallConditions`\-Element kann über null oder mehr `BypassIf`\-Elemente verfügen.  
  
 `BypassIf` verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der zu testenden Eigenschaft.  Die Eigenschaft muss zuvor durch ein untergeordnetes Element des `InstallChecks`\-Elements definiert worden sein.  Weitere Informationen hierzu finden Sie unter [\<InstallChecks\>\-Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Erforderlich.  Der Typ des auszuführenden Vergleichs.  Die folgende Liste zeigt die gültigen Werte:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Erforderlich.  Der Wert, der mit der Eigenschaft verglichen werden soll.|  
|`Schedule`|Optional.  Der Name eines `Schedule`\-Tags, das definiert, wann diese Regel ausgewertet werden soll.|  
  
## FailIf  
 Das `FailIf`\-Element ist ein untergeordnetes Element des `InstallConditions`\-Elements. Es beschreibt eine positive Bedingung, bei deren Erfüllung die Installation angehalten werden soll.  Jedes `InstallConditions`\-Element kann über null oder mehr `FailIf`\-Elemente verfügen.  
  
 `FailIf` verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der zu testenden Eigenschaft.  Die Eigenschaft muss zuvor durch ein untergeordnetes Element des `InstallChecks`\-Elements definiert worden sein.  Weitere Informationen hierzu finden Sie unter [\<InstallChecks\>\-Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Erforderlich.  Der Typ des auszuführenden Vergleichs.  Die folgende Liste zeigt die gültigen Werte:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Erforderlich.  Der Wert, der mit der Eigenschaft verglichen werden soll.|  
|`String`|Optional.  Der Text, der dem Benutzer bei einem Fehler angezeigt werden soll.|  
|`Schedule`|Optional.  Der Name eines `Schedule`\-Tags, das definiert, wann diese Regel ausgewertet werden soll.|  
  
## ExitCodes  
 Das `ExitCodes`\-Element ist ein untergeordnetes Element des `Command`\-Elements.  Das `ExitCodes`\-Element enthält mindestens ein `ExitCode`\-Element, das bestimmt, wie die Installation auf einen Exitcode eines Pakets reagieren soll.  Unter einem `Command`\-Element kann sich ein optionales `ExitCode`\-Element befinden.  `ExitCodes` verfügt über keine Attribute.  
  
## ExitCode  
 Das `ExitCode`\-Element ist ein untergeordnetes Element des `ExitCodes`\-Elements.  Das `ExitCode`\-Element bestimmt, wie die Installation auf einen Exitcode aus einem Paket reagieren soll.  `ExitCode` enthält keine untergeordneten Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Value`|Erforderlich.  Der Exitcodewert für dieses `ExitCode`\-Element.|  
|`Result`|Erforderlich.  Gibt an, wie die Installation auf diesen Exitcode reagieren soll.  Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Success`.  Kennzeichnet das Paket als erfolgreich installiert.<br /><br /> `SuccessReboot`.  Kennzeichnet das Paket als erfolgreich installiert und weist das System an, neu zu starten.<br /><br /> `Fail`.  Kennzeichnet das Paket als fehlgeschlagen.<br /><br /> `FailReboot`.  Kennzeichnet das Paket als fehlgeschlagen und weist das System an, neu zu starten.|  
|`String`|Optional.  Der Wert, der dem Benutzer als Reaktion auf diesen Exitcode angezeigt werden soll.|  
|`FormatMessageFromSystem`|Optional.  Bestimmt, ob die vom System bereitgestellte Fehlermeldung für den Exitcode oder der in `String` bereitgestellte Wert verwendet wird.  Gültige Werte sind `true` \(Verwendung der vom System bereitgestellten Fehlermeldung\) und `false` \(Verwendung der durch `String` bereitgestellten Zeichenfolge\).  Der Standardwert ist `false.` Wenn diese Eigenschaft den Wert `false` hat, `String` jedoch nicht festgelegt ist, wird die vom System bereitgestellte Fehlermeldung verwendet.|  
  
## Beispiel  
 Im folgenden Codebeispiel werden Befehle für die Installation von .NET Framework 2.0 definiert.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks\>\-Element](../deployment/installchecks-element-bootstrapper.md)