---
title: Installieren und Konfigurieren von Tools zum Erstellen mit iOS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 7290ba820c9b678e0b87bdbeaadf9c025162e8ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844474"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Install and Configure Tools to Build using iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Visual C++ für plattformübergreifende Mobile-Entwicklung verwenden, um iOS-Code für den iOS-Simulator oder ein iOS-Gerät zu bearbeiten, zu debuggen und bereitzustellen. Aufgrund von Lizenzeinschränkungen muss der Code jedoch remote auf einem Macintosh-Computer erstellt und ausgeführt werden. Zum Erstellen und Ausführen von iOS-Apps mithilfe von Visual Studio müssen Sie den Remote-Agent ( [vcremote](https://www.npmjs.com/package/vcremote)) auf Ihrem Macintosh-Computer einrichten und konfigurieren. Der Remote-Agent verarbeitet Buildanforderungen von Visual Studio und führt die App auf einem iOS-Gerät, das mit dem Macintosh-Computer verbunden ist, oder im iOS-Simulator auf dem Macintosh-Computer aus.  
  
> [!NOTE]
> Informationen zur Verwendung von in der Cloud gehosteten Mac-Diensten anstelle eines Macs finden Sie unter [Build and Simulate iOS in the Cloud](https://taco.visualstudio.com/docs/build_ios_cloud/). Die Anweisungen gelten für das Erstellen mit Visual Studio Tools for Apache Cordova. Wenn Sie die Anweisungen zum Erstellen mit Visual C++ für plattformübergreifende Mobile-Entwicklung verwenden möchten, ersetzen Sie "vcremote" durch "vs-mda-remote".  
  
 Lesen Sie nach der Installation der Tools zum Erstellen mit iOS in diesem Thema nach, wie Sie den Remote-Agent schnell für die iOS-Entwicklung in Visual Studio und auf Ihrem Macintosh-Computer konfigurieren und aktualisieren können.  
  
 [Voraussetzungen](#Prerequisites)  
  
 [Installieren des Remote-Agents für IOS](#Install)  
  
 [Starten Sie den Remote-Agent.](#Start)  
  
 [Konfigurieren des Remote-Agents in Visual Studio](#ConfigureVS)  
  
 [Generieren einer neuen Sicherheits-PIN](#GeneratePIN)  
  
 [Generieren eines neuen Serverzertifikats](#GenerateCert)  
  
 [Konfigurieren des Remote-Agents auf dem Mac](#ConfigureMac)  
  
## <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
 Um den Remote-Agent für die Entwicklung von Code für iOS installieren und verwenden zu können, benötigen Sie folgende Komponenten:  
  
- Einen Macintosh-Computer mit OS X Mavericks oder höher  
  
- Eine [Apple-ID](https://appleid.apple.com/)  
  
- Ein aktives [iOS-Entwicklerprogramm](https://developer.apple.com/programs/ios/) -Konto bei Apple  
  
- [Xcode 6](https://developer.apple.com/xcode/downloads/)  
  
     Xcode 6 kann aus dem App Store heruntergeladen werden.  
  
- Xcode-Befehlszeilentools  
  
     Um die Xcode-Befehlszeilentools zu installieren, öffnen Sie die Terminal-App auf Ihrem Mac, und geben Sie den folgenden Befehl ein:  
  
     `xcode-select --install`  
  
- Eine in Xcode konfigurierte iOS-Signierungsidentität  
  
     Ausführliche Informationen zum Abrufen einer iOS-Signierungsidentität finden Sie unter [Maintaining Your Signing Identities and Certificates](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) (Verwalten von Signierungsidentitäten und Zertifikaten) (in englischer Sprache) in der iOS Developer Library. Um die Signierungsidentität in Xcode anzuzeigen oder festzulegen, öffnen Sie das Menü **Xcode** , und wählen Sie **Einstellungen**aus. Wählen Sie unter **Konten** Ihre Apple-ID aus, und wählen Sie dann die Schaltfläche **Details anzeigen** aus.  
  
- Bei Verwendung eines iOS-Geräts für die Entwicklung ein in Xcode konfiguriertes Bereitstellungsprofil für Ihr Gerät  
  
     Ausführliche Informationen zum Erstellen von Bereitstellungsprofilen finden Sie unter [Creating Provisioning Profiles Using Member Center](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) (Erstellen von Bereitstellungsprofilen mit Member Center) (in englischer Sprache) in der iOS Developer Library.  
  
- [Node.js](https://nodejs.org/en/)  
  
- Eine aktualisierte Version von npm  
  
     Die Version von npm, die mit Node.js bereitgestellt wird, ist möglicherweise nicht aktuell genug, um vcremote zu installieren. Um npm zu aktualisieren, öffnen Sie die Terminal-App auf Ihrem Mac, und geben Sie den folgenden Befehl ein:  
  
     `sudo npm install -g npm@latest`  
  
## <a name="install-the-remote-agent-for-ios"></a><a name="Install"></a> Installieren des Remote-Agents für iOS  
 Wenn Sie Visual C++ for Cross-Platform Mobile Development installieren, kann Visual Studio mit [vcremote](https://www.npmjs.com/package/vcremote)kommunizieren. Dies ist ein Remote-Agent, der auf Ihrem Mac ausgeführt wird und mit dem Dateien übertragen, die iOS-App erstellt und ausgeführt sowie Debugbefehle gesendet werden können.  
  
 Stellen Sie vor der Installation des Remote-Agents sicher, dass Sie die [Voraussetzungen](#Prerequisites) erfüllt und [Visual C++ für plattformübergreifende Mobile-Entwicklung](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#InstallTheTools)installiert haben.  
  
### <a name="to-download-and-install-the-remote-agent"></a><a name="DownloadInstall"></a> Herunterladen und Installieren des Remote-Agenten  
  
- Geben Sie über die Terminal-App auf Ihrem Mac Folgendes ein:  
  
   `sudo npm install -g --unsafe-perm vcremote`  
  
   Der Schalter für die globale Installation (**-g**) wird empfohlen, ist jedoch nicht zwingend erforderlich.  
  
   Während der Installation wird "vcremote" installiert, und der Entwicklermodus wird auf Ihrem Mac aktiviert. [Homebrew](https://brew.sh/) und zwei npm-Pakete, "vcremote-lib" und "vcremote-utils", werden ebenfalls installiert.  
  
  > [!NOTE]
  > Zum Installieren von Homebrew benötigen Sie sudo-Zugriff (Administrator). Wenn Sie "vcremote" ohne sudo installieren müssen, können Sie Homebrew manuell unter einem "usr/local"-Speicherort installieren und den Ordner "bin" zu Ihrem Pfad hinzufügen. Weitere Informationen finden Sie in der [Homebrew-Dokumentation](https://github.com/Homebrew/homebrew/wiki/Installation). Um den Entwicklermodus manuell zu aktivieren, geben Sie folgenden Befehl in die Terminal-App ein: `DevToolsSecurity –enable`  
  
  Wenn Sie auf eine neue Version von Visual Studio aktualisiert haben, müssen Sie diese Aktualisierung auch auf dem Remote-Agent vornehmen. Wiederholen Sie die Schritte zum Herunterladen und Installieren des Remote-Agents, um diesen zu aktualisieren.  
  
## <a name="start-the-remote-agent"></a><a name="Start"></a> Starten des Remote-Agents  
 Der Remote-Agent muss ausgeführt werden, damit Visual Studio den iOS-Code erstellen und ausführen kann. Visual Studio muss mit dem Remote-Agent gekoppelt werden, bevor eine Kommunikation stattfinden kann. Standardmäßig wird der Remote-Agent im Modus für sichere Verbindung ausgeführt. Dazu muss Visual Studio mit einer PIN gekoppelt werden.  
  
### <a name="to-start-the-remote-agent"></a><a name="RemoteAgentStartServer"></a> So starten Sie den Remote-Agenten  
  
- Geben Sie über die Terminal-App auf Ihrem Mac Folgendes ein:  
  
   `vcremote`  
  
   Dadurch wird der Remote-Agent mit einem standardmäßigen Buildverzeichnis von "~/vcremote" gestartet. Zusätzliche Konfigurationsoptionen finden Sie unter [Configure the remote agent on the Mac](#ConfigureMac).  
  
  Beim ersten Start des Remote-Agents sowie jederzeit beim Erstellen eines neuen Clientzertifikats erhalten Sie die Informationen, die zum Konfigurieren des Agents in Visual Studio erforderlich sind, einschließlich des Hostnamens, des Ports und der PIN.  
  
  ![Verwenden von vcremote zum Generieren einer sicheren PIN](../cross-platform/media/cppmdd-vcremote-generateclientcert.png "CPPMDD_vcremote_generateClientCert")  
  
  Wenn Sie vorhaben, den Remote-Agent in Visual Studio unter Verwendung des Hostnamens zu konfigurieren, pingen Sie den Mac von Windows mithilfe des Hostnamens, um sicherzustellen, dass er erreichbar ist. Ansonsten müssen Sie möglicherweise die IP-Adresse dafür verwenden.  
  
  Die generierte PIN ist für die einmalige Verwendung bestimmt und nur für einen begrenzten Zeitraum gültig. Wenn Sie Visual Studio nicht vor Ablauf dieses Zeitraums mit dem Remote-Agent koppeln, müssen Sie eine neue PIN generieren. Weitere Informationen finden Sie unter [Generate a new security PIN](#GeneratePIN).  
  
  Sie können den Remote-Agent im ungesicherten Modus verwenden. Im ungesicherten Modus kann der Remote-Agent mit Visual Studio ohne PIN gekoppelt werden.  
  
#### <a name="to-disable-secured-connection-mode"></a>So deaktivieren Sie den Modus für sichere Verbindung  
  
- Um den Modus für sichere Verbindung in "vcremote" zu deaktivieren, geben Sie diesen Befehl in der Terminal-App auf Ihrem Mac ein:  
  
     `vcremote --secure false`  
  
#### <a name="to-enable-secured-connection-mode"></a>So aktivieren Sie den Modus für sichere Verbindung  
  
- Um den Modus für sichere Verbindung zu aktivieren, geben Sie diesen Befehl ein:  
  
   `vcremote --secure true`  
  
  Sobald Sie den Remote-Agenten gestartet haben, können Sie ihn von Visual Studio aus verwenden, bis Sie ihn beenden.  
  
#### <a name="to-stop-the-remote-agent"></a>So beenden Sie den Remote-Agenten  
  
- Geben Sie im Terminalfenster, in dem "vcremote" ausgeführt wird, `Control+C`ein.  
  
## <a name="configure-the-remote-agent-in-visual-studio"></a><a name="ConfigureVS"></a> Konfigurieren des Remote-Agents in Visual Studio  
 Um von Visual Studio aus eine Verbindung mit dem Remote-Agent herzustellen, müssen Sie die Remotekonfiguration in den Visual Studio-Optionen angeben.  
  
#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>So konfigurieren Sie den Remote-Agenten in Visual Studio  
  
1. Wenn der Agent nicht bereits auf Ihrem Mac ausgeführt wird, führen Sie die Schritte unter [Starten des Remote-Agents](#Start)aus. Auf Ihrem Mac muss "vcremote" ausgeführt werden, damit Visual Studio erfolgreich gekoppelt und verbunden und das Projekt erstellt werden kann erstellen.  
  
2. Rufen Sie den Hostnamen auf Ihrem Mac oder Ihres IP-Adresse Ihres Macs ab.  
  
    Mit dem **ifconfig** -Befehl kann die IP-Adresse in einem Terminalfenster abgerufen werden. Verwenden Sie die inet-Adresse, die unter der aktiven Netzwerkschnittstelle ausgeführt ist.  
  
3. Wählen Sie in der Menüleiste von Visual Studio **Extras**, **Optionen**aus.  
  
4. Erweitern Sie im Dialogfeld **Optionen****Plattformübergreifend**, **C++**, **iOS**.  
  
5. Geben Sie in die Felder **Hostname** und **Port** die Werte ein, die vom Remote-Agent angegeben wurden, als Sie diesen gestartet haben. Der Hostname kann der DNS-Name oder die IP-Adresse Ihres Macs sein. Der Standardport ist 3030.  
  
   > [!NOTE]
   > Wenn Sie den Mac nicht mithilfe des Hostnamens pingen können, müssen Sie möglicherweise die IP-Adresse verwenden.  
  
6. Wenn Sie den Remote-Agent im standardmäßigen Modus für sichere Verbindung verwenden, aktivieren Sie das Kontrollkästchen **Sicher** , und geben Sie dann den vom Remote-Agent angegebenen PIN-Wert im Feld für die **Pin** ein. Wenn Sie den Remote-Agent im ungesicherten Verbindungsmodus verwenden, deaktivieren Sie das Kontrollkästchen **Sicher** , und lassen Sie das Feld für die **Pin** leer.  
  
7. Wählen Sie **Koppeln** aus, um das Koppeln zu aktivieren.  
  
    ![Konfigurieren der vcremote-Verbindung für iOS-Builds](../cross-platform/media/cppmdd-options-ios.PNG "CPPMDD_Options_iOS")  
  
    Die Kopplung bleibt erhalten, bis Sie den Hostnamen oder Port ändern. Wenn Sie den Hostnamen oder den Port im Dialogfeld **Optionen** ändern, wählen Sie zum Rückgängigmachen der Änderung die Schaltfläche **Zurücksetzen** aus. So stellen Sie die vorherige Kopplung wieder her.  
  
    Wenn die Kopplung nicht erfolgreich ist, stellen Sie sicher, dass der Remote-Agent ausgeführt wird. Führen Sie dazu die unter [Start the remote agent](#Start)beschriebenen Schritte aus. Wenn zu viel Zeit verstrichen ist, seit die Remote-Agent-PIN generiert wurde, führen Sie die Schritte unter [Generate a new security PIN](#GeneratePIN) auf dem Mac aus, und versuchen Sie es dann erneut. Versuchen Sie bei Verwendung der Hostname Ihres Macs stattdessen mit der IP-Adresse im Feld **Hostname** .  
  
8. Aktualisieren Sie den Namen des Ordners im Feld **Remote** Stamm, um den Ordner anzugeben, der von dem Remote-Agent im Verzeichnis Home (~) auf dem Mac verwendet wird. Standardmäßig verwendet der Remote-Agent "/Users/`username`/vcremote" als Remotestamm.  
  
9. Wählen Sie **OK** aus, um die Verbindungseinstellungen für die Remotekopplung zu speichern.  
  
   Visual Studio verwendet jedes Mal dieselben Information, um die Verbindung mit dem Remote-Agent auf Ihrem Mac herzustellen. Es ist nicht erforderlich, Visual Studio erneut mit dem Remote-Agent zu koppeln, es sei denn, Sie generieren ein neues Sicherheitszertifikat auf Ihrem Mac oder ändern dessen Hostnamen oder IP-Adresse.  
  
## <a name="generate-a-new-security-pin"></a><a name="GeneratePIN"></a> Generate a new security PIN  
 Wenn Sie den Remote-Agent erstmals starten, ist die generierte PIN für einen begrenzten Zeitraum (standardmäßig 10 Minuten) gültig. Wenn Sie Visual Studio nicht vor Ablauf dieses Zeitraums mit dem Remote-Agent koppeln, müssen Sie eine neue PIN generieren.  
  
#### <a name="to-generate-a-new-pin"></a>So generieren Sie eine neue PIN  
  
1. Halten Sie den Agent an, oder öffnen Sie ein zweites Terminal-App-Fenster auf Ihrem Mac, und verwenden Sie dieses, um den Befehl einzugeben.  
  
2. Geben Sie diesen Befehl in der Terminal-App ein:  
  
     `vcremote generateClientCert`  
  
     Der Remote-Agent generiert eine neue temporäre PIN. Wiederholen Sie die Schritte unter [Konfigurieren des Remote-Agents in Visual Studio](#ConfigureVS), um Visual Studio mithilfe der neuen PIN zu koppeln.  
  
## <a name="generate-a-new-server-certificate"></a><a name="GenerateCert"></a> Generieren eines neuen Serverzertifikats  
 Aus Sicherheitsgründen sind die Serverzertifikate, die Visual Studio mit dem Remote-Agent koppeln, an die IP oder den Hostnamen Ihres Macs gebunden. Wenn sich diese Werte geändert haben, müssen Sie ein neues Serverzertifikat generieren und anschließend Visual Studio mit den neuen Werte neu konfigurieren.  
  
#### <a name="to-generate-a-new-server-certificate"></a>So generieren Sie ein neues Serverzertifikat  
  
1. So beenden Sie den vcremote-Agent  
  
2. Geben Sie diesen Befehl in der Terminal-App ein:  
  
     `vcremote resetServerCert`  
  
3. Wenn Sie zur Bestätigung aufgefordert werden, geben Sie `Y`ein.  
  
4. Geben Sie diesen Befehl in der Terminal-App ein:  
  
     `vcremote generateClientCert`  
  
     Dadurch wird eine neue temporäre PIN generiert.  
  
5. Wiederholen Sie die Schritte unter [Konfigurieren des Remote-Agents in Visual Studio](#ConfigureVS), um Visual Studio mithilfe der neuen PIN zu koppeln.  
  
## <a name="configure-the-remote-agent-on-the-mac"></a><a name="ConfigureMac"></a> Configure the remote agent on the Mac  
 Sie können den Remoteagent mit verschiedenen Befehlszeilenoptionen konfigurieren. Beispielsweise können Sie den Port zum Überwachen der Build-Anforderungen und die maximale Anzahl an Builds angeben, die auf dem Dateisystem verwaltet werden sollen. Die Standardgrenze ist 10 Builds. Der Remote-Agent entfernt beim Herunterfahren die überzähligen Builds.  
  
#### <a name="to-configure-the-remote-agent"></a>So konfigurieren Sie den Remote-Agenten  
  
- Um eine vollständige Liste der Remote-Agent-Befehle anzuzeigen, geben Sie in die Terminal-App Folgendes ein:  
  
     `vcremote --help`  
  
- Geben Sie zum Deaktivieren des sicheren Modus und zum Aktivieren von einfachen HTTP-basierten Verbindungen Folgendes ein:  
  
     `vcremote --secure false`  
  
     Wenn Sie diese Option verwenden, deaktivieren Sie das Kontrollkästchen **Sicher**, und lassen Sie das Feld für die **PIN** leer, wenn Sie den Agent in Visual Studio konfigurieren.  
  
- Geben Sie zum Angeben eines Speicherorts für Remote-Agent-Dateien Folgendes ein:  
  
     `vcremote --serverDir directory_path`  
  
     *&lt;directory_path&gt;* ist hierbei der Speicherort auf Ihrem Mac, in welchem Protokolldateien, Builds und Serverzertifikate abgelegt werden. Standardmäßig ist dies der Speicherort/Users/*username*/vcremote ". Builds werden an diesem Speicherort nach Build-Nummer angeordnet.  
  
- Um mithilfe eines Hintergrundprozesses `stdout` und `stderr` in einer Datei namens "server.log" zu erfassen, geben Sie Folgendes ein:  
  
     `vcremote > server.log 2>&1 &`  
  
     Die Datei "server.log" kann bei der Problembehandlung von Builds hilfreich sein.  
  
- Um den Agent mit einer Konfigurationsdatei anstelle von Befehlszeilenparametern auszuführen, geben Sie Folgendes ein:  
  
     `vcremote --config config_file_path`  
  
     *config_file_path* ist hierbei der Pfad zu einer Konfigurationsdatei im JSON-Format. Die Startoptionen und deren Werte dürfen keine Bindestriche enthalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von Visual C++ für plattformübergreifende Mobile-Entwicklung](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
