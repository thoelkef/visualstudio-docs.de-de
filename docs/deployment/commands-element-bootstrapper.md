---
title: '&lt;Befehle&gt; Element (Bootstrapper) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 67bbb7cbec1df53a8481acf26273cc371f92bb40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Befehle&gt; Element (Bootstrapper)
Die `Commands` Element implementiert Tests, die durch die Elemente beschrieben die `InstallChecks` Element, und welches Paket deklariert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bootstrapper sollten installiert werden, wenn der Test fehlschlägt.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `Commands` Element ist erforderlich. Das Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Reboot`|Dies ist optional. Bestimmt, ob das System neu starten soll, wenn eines der Pakete ein Neustart-Exitcode zurückgegeben. Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Defer` Der Neustart wird verzögert, bis zu einem späteren Zeitpunkt.<br /><br /> `Immediate` Führt einen sofortigen Neustart, wenn eines der Pakete einen Neustart-Exitcode zurückgegeben.<br /><br /> `None` Bewirkt, dass alle Anforderungen Neustart, ignoriert werden sollen.<br /><br /> Die Standardeinstellung ist `Immediate`.|  
  
## <a name="command"></a>Befehl  
 Das `Command`-Element ist ein untergeordnetes Element des `Commands`-Elements. Ein `Commands` Element haben eine oder mehrere `Command` Elemente. Das Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`PackageFile`|Erforderlich. Der Name des zu installierenden Pakets sollte mindestens eine der Bedingungen gemäß `InstallConditions` "false" zurückgeben. Das Paket muss in derselben Datei definiert werden, mithilfe einer `PackageFile` Element.|  
|`Arguments`|Dies ist optional. Ein Satz von Befehlszeilenargumenten, die an die Paketdatei übergeben.|  
|`EstimatedInstallSeconds`|Dies ist optional. Die geschätzte Zeit in Sekunden, dauert es zum Installieren des Pakets. Dieser Wert bestimmt die Größe der Statusanzeige, die der Bootstrapper, an den Benutzer angezeigt. Der Standardwert ist 0 (null) in diesem Fall keine Uhrzeit Schätzung angegeben wird.|  
|`EstimatedDiskBytes`|Dies ist optional. Der geschätzte Umfang der Speicherplatz in Bytes, der belegt das Paket nach der Installation ist abgeschlossen. Dieser Wert ist in Anforderungen an den Festplattenspeicherplatz verwendet, die der Bootstrapper dem Benutzer angezeigt. Der Standardwert ist 0 (null) und in der der Bootstrapper alle Anforderungen an den Festplattenspeicherplatz nicht angezeigt wird.|  
|`EstimatedTempBytes`|Dies ist optional. Der geschätzte Umfang an Speicherplatz in Bytes, der das Paket benötigen.|  
|`Log`|Dies ist optional. Der Pfad zur Protokolldatei, die das Paket generiert wird, relativ zum Stammverzeichnis des Pakets.|  
  
## <a name="installconditions"></a>InstallConditions  
 Die `InstallConditions` Element ist ein untergeordnetes Element von der `Command` Element. Jede `Command` Element kann höchstens eine haben `InstallConditions` Element. Wenn kein `InstallConditions` Element vorhanden ist, das Paket vom angegebenen `Condition` wird immer ausgeführt.  
  
