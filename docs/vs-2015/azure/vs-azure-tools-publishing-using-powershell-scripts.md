---
title: Mithilfe von Windows PowerShell-Skripts zum Veröffentlichen in Entwicklungs- und Testumgebungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit Windows PowerShell-Skripts in Visual Studio zum Veröffentlichen für Entwicklungs- und testumgebungen.
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001873"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Veröffentlichung in Entwicklungs- und Testumgebungen mithilfe von Windows PowerShell-Skripts

Wenn Sie eine Webanwendung in Visual Studio erstellen, können Sie ein Windows PowerShell-Skript generieren, die Sie später zum Automatisieren der Veröffentlichung Ihrer Website in Azure als Web-App in Azure App Service oder einen virtuellen Computer verwenden können. Sie können bearbeiten und erweitern das Windows PowerShell-Skript in der Visual Studio-Editor, um Ihre Anforderungen anpassen oder das Skript in vorhandene Build-, Test- und veröffentlichungsskripts integrieren.

Mithilfe dieser Skripts können Sie angepasste Versionen (auch bekannt als Entwicklungs- und testumgebungen) Ihres Standorts zur vorübergehenden Verwendung bereitstellen. Beispielsweise können Sie eine bestimmte Version Ihrer Website auf virtuellen Azure-Computer oder den stagingslot auf einer Website zum Ausführen einer Testsuite, reproduzieren eines Bugs, Testen eines Bugfixes, Testen einer vorgeschlagenen Änderung oder richten Sie eine benutzerdefinierte Umgebung für eine Demo oder Präsentation einrichten. Nachdem Sie ein Skript, die Ihr Projekt veröffentlicht erstellt haben, können Sie identische Umgebungen erstellen, indem Sie das Skript erneut ausführen, je nach Bedarf, oder führen Sie das Skript mit Ihrem eigenen Build Ihrer Webanwendung, um eine benutzerdefinierte Umgebung für Testzwecke zu erstellen.

## <a name="prerequisites"></a>Vorraussetzungen

