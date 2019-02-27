---
title: '&lt;Befehle&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f52c862adcdaf7a95de6a90c2c330c39edcea13
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598505"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Befehle&gt; -Element (Bootstrapper)
Die `Commands` Element implementiert, Tests, die durch die Elemente beschrieben die `InstallChecks` -Element, und welches Paket deklariert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bootstrapper sollten installiert werden, wenn der Test fehlschlägt.

## <a name="syntax"></a>Syntax

```xml
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
 Die `Commands` Element ist erforderlich. Das Element weist das folgende Attribut auf.

|Attribut|Beschreibung|
|---------------|-----------------|
|`Reboot`|Dies ist optional. Bestimmt, ob das System neu starten soll, wenn keines der Pakete einen Neustart-Exitcode zurückgeben. Die folgende Liste zeigt die gültigen Werte an:<br /><br /> `Defer`. Der Neustart wird verzögert, bis zu einem späteren Zeitpunkt.<br /><br /> `Immediate`. Führt einen sofortigen Neustart, wenn eines der Pakete einen Neustart-Exitcode zurückgegeben.<br /><br /> `None`. Bewirkt, dass alle Anforderungen Neustart ignoriert werden soll.<br /><br /> Die Standardeinstellung ist `Immediate`.|

## <a name="command"></a>Befehl
 Das `Command`-Element ist ein untergeordnetes Element des `Commands`-Elements. Ein `Commands` Element haben eine oder mehrere `Command` Elemente. Das Element weist folgende Attribute auf.

|Attribut|Beschreibung|
|---------------|-----------------|
|`PackageFile`|Erforderlich. Der Name des zu installierenden Pakets sollte mindestens eine der Bedingungen gemäß `InstallConditions` "false" zurückgegeben. Das Paket muss in derselben Datei definiert werden, mithilfe einer `PackageFile` Element.|
|`Arguments`|Dies ist optional. Ein Satz von Befehlszeilenargumenten, die Paketdatei übergeben.|
|`EstimatedInstallSeconds`|Dies ist optional. Die geschätzte Zeit in Sekunden, dauert es, um das Paket installieren zu können. Dieser Wert bestimmt die Größe der Statusanzeige, die der Bootstrapper, die dem Benutzer angezeigt. Der Standardwert ist 0 (null) in diesem Fall keine Zeit, die Schätzung angegeben wird.|
|`EstimatedDiskBytes`|Dies ist optional. Die geschätzte Dauer des Speicherplatzes in Bytes, die das Paket nach der Installation belegt wird, ist abgeschlossen. Dieser Wert wird in den Anforderungen an den Festplattenspeicherplatz verwendet, in der der Bootstrapper, die dem Benutzer angezeigt. Der Standardwert ist 0 (null) und in der der Bootstrapper alle erforderlichen Festplattenspeicherplatz nicht angezeigt wird.|
|`EstimatedTempBytes`|Dies ist optional. Die geschätzte Dauer des temporären Speicherplatzes, in Bytes, die das Paket benötigen.|
|`Log`|Dies ist optional. Der Pfad zur Protokolldatei, die das Paket generiert wird, relativ zum Stammverzeichnis des Pakets.|

## <a name="installconditions"></a>InstallConditions
 Die `InstallConditions` Element ist ein untergeordnetes Element des der `Command` Element. Jede `Command` Element kann höchstens ein verfügen `InstallConditions` Element. Wenn kein `InstallConditions` Element vorhanden ist, das angegebene Paket `Condition` wird immer ausgeführt.

## <a name="bypassif"></a>BypassIf
 Die `BypassIf` Element ist ein untergeordnetes Element des der `InstallConditions` -Element, und beschreibt eine positive Bedingung, unter dem der Befehl nicht ausgeführt werden sollte. Jede `InstallConditions` haben Element 0 (null) oder mehrere `BypassIf` Elemente.

 `BypassIf` hat die folgenden Attribute an.

|Attribut|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name des zu überprüfenden Eigenschaft. Die Eigenschaft muss zuvor definiert wurden durch ein untergeordnetes Element des der `InstallChecks` Element. Weitere Informationen finden Sie unter [ \<InstallChecks >-Element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Erforderlich. Der Typ des Vergleichs. Die folgende Liste zeigt die gültigen Werte an:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Erforderlich. Der Wert, mit der Eigenschaft verglichen werden soll.|
|`Schedule`|Dies ist optional. Der Name des eine `Schedule` Tag, das definiert, wenn diese Regel ausgewertet werden soll.|

## <a name="failif"></a>FailIf
 Die `FailIf` Element ist ein untergeordnetes Element des der `InstallConditions` -Element, und beschreibt eine positive Bedingung, unter denen die Installation beendet werden soll. Jede `InstallConditions` haben Element 0 (null) oder mehrere `FailIf` Elemente.

 `FailIf` hat die folgenden Attribute an.

|Attribut|Beschreibung|
|---------------|-----------------|
|`Property`|Erforderlich. Der Name des zu überprüfenden Eigenschaft. Die Eigenschaft muss zuvor definiert wurden durch ein untergeordnetes Element des der `InstallChecks` Element. Weitere Informationen finden Sie unter [ \<InstallChecks >-Element](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Erforderlich. Der Typ des Vergleichs. Die folgende Liste zeigt die gültigen Werte an:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Erforderlich. Der Wert, mit der Eigenschaft verglichen werden soll.|
|`String`|Dies ist optional. Der Text, der für den Benutzer bei einem Fehler anzuzeigen.|
|`Schedule`|Dies ist optional. Der Name des eine `Schedule` Tag, das definiert, wenn diese Regel ausgewertet werden soll.|

## <a name="exitcodes"></a>ExitCodes
 Die `ExitCodes` Element ist ein untergeordnetes Element des der `Command` Element. Die `ExitCodes` Element enthält ein oder mehrere `ExitCode` Element, das bestimmt, was die Installation als Reaktion auf einen Exitcode aus einem Paket tun sollten. Es kann eine optionale `ExitCode` untergeordnete Element einer `Command` Element. `ExitCodes` weist keine Attribute auf.

## <a name="exitcode"></a>ExitCode
 Die `ExitCode` Element ist ein untergeordnetes Element des der `ExitCodes` Element. Die `ExitCode` Element bestimmt, was die Installation als Reaktion auf einen Exitcode aus einem Paket tun sollten. `ExitCode` enthält keine untergeordneten Elemente ein, und weist folgende Attribute.

|Attribut|Beschreibung|
|---------------|-----------------|
|`Value`|Erforderlich. Der Wert für den Exitcode an den diese `ExitCode` Element angewendet wird.|
|`Result`|Erforderlich. Wie die Installation auf diesen Exitcode reagieren soll. Die folgende Liste zeigt die gültigen Werte an:<br /><br /> `Success`. Kennzeichnet das Paket als erfolgreich installiert.<br /><br /> `SuccessReboot`. Kennzeichnet das Paket als erfolgreich installiert, und weist das System neu starten.<br /><br /> `Fail`. Kennzeichnet das Paket an, wie Fehler.<br /><br /> `FailReboot`. Kennzeichnet das Paket als Fehler, und weist das System neu starten.|
|`String`|Dies ist optional. Der Wert, der für den Benutzer als Reaktion auf diese Exitcode anzuzeigen.|
|`FormatMessageFromSystem`|Dies ist optional. Bestimmt, ob anhand der vom System bereitgestellten Fehlermeldung, die für den Exitcode ein, oder verwenden Sie den Wert im bereitgestellten `String`. Gültige Werte sind `true`, das bedeutet, dass den Fehler vom System bereitgestellten und `false`, das bedeutet, dass die vom bereitgestellten Zeichenfolge `String`. Die Standardeinstellung ist `false`. Wenn diese Eigenschaft `false`, aber `String` ist nicht festgelegt ist, wird vom System bereitgestellten Fehlermeldung verwendet werden.|

## <a name="example"></a>Beispiel
 Das folgende Codebeispiel definiert die Befehle zum Installieren von .NET Framework 2.0.

```xml
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
- [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)
- [\<InstallChecks >-Element](../deployment/installchecks-element-bootstrapper.md)