## <a name="bypassif"></a>BypassIf  
 Die `BypassIf` Element ist ein untergeordnetes Element von der `InstallConditions` -Element, und beschreibt eine positive Bedingung, unter dem der Befehl nicht ausgeführt werden sollte. Jede `InstallConditions` haben Element 0 (null) oder mehrere `BypassIf` Elemente.  
  
 `BypassIf`verfügt über die folgenden Attribute aus.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der zu überprüfenden Eigenschaft. Die Eigenschaft muss zuvor definiert wurden durch ein untergeordnetes Element von der `InstallChecks` Element. Weitere Informationen finden Sie unter [ \<InstallChecks >-Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Erforderlich. Der Typ des auszuführenden Vergleichs an. Die folgende Liste zeigt die gültigen Werte:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Erforderlich. Der Wert, mit der Eigenschaft verglichen werden soll.|  
|`Schedule`|Dies ist optional. Der Name des eine `Schedule` Tags, das definiert, wann diese Regel ausgewertet werden sollen.|  
  
## <a name="failif"></a>FailIf  
 Die `FailIf` Element ist ein untergeordnetes Element von der `InstallConditions` -Element, und beschreibt eine positive Bedingung, unter denen die Installation beendet werden soll. Jede `InstallConditions` haben Element 0 (null) oder mehrere `FailIf` Elemente.  
  
 `FailIf`verfügt über die folgenden Attribute aus.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der zu überprüfenden Eigenschaft. Die Eigenschaft muss zuvor definiert wurden durch ein untergeordnetes Element von der `InstallChecks` Element. Weitere Informationen finden Sie unter [ \<InstallChecks >-Element](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Erforderlich. Der Typ des auszuführenden Vergleichs an. Die folgende Liste zeigt die gültigen Werte:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Erforderlich. Der Wert, mit der Eigenschaft verglichen werden soll.|  
|`String`|Dies ist optional. Der Text, der Benutzer bei einem Fehler angezeigt.|  
|`Schedule`|Dies ist optional. Der Name des eine `Schedule` Tags, das definiert, wann diese Regel ausgewertet werden sollen.|  
  
## <a name="exitcodes"></a>ExitCodes  
 Die `ExitCodes` Element ist ein untergeordnetes Element von der `Command` Element. Die `ExitCodes` Element enthält eine oder mehrere `ExitCode` Elemente, die bestimmen, was die Installation als Antwort auf einen Exitcode von einem Paket ausführen soll. Es kann eine optionale `ExitCode` Element unterhalb einer `Command` Element. `ExitCodes`weist keine Attribute.  
  
## <a name="exitcode"></a>exitCode  
 Die `ExitCode` Element ist ein untergeordnetes Element von der `ExitCodes` Element. Die `ExitCode` Element bestimmt, was die Installation als Antwort auf einen Exitcode von einem Paket tun sollten. `ExitCode`enthält keine untergeordneten Elemente und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Value`|Erforderlich. Den Exitcodewert, der diese `ExitCode` Element angewendet wird.|  
|`Result`|Erforderlich. Wie die Installation auf diesen Exitcode reagieren soll. Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Success` Kennzeichnet das Paket als erfolgreich installiert.<br /><br /> `SuccessReboot` Kennzeichnet das Paket als erfolgreich installiert, und weist das System neu starten.<br /><br /> `Fail` Kennzeichnet das Paket aus, als fehlgeschlagen eingestuft.<br /><br /> `FailReboot` Kennzeichnet das Paket als fehlgeschlagen eingestuft, und weist das System neu starten.|  
|`String`|Dies ist optional. Der Wert für den Benutzer als Antwort auf diese Exitcode anzuzeigen.|  
|`FormatMessageFromSystem`|Dies ist optional. Bestimmt, ob die vom System bereitgestellte Fehlermeldung für den Exitcode, oder verwenden Sie den Wert im bereitgestellten `String`. Gültige Werte sind `true`, was bedeutet den Fehler vom System bereitgestellte verwenden und `false`, d. h., die vom bereitgestellten Zeichenfolge verwenden `String`. Die Standardeinstellung ist `false`. Wenn diese Eigenschaft ist `false`, aber `String` ist nicht festgelegt ist, wird der Fehler vom System bereitgestellte verwendet werden.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel definiert die Befehle zum Installieren von .NET Framework 2.0.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Produkt- und Paketschemareferenz](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks >-Element](../deployment/installchecks-element-bootstrapper.md)