* Azure SDK 2.3 oder höher. Finden Sie unter [Visual Studio-Downloads](http://go.microsoft.com/fwlink/?LinkID=624384). (Sie benötigen keine Azure SDK, um die Skripts für Webprojekte zu generieren. Dieses Feature ist für Webprojekte, nicht auf Webrollen in Clouddiensten.)
* Azure PowerShell 0.7.4 oder höher. Finden Sie unter [installieren und Konfigurieren von Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) oder höher.

## <a name="additional-tools"></a>Zusätzliche Tools

Zusätzliche Tools und Ressourcen für die Arbeit mit PowerShell in Visual Studio für Azure-Entwicklung zur Verfügung stehen. Finden Sie unter [PowerShell-Tools für Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Generieren der veröffentlichungsskripts

Sie können die veröffentlichungsskripts für einen virtuellen Computer, die Ihre Website hostet, wenn Sie ein neues Projekt anhand generieren [diese Anweisungen](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Sie können auch [Generieren von veröffentlichungsskripts für Web-apps in Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Skripts, die Visual Studio generiert

Visual Studio generiert einen Ordner auf Projektebene namens **PublishScripts** , enthält zwei Windows PowerShell-Dateien, ein veröffentlichungsskript für Ihren virtuellen Computer oder die Website und ein Modul, das Funktionen, mit denen Sie enthält in der -Skripts. Visual Studio generiert außerdem eine Datei in das JSON-Format, das angibt, die Details des Projekts, das Sie bereitstellen.

### <a name="windows-powershell-publish-script"></a>Windows PowerShell-veröffentlichungsskript

Das veröffentlichungsskript enthält spezifische veröffentlichungsschritte für die Bereitstellung auf einer Website oder einen virtuellen Computer. Visual Studio stellt farbige syntaxmarkierung für die Entwicklung mit Windows PowerShell. Hilfe zu Funktionen zur Verfügung steht, und Sie frei, die Funktionen im Skript bearbeiten können an Ihre sich ändernden Anforderungen anpassen.

### <a name="windows-powershell-module"></a>Windows PowerShell-Modul

Das Windows PowerShell-Modul, das generiert Visual Studio enthält Funktionen, die vom veröffentlichungsskript verwendet. Diese Azure PowerShell-Funktionen sind nicht dazu gedacht, die geändert werden. Finden Sie unter [installieren und Konfigurieren von Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>JSON-Konfigurationsdatei

Die JSON-Datei wird erstellt, der **Konfigurationen** Ordner und enthält Configuration-Daten, die genau, welche Ressourcen in Azure bereitgestellt werden. Der Name der Datei, die Visual Studio generiert ist, Projekt-Name-WAWS-dev.json, wenn Sie eine Website oder ein Projekt namens-VM-dev.json erstellt, wenn Sie einen virtuellen Computer erstellt haben. Hier ist ein Beispiel einer JSON-Konfigurationsdatei, die generiert wird, wenn Sie eine Website erstellen. Die meisten Werte sind selbsterklärend. Der Websitename wird von Azure generiert, damit es unter Umständen nicht den Projektnamen übereinstimmt.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Wenn Sie einen virtuellen Computer erstellen, sieht die JSON-Konfigurationsdatei ähnlich der folgenden. Ein Cloud-Dienst wird als Container für den virtuellen Computer erstellt. Der virtuelle Computer enthält die üblichen Endpunkte für den Webzugriff über HTTP und HTTPS sowie Endpunkte für Web Deploy, Hier können Sie die Veröffentlichung auf der Website von Ihrem lokalen Computer, Remotedesktop und Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Sie können die JSON-Konfiguration ändern, was geschieht, wenn Sie beim Ausführen der veröffentlichungsskripts bearbeiten. Die `cloudService` und `virtualMachine` Abschnitte sind erforderlich, aber Sie können löschen, die `databases` Abschnitt, wenn Sie ihn nicht benötigen. Die Eigenschaften leer in der Standardkonfigurationsdatei, die Visual Studio generiert sind optional. die Eigenschaften, die in der Standardkonfigurationsdatei Werte aufweisen müssen.

Wenn Sie über eine Website mit mehreren bereitstellungsumgebungen (als Slots bezeichnet) anstelle einer einzelnen Produktionswebsite in Azure verfügen, können Sie den slotnamen der Website in der JSON-Konfigurationsdatei einschließen. Z. B., wenn Sie eine Website verfügen, mit dem Namen **Mysite** und einem Slot namens **testen** lautet der URI `mysite-test.cloudapp.net`, aber der richtige Namen für die Verwendung in der Konfigurationsdatei ist MySite(Test)". Nur möglich, diesen, wenn die Website und die Slots bereits in Ihrem Abonnement vorhanden sein. Wenn sie nicht vorhanden sind, erstellen Sie die Website durch Ausführen des Skripts ohne den Slot anzugeben, erstellen Sie dann den Slot in der [Azure-Portal](https://portal.azure.com/), und führen Sie anschließend das Skript mit dem geänderten Websitenamen. Weitere Informationen zu den bereitstellungsslots für Web-apps finden Sie unter [Einrichten von Stagingumgebungen für Web-apps in Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Gewusst wie: Ausführen der veröffentlichungsskripts

Wenn Sie ein Windows PowerShell-Skript vor der nie ausgeführt haben, müssen Sie zuerst die Ausführungsrichtlinie So aktivieren Sie die Ausführung von Skripts festlegen. Die Richtlinie ist eine Sicherheitsfunktion, um zu verhindern, dass Benutzer Windows PowerShell-Skripts ausführen, wenn sie sind anfällig für Malware oder Viren, bei denen Skripts ausführen.

### <a name="run-the-script"></a>Führen Sie das Skript

1. Erstellen Sie das Web Deploy-Paket für Ihr Projekt. Web Deploy-Pakete ist, komprimierte Archive (ZIP-Datei), die Dateien enthalten, die Sie zu Ihrer Website oder einen virtuellen Computer kopieren möchten. Sie können Web Deploy-Pakete in Visual Studio für jede Webanwendung erstellen.

   ![Erstellen Sie Paket bereitstellen](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Webbereitstellungspakets in Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). Sie können die Erstellung Ihres Web Deploy-Pakets auch automatisieren, wie in beschrieben [anpassen und Erweitern der veröffentlichungsskripts](#customizing-and-extending-publish-scripts).

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Skript aus, und wählen Sie dann **mit PowerShell-ISE öffnen**.
1. Wenn Windows PowerShell-Skripts auf diesem Computer zum ersten Mal ausgeführt wird, öffnen Sie ein Eingabeaufforderungsfenster mit Administratorrechten, und geben Sie den folgenden Befehl aus:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Melden Sie sich in Azure mithilfe des folgenden Befehls.

    ```powershell
    Add-AzureAccount
    ```

    Geben Sie bei entsprechender Aufforderung Ihren Benutzernamen und Kennwort ein.

    Beachten Sie, dass wenn Sie das Skript automatisieren, diese Methode für die Bereitstellung von Azure-Anmeldeinformationen nicht funktioniert. Sie sollten stattdessen die `.publishsettings` Datei, um Anmeldeinformationen bereitzustellen. Nur Sie verwenden den Befehl **Get-AzurePublishSettingsFile** um die Datei aus Azure herunterzuladen und danach verwenden Sie **Import-AzurePublishSettingsFile** zum Importieren der Datei. Ausführliche Anweisungen finden Sie unter [installieren und Konfigurieren von Azure PowerShell](/powershell/azure/overview).

1. (Optional) Verwenden, wenn Sie Azure-Ressourcen wie z. B. den virtuellen Computer erstellen möchten, Datenbanken und Websites, ohne die Veröffentlichung Ihrer Webanwendung, die **Publish-WebApplication. ps1** -Befehl mit der **-Konfiguration**-Argument auf die JSON-Konfigurationsdatei festgelegt. Diese Befehlszeile verwendet die JSON-Konfigurationsdatei, um zu bestimmen, welche Ressourcen zum Erstellen. Da sie die Standardeinstellungen für andere Befehlszeilenargumente verwendet, die Ressourcen erstellt, aber nicht Ihre Webanwendung zu veröffentlichen. – Verbose Option erhalten Sie weitere Informationen dazu, was passiert.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Verwenden der **Publish-WebApplication. ps1** Befehl wie in einem der folgenden Beispiele rufen Sie das Skript, und veröffentlichen Ihre Web-Anwendung gezeigt. Wenn Sie außer Kraft setzen die Standardeinstellungen für alle anderen Argumente, z. B. den Namen des Abonnements, Paketname, VM-Anmeldeinformationen oder Anmeldeinformationen für die Datenbank zu veröffentlichen müssen, können Sie diesen Parameter angeben. Verwenden der **– Verbose** Option, um weitere Informationen über den Fortschritt des Veröffentlichungsvorgangs anzuzeigen.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Wenn Sie einen virtuellen Computer erstellen, sieht der Befehl wie folgt aus. Außerdem wird veranschaulicht, wie Sie die Anmeldeinformationen für mehrere Datenbanken angeben. Für die virtuellen Computer, die diese Skripts zu erstellen, ist das SSL-Zertifikat nicht von einer vertrauenswürdigen Stammzertifizierungsstelle. Aus diesem Grund müssen Sie verwenden die **AllowUntrusted** Option.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Das Skript kann Datenbanken erstellen, es erstellt jedoch keine Datenbankserver. Wenn Sie einen Datenbankserver erstellen möchten, können Sie mithilfe der **New-AzureSqlDatabaseServer** Funktion im Azure-Modul.

## <a name="customizing-and-extending-the-publish-scripts"></a>Anpassen und Erweitern der veröffentlichungsskripts

Sie können das veröffentlichungsskript und die JSON-Konfigurationsdatei anpassen. Die Funktionen im Windows PowerShell-Modul **AzureWebAppPublishModule.psm1** nicht geändert werden sollen. Wenn Sie nur eine andere Datenbank angeben oder einige der Eigenschaften des virtuellen Computers ändern möchten, bearbeiten Sie die JSON-Konfigurationsdatei. Wenn Sie die Funktionalität des Skripts zu automatisieren, erstellen und Testen Ihr Projekt erweitern möchten, können Sie funktionsstubs in implementieren **Publish-WebApplication. ps1**.

Um den Buildvorgang Ihres Projekts automatisieren möchten, fügen Sie Code, den MSBuild Aufrufen `New-WebDeployPackage` wie in diesem Codebeispiel gezeigt. Der Pfad zum MSBuild-Befehl unterscheidet sich abhängig von der Version von Visual Studio, die Sie installiert haben. Um den richtigen Pfad zu erhalten, können Sie mithilfe der Funktion **Get-MSBuildCmd**, wie im folgenden Beispiel gezeigt.

### <a name="to-automate-building-your-project"></a>Um den Buildvorgang Ihres Projekts automatisieren

1. Hinzufügen der `$ProjectFile` Parameter in den globalen Parametern-Abschnitt.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Kopieren Sie die Funktion `Get-MSBuildCmd` in Ihre Skriptdatei.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Ersetzen Sie dies `New-WebDeployPackage` mit den folgenden code, und Ersetzen Sie die Platzhalter in der Zeile `$msbuildCmd`. Dieser Code ist für Visual Studio 2015. Wenn Sie Visual Studio 2017 verwenden, ändern Sie die **VisualStudioVersion** Eigenschaft `15.0` (`12.0` für Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Um Ihre Webanwendung zu erstellen, verwenden Sie MsBuild.exe. Hilfe finden Sie in der MSBuild-Befehlszeilenreferenz unter: [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Starten der Ausführung des Build-Befehls

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Rufen Sie die `New-WebDeployPackage` Funktion, bevor Sie diese Zeile: `$Config = Read-ConfigFile $Configuration` für Web-apps oder `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` für virtuelle Computer.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Rufen Sie das angepasste Skript über die Befehlszeile, und übergeben die `$Project` Argument aus, wie im folgenden Beispiel:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Fügen Sie Code zum Testen der Anwendung zu automatisieren, `Test-WebApplication`. Achten Sie darauf, dass Sie die auskommentierung der Zeilen im **Publish-WebApplication. ps1** , in denen diese Funktionen aufgerufen werden. Wenn Sie keine Implementierung bereitstellen, können Sie Ihr Projekt mit Visual Studio manuell erstellen und führen Sie dann das veröffentlichungsskript zum Veröffentlichen in Azure.

## <a name="publishing-function-summary"></a>Zusammenfassung der Veröffentlichungsfunktion
Um Hilfe zu Funktionen erhalten Sie an der Windows PowerShell-Eingabeaufforderung verwenden können, verwenden Sie den Befehl `Get-Help function-name`. Die Hilfe umfasst Parameterhilfe und Beispiele. Es ist auch der gleichen Hilfetext in den skriptquelldateien **AzureWebAppPublishModule.psm1** und **Publish-WebApplication. ps1**. Das Skript und die Hilfe werden in der Visual Studio-Sprache lokalisiert.

**AzureWebAppPublishModule**

| Funktionsname | Beschreibung |
| --- | --- |
| Add-AzureSQLDatabase |Erstellt eine neue Azure SQL-Datenbank an. |
| Add-AzureSQLDatabases |Erstellt Azure SQL-Datenbanken von den Werten in der JSON-Konfigurationsdatei, die Visual Studio generiert. |
| Add-AzureVM |Erstellt eine Azure-VM, und gibt die URL des bereitgestellten virtuellen Computers zurück. Die Funktion richtet die Voraussetzungen und ruft dann die **New-AzureVM** Funktion (Azure-Modul), um einen neuen virtuellen Computer zu erstellen. |
| Add-AzureVMEndpoints |Einen virtuellen Computer neue eingabeendpunkte hinzugefügt, und gibt Sie den virtuellen Computer mit dem neuen Endpunkt zurück. |
| Add-AzureVMStorage |Erstellt ein neues Azure Storage-Konto im aktuellen Abonnement. Der Name des Kontos beginnt mit "Devtest", gefolgt von einer eindeutigen alphanumerischen Zeichenfolge. Die Funktion gibt den Namen des neuen Speicherkontos. Geben Sie einen Speicherort oder eine Affinitätsgruppe für das neue Speicherkonto ein. |
| Add-AzureWebsite |Erstellt eine Website mit dem angegebenen Namen und Speicherort. Diese Funktion ruft die **New-AzureWebsite** Funktion im Azure-Modul. Wenn das Abonnement bereits eine Website mit dem angegebenen Namen enthält, wird diese Funktion wird die Website erstellt, und gibt ein Websiteobjekt zurück. Andernfalls wird `$null` zurückgegeben. |
| Backup-Subscription |Speichert das aktuelle Azure-Abonnement in der `$Script:originalSubscription` Variablen im Geltungsbereich des Skripts. Diese Funktion speichert das aktuelle Azure-Abonnement (abgerufenen `Get-AzureSubscription -Current`) und sein Speicherkonto sowie das Abonnement, das von diesem Skript geändert wird (in der Variablen gespeicherten `$UserSpecifiedSubscription`) und sein Speicherkonto im Skriptbereich. Durch die Werte gespeichert werden, können Sie eine Funktion, wie z. B. `Restore-Subscription`, um den ursprüngliche aktuelle Abonnements und Speicherkontos Konto zum aktuellen Status zurückzusetzen, wenn der aktuelle Status geändert hat. |
| Find-AzureVM |Ruft die angegebenen virtuellen Azure-Computer ab. |
| Format-DevTestMessageWithTime |Voran, Datum und Uhrzeit in eine Nachricht. Diese Funktion dient für Nachrichten, die in die Fehler- und Verbose-Streams geschrieben. |
| Get-AzureSQLDatabaseConnectionString |Stellt eine Verbindungszeichenfolge zur Verbindung mit einer Azure SQL-Datenbank zusammen. |
| Get-AzureVMStorage |Gibt den Namen der vom ersten Speicherkonto mit dem Namensmuster "Devtest *" (Groß-/Kleinschreibung) in der angegebenen Position oder die Affinitätsgruppe. Wenn die "Devtest*" Storage-Konto entspricht nicht der Speicherort oder die Affinitätsgruppe, der Funktion ignoriert. Geben Sie einen Speicherort oder eine Affinitätsgruppe an. |
| Get-MSDeployCmd |Gibt einen Befehl zum Ausführen des Tools MsDeploy.exe zurück. |
| New-AzureVMEnvironment |Sucht oder erstellt einen virtuellen Computer im Abonnement, das mit den Werten in der JSON-Konfigurationsdatei übereinstimmt. |
| Publish-WebPackage |Verwendet MsDeploy.exe und ein Paket veröffentlichen. ZIP-Datei zum Bereitstellen von Ressourcen auf einer Website. Diese Funktion generiert keine Ausgabe. Wenn der Aufruf von MSDeploy.exe fehlschlägt, löst die Funktion eine Ausnahme aus. Um eine ausführlichere Ausgabe wünschen, verwenden Sie die **-Verbose** Option. |
| Publish-WebPackageToVM |Überprüft die Parameterwerte und ruft dann die **Publish-WebPackage** Funktion. |
| Read-ConfigFile |Überprüft die JSON-Konfigurationsdatei, und gibt eine Hashtabelle der ausgewählten Werte zurück. |
| Restore-Subscription |Setzt das aktuelle Abonnement auf das ursprüngliche Abonnement zurück. |
| Test-AzureModule |Gibt `$true` ist die Version des installierten Azure-Moduls 0.7.4 oder höher. Gibt `$false` , wenn das Modul nicht installiert ist, oder eine frühere Version. Diese Funktion hat keine Parameter. |
| Test-AzureModuleVersion |Gibt `$true` ist die Version des Azure-Moduls 0.7.4 oder höher. Gibt `$false` , wenn das Modul nicht installiert ist, oder eine frühere Version. Diese Funktion hat keine Parameter. |
| Test-HttpsUrl |Die Eingabe-URL konvertiert in ein System.Uri-Objekt. Gibt `$True` , wenn die URL absolut ist und ihr Schema Https ist. Gibt `$false` , wenn die URL relativ ist, nicht das HTTPS-Schema oder die Eingabezeichenfolge in eine URL konvertiert werden kann. |
| Test-Member |Gibt `$true` ist eine Eigenschaft oder Methode ein Member des Objekts. Andernfalls wird `$false` zurückgegeben. |
| Write-ErrorWithTime |Schreibt eine Fehlermeldung angezeigt, die momentan vorangestellt. Diese Funktion ruft die **Format-DevTestMessageWithTime** Funktion die Zeit, bevor die Nachricht in den fehlerdatenstrom geschrieben vorangestellt werden soll. |
| Write-HostWithTime |Schreibt eine Meldung in das Hostprogramm (**Write-Host**) mit dem Präfix, mit der aktuellen Zeit. Die Auswirkungen des Schreibens in das Hostprogramm variiert. Die meisten Programme, die Windows PowerShell hosten diese Nachrichten an die Standardausgabe geschrieben. |
| Write-VerboseWithTime |Schreibt eine ausführliche Meldung mit dem Präfix, mit der aktuellen Zeit. Da sie aufruft, **Write-Verbose**, die Meldung angezeigt, nur wenn das Skript mit ausgeführt wird die **ausführlich** Parameter oder wenn die **VerbosePreference** zu festgelegtist **Weiterhin**. |

**Veröffentlichen-WebApplication**

| Funktionsname | Beschreibung |
| --- | --- |
| Neue AzureWebApplicationEnvironment |Azure-Ressourcen, z. B. eine Website oder eine virtuelle Maschine wird erstellt. |
| Neue WebDeployPackage |Diese Funktion ist nicht implementiert. Sie können Befehle in dieser Funktion zum Erstellen Ihres Projekts hinzufügen. |
| Veröffentlichen von AzureWebApplication |Veröffentlicht eine Webanwendung in Azure. |
| Veröffentlichen-WebApplication |Erstellen und Bereitstellen von Web-Apps, virtuelle Computer, SQL-Datenbanken und Speicherkonten für ein Visual Studio-Webprojekt. |
| Test-WebApplication |Diese Funktion ist nicht implementiert. Sie können Befehle in dieser Funktion zum Testen Ihrer Anwendung hinzufügen. |

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr über die PowerShell-Skripterstellung [Skripterstellung mit Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) und andere Azure PowerShell-Skripts finden Sie in der [Script Center](https://azure.microsoft.com/documentation/scripts/).
