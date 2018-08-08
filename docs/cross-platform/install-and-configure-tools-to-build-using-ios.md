---
title: Installieren und Konfigurieren von Tools zum Erstellen mit iOS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0c311c9-9eb9-42c5-ba07-25604362cd28
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: fe73510c645eadea99796b8b8aea5b6eec1f01c9
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251810"
---
# <a name="install-and-configure-tools-to-build-using-ios"></a>Installieren und Konfigurieren von Tools zum Erstellen mit iOS

Sie können Visual C++ für plattformübergreifende Mobile-Entwicklung verwenden, um iOS-Code für den iOS-Simulator oder ein iOS-Gerät zu bearbeiten, zu debuggen und bereitzustellen. Aufgrund von Lizenzeinschränkungen muss der Code jedoch remote auf einem Macintosh-Computer erstellt und ausgeführt werden. Zum Erstellen und Ausführen von iOS-Apps mithilfe von Visual Studio müssen Sie den Remote-Agent ( [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)) auf Ihrem Macintosh-Computer einrichten und konfigurieren. Der Remote-Agent verarbeitet Buildanforderungen von Visual Studio und führt die App auf einem iOS-Gerät, das mit dem Macintosh-Computer verbunden ist, oder im iOS-Simulator auf dem Macintosh-Computer aus.

> [!NOTE]
> Informationen zur Verwendung von in der Cloud gehosteten Mac-Diensten anstelle eines Macs finden Sie unter [Konfigurieren von Visual Studio zum Herstellen der Verbindung zu Ihrem in der Cloud gehosteten Mac](https://docs.microsoft.com/en-us/visualstudio/cross-platform/tools-for-cordova/tips-workarounds/host-a-mac-in-the-cloud?view=toolsforcordova-2017#configure-visual-studio-to-connect-to-your-cloud-hosted-mac). Die Anweisungen gelten für das Erstellen mit Visual Studio Tools for Apache Cordova. Um die Anweisungen für den Build mit C++ zu verwenden, müssen Sie „vcremote“ statt „remotebuild“ angeben.

Lesen Sie nach der Installation der Tools zum Erstellen mit iOS in diesem Thema nach, wie Sie den Remote-Agent schnell für die iOS-Entwicklung in Visual Studio und auf Ihrem Macintosh-Computer konfigurieren und aktualisieren können.

## <a name="prerequisites"></a>Erforderliche Komponenten

Um den Remote-Agent für die Entwicklung von Code für iOS installieren und verwenden zu können, benötigen Sie folgende Komponenten:

- Einen Mac-Computer mit OS X Mavericks (Version 10.9) oder höher

- Eine [Apple-ID](https://appleid.apple.com/)

- Ein aktives [iOS-Entwicklerprogramm](https://developer.apple.com/programs/ios/) -Konto bei Apple

- [Xcode](https://developer.apple.com/xcode/downloads/) Version 6 oder höher.

   Xcode kann aus dem App Store heruntergeladen werden.

- Xcode-Befehlszeilentools

   Um die Xcode-Befehlszeilentools zu installieren, öffnen Sie die Terminal-App auf Ihrem Mac, und geben Sie den folgenden Befehl ein:

   `xcode-select --install`

- Eine in Xcode konfigurierte iOS-Signierungsidentität

   Ausführliche Informationen zum Abrufen einer iOS-Signierungsidentität finden Sie unter [Maintaining Your Signing Identities and Certificates (Verwalten von Signierungsidentitäten und Zertifikaten)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingCertificates/MaintainingCertificates.html) in der iOS Developer Library. Um die Signierungsidentität in Xcode anzuzeigen oder festzulegen, öffnen Sie das Menü **Xcode** , und wählen Sie **Einstellungen**aus. Wählen Sie unter **Konten** Ihre Apple-ID aus, und wählen Sie dann die Schaltfläche **Details anzeigen** aus.

- Bei Verwendung eines iOS-Geräts für die Entwicklung ein in Xcode konfiguriertes Bereitstellungsprofil für Ihr Gerät

   Ausführliche Informationen zum Erstellen von Bereitstellungsprofilen finden Sie unter [Creating Provisioning Profiles Using Member Center (Erstellen von Bereitstellungsprofilen mit Member Center)](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/MaintainingProfiles/MaintainingProfiles.html#//apple_ref/doc/uid/TP40012582-CH30-SW24) in der iOS Developer Library.

- [Node.js](https://nodejs.org/)

   Installieren Sie die aktuelle Long Term Support-Version (LTS) 8.x von Node.js auf Ihrem Mac. Beachten Sie, dass andere aktuelle Releaseversionen einige Module in „vcremote“ möglicherweise nicht unterstützen. Dadurch kann die Installation von „vcremote“ fehlschlagen.

- Eine aktualisierte Version von npm

   Die Version von npm, die mit Node.js bereitgestellt wird, ist möglicherweise nicht aktuell genug, um vcremote zu installieren. Um npm zu aktualisieren, öffnen Sie die Terminal-App auf Ihrem Mac, und geben Sie den folgenden Befehl ein:

   `sudo npm install -g npm@latest`

##  <a name="Install"></a> Installieren des Remote-Agents für iOS

Wenn Sie Visual C++ for Cross-Platform Mobile Development installieren, kann Visual Studio mit [vcremote](https://go.microsoft.com/fwlink/p/?LinkId=534988)kommunizieren. Dies ist ein Remote-Agent, der auf Ihrem Mac ausgeführt wird und mit dem Dateien übertragen, die iOS-App erstellt und ausgeführt sowie Debugbefehle gesendet werden können.

Stellen Sie vor der Installation des Remote-Agents sicher, dass alle [erforderlichen Komponenten](#Prerequisites) vorhanden sind und [Visual C++ für die plattformübergreifende Mobile-Entwicklung](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md#install-the-tools) installiert ist.

###  <a name="DownloadInstall"></a> Herunterladen und Installieren des Remote-Agenten

- Geben Sie über die Terminal-App auf Ihrem Mac Folgendes ein:

   `sudo npm install -g --unsafe-perm vcremote`

   Der Schalter für die globale Installation (**-g**) wird empfohlen, ist jedoch nicht zwingend erforderlich.

   Während der Installation wird "vcremote" installiert, und der Entwicklermodus wird auf Ihrem Mac aktiviert. [Homebrew](https://brew.sh/) und zwei npm-Pakete, "vcremote-lib" und "vcremote-utils", werden ebenfalls installiert. Nach Abschluss der Installation ist es sicher, alle Warnungen über übersprungene optionale Abhängigkeiten zu ignorieren.

   > [!NOTE]
   > Zum Installieren von Homebrew benötigen Sie sudo-Zugriff (Administrator). Wenn Sie "vcremote" ohne sudo installieren müssen, können Sie Homebrew manuell unter einem "usr/local"-Speicherort installieren und den Ordner "bin" zu Ihrem Pfad hinzufügen. Weitere Informationen finden Sie in der [Homebrew-Dokumentation](https://github.com/Homebrew/homebrew/wiki/Installation). Um den Entwicklermodus manuell zu aktivieren, geben Sie folgenden Befehl in die Terminal-App ein: `DevToolsSecurity -enable`

Wenn Sie auf eine neue Version von Visual Studio aktualisiert haben, müssen Sie diese Aktualisierung auch auf dem Remote-Agent vornehmen. Wiederholen Sie die Schritte zum Herunterladen und Installieren des Remote-Agents, um diesen zu aktualisieren.

##  <a name="Start"></a> Starten des Remote-Agents

Der Remote-Agent muss ausgeführt werden, damit Visual Studio den iOS-Code erstellen und ausführen kann. Visual Studio muss mit dem Remote-Agent gekoppelt werden, bevor eine Kommunikation stattfinden kann. Standardmäßig wird der Remote-Agent im Modus für sichere Verbindung ausgeführt. Dazu muss Visual Studio mit einer PIN gekoppelt werden.

###  <a name="RemoteAgentStartServer"></a> So starten Sie den Remote-Agenten

- Geben Sie über die Terminal-App auf Ihrem Mac Folgendes ein:

   `vcremote`

   Dadurch wird der Remote-Agent mit einem standardmäßigen Buildverzeichnis von "~/vcremote" gestartet. Zusätzliche Konfigurationsoptionen finden Sie unter [Configure the remote agent on the Mac](#ConfigureMac).

Beim ersten Start des Remote-Agents sowie jederzeit beim Erstellen eines neuen Clientzertifikats erhalten Sie die Informationen, die zum Konfigurieren des Agents in Visual Studio erforderlich sind, einschließlich des Hostnamens, des Ports und der PIN.

![Verwenden von vcremote zum Generieren einer sicheren PIN](../cross-platform/media/cppmdd_vcremote_generateclientcert.png "CPPMDD_vcremote_generateClientCert")

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

- Drücken Sie im Terminalfenster, in dem „vcremote“ ausgeführt wird, **UMSCHALT**+**C**.

##  <a name="ConfigureVS"></a> Konfigurieren des Remote-Agents in Visual Studio

Um von Visual Studio aus eine Verbindung mit dem Remote-Agent herzustellen, müssen Sie die Remotekonfiguration in den Visual Studio-Optionen angeben.

#### <a name="to-configure-the-remote-agent-from-visual-studio"></a>So konfigurieren Sie den Remote-Agenten in Visual Studio

1. Wenn der Agent nicht bereits auf Ihrem Mac ausgeführt wird, führen Sie die Schritte unter [Starten des Remote-Agents](#Start)aus. Auf Ihrem Mac muss "vcremote" ausgeführt werden, damit Visual Studio erfolgreich gekoppelt und verbunden und das Projekt erstellt werden kann erstellen.

1. Rufen Sie den Hostnamen auf Ihrem Mac oder Ihres IP-Adresse Ihres Macs ab.

   Mit dem **ifconfig** -Befehl kann die IP-Adresse in einem Terminalfenster abgerufen werden. Verwenden Sie die inet-Adresse, die unter der aktiven Netzwerkschnittstelle ausgeführt ist.

1. Wählen Sie in der Menüleiste von Visual Studio **Extras**, **Optionen**aus.

1. Erweitern Sie im Dialogfeld **Optionen** **Plattformübergreifend**, **C++**, **iOS**.

1. Geben Sie in die Felder **Hostname** und **Port** die Werte ein, die vom Remote-Agent angegeben wurden, als Sie diesen gestartet haben. Der Hostname kann der DNS-Name oder die IP-Adresse Ihres Macs sein. Der Standardport ist 3030.

   > [!NOTE]
   > Wenn Sie den Mac nicht mithilfe des Hostnamens pingen können, müssen Sie möglicherweise die IP-Adresse verwenden.

1. Wenn Sie den Remote-Agent im standardmäßigen Modus für sichere Verbindung verwenden, aktivieren Sie das Kontrollkästchen **Sicher** , und geben Sie dann den vom Remote-Agent angegebenen PIN-Wert im Feld für die **Pin** ein. Wenn Sie den Remote-Agent im ungesicherten Verbindungsmodus verwenden, deaktivieren Sie das Kontrollkästchen **Sicher** , und lassen Sie das Feld für die **Pin** leer.

1. Wählen Sie **Koppeln** aus, um das Koppeln zu aktivieren.

   ![Konfigurieren der vcremote-Verbindung für iOS-Builds](../cross-platform/media/cppmdd_options_ios.PNG "CPPMDD_Options_iOS")

   Die Kopplung bleibt erhalten, bis Sie den Hostnamen oder Port ändern. Wenn Sie den Hostnamen oder den Port im Dialogfeld **Optionen** ändern, wählen Sie zum Rückgängigmachen der Änderung die Schaltfläche **Zurücksetzen** aus. So stellen Sie die vorherige Kopplung wieder her.

   Wenn die Kopplung nicht erfolgreich ist, stellen Sie sicher, dass der Remote-Agent ausgeführt wird. Führen Sie dazu die unter [Start the remote agent](#Start)beschriebenen Schritte aus. Wenn zu viel Zeit verstrichen ist, seit die Remote-Agent-PIN generiert wurde, führen Sie die Schritte unter [Generate a new security PIN](#GeneratePIN) auf dem Mac aus, und versuchen Sie es dann erneut. Versuchen Sie bei Verwendung der Hostname Ihres Macs stattdessen mit der IP-Adresse im Feld **Hostname** .

1. Aktualisieren Sie den Namen des Ordners im Feld **Remotestamm**, um den Ordner in Ihrem Stammverzeichnis (*~*) auf dem Mac anzugeben, der von dem Remote-Agent verwendet wird. Standardmäßig verwendet der Remote-Agent "/Users/`username`/vcremote" als Remotestamm.

1. Wählen Sie **OK** aus, um die Verbindungseinstellungen für die Remotekopplung zu speichern.

Visual Studio verwendet jedes Mal dieselben Information, um die Verbindung mit dem Remote-Agent auf Ihrem Mac herzustellen. Es ist nicht erforderlich, Visual Studio erneut mit dem Remote-Agent zu koppeln, es sei denn, Sie generieren ein neues Sicherheitszertifikat auf Ihrem Mac oder ändern dessen Hostnamen oder IP-Adresse.

##  <a name="GeneratePIN"></a> Generate a new security PIN

Wenn Sie den Remote-Agent erstmals starten, ist die generierte PIN für einen begrenzten Zeitraum (standardmäßig 10 Minuten) gültig. Wenn Sie Visual Studio nicht vor Ablauf dieses Zeitraums mit dem Remote-Agent koppeln, müssen Sie eine neue PIN generieren.

#### <a name="to-generate-a-new-pin"></a>So generieren Sie eine neue PIN

1. Halten Sie den Agent an, oder öffnen Sie ein zweites Terminal-App-Fenster auf Ihrem Mac, und verwenden Sie dieses, um den Befehl einzugeben.

1. Geben Sie diesen Befehl in der Terminal-App ein:

   `vcremote generateClientCert`

   Der Remote-Agent generiert eine neue temporäre PIN. Wiederholen Sie die Schritte unter [Konfigurieren des Remote-Agents in Visual Studio](#ConfigureVS), um Visual Studio mithilfe der neuen PIN zu koppeln.

##  <a name="GenerateCert"></a> Generieren eines neuen Serverzertifikats

Aus Sicherheitsgründen sind die Serverzertifikate, die Visual Studio mit dem Remote-Agent koppeln, an die IP oder den Hostnamen Ihres Macs gebunden. Wenn sich diese Werte geändert haben, müssen Sie ein neues Serverzertifikat generieren und anschließend Visual Studio mit den neuen Werte neu konfigurieren.

#### <a name="to-generate-a-new-server-certificate"></a>So generieren Sie ein neues Serverzertifikat

1. So beenden Sie den vcremote-Agent

1. Geben Sie diesen Befehl in der Terminal-App ein:

   `vcremote resetServerCert`

1. Wenn Sie zur Bestätigung aufgefordert werden, geben Sie `Y`ein.

1. Geben Sie diesen Befehl in der Terminal-App ein:

   `vcremote generateClientCert`

   Dadurch wird eine neue temporäre PIN generiert.

1. Wiederholen Sie die Schritte unter [Konfigurieren des Remote-Agents in Visual Studio](#ConfigureVS), um Visual Studio mithilfe der neuen PIN zu koppeln.

##  <a name="ConfigureMac"></a> Configure the remote agent on the Mac

Sie können den Remoteagent mit verschiedenen Befehlszeilenoptionen konfigurieren. Beispielsweise können Sie den Port zum Überwachen der Build-Anforderungen und die maximale Anzahl an Builds angeben, die auf dem Dateisystem verwaltet werden sollen. Die Standardgrenze ist 10 Builds. Der Remote-Agent entfernt beim Herunterfahren die überzähligen Builds.

#### <a name="to-configure-the-remote-agent"></a>So konfigurieren Sie den Remote-Agenten

- Um eine vollständige Liste der Remote-Agent-Befehle anzuzeigen, geben Sie in die Terminal-App Folgendes ein:

   `vcremote --help`

- Geben Sie zum Deaktivieren des sicheren Modus und zum Aktivieren von einfachen HTTP-basierten Verbindungen Folgendes ein:

   `vcremote --secure false`

   Wenn Sie diese Option verwenden, deaktivieren Sie das Kontrollkästchen **Sicher**, und lassen Sie das Feld für die **PIN** leer, wenn Sie den Agent in Visual Studio konfigurieren.

- Geben Sie zum Angeben eines Speicherorts für Remote-Agent-Dateien Folgendes ein:

   `vcremote --serverDir directory_path`

   *&lt;directory_path&gt;* ist hierbei der Speicherort auf Ihrem Mac, in welchem Protokolldateien, Builds und Serverzertifikate abgelegt werden. Standardmäßig handelt es sich hierbei um */Users/\<username>/vcremote*. Builds werden an diesem Speicherort nach Build-Nummer angeordnet.

- Um mithilfe eines Hintergrundprozesses `stdout` und `stderr` in einer Datei namens "server.log" zu erfassen, geben Sie Folgendes ein:

   `vcremote > server.log 2>&1 &`

   Die Datei "server.log" kann bei der Problembehandlung von Builds hilfreich sein.

- Um den Agent mit einer Konfigurationsdatei anstelle von Befehlszeilenparametern auszuführen, geben Sie Folgendes ein:

   `vcremote --config config_file_path`

   *config_file_path* ist hierbei der Pfad zu einer Konfigurationsdatei im JSON-Format. Die Startoptionen und deren Werte dürfen keine Bindestriche enthalten.

## <a name="see-also"></a>Siehe auch

- [Installieren der plattformübergreifenden Mobile-Entwicklung mit Visual C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
