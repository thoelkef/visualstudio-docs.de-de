---
title: "Remotearbeitsbereiche mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/30/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5778c9cf-564d-47b0-8d64-e5dc09162479
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b708aa33b490cb01ad1e1f31664804f658f1aa55
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="setting-up-remote-workspaces"></a>Einrichten von Remotearbeitsbereichen

In diesem Thema wird erklärt, wie ein Remoteserver mit SSL und einem geeigneten R-Dienst konfiguriert wird. So kann R Tools für Visual Studio (RTVS) mit einem Remotearbeitsbereich auf diesem Server verbunden werden. 

- [Anforderungen an Remotecomputer](#remote-computer-requirements)
- [Installieren eines SSL-Zertifikats](#install-an-ssl-certificate)
- [Installieren von R Services](#install-r-services)
- [Konfigurieren von R Services](#configure-r-services)
- [Problembehandlung](#troubleshooting)

## <a name="remote-computer-requirements"></a>Anforderungen an Remotecomputer

- Windows 10, Windows Server 2016 oder Windows Server 2012 R2 RTVS erfordert ebenfalls
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) oder höher

## <a name="install-an-ssl-certificate"></a>Installieren eines SSL-Zertifikats

RTVS erfordert, dass die gesamte Kommunikation mit einem Remoteserver über HTTP abläuft, wofür ein SSL-Zertifikat auf dem Server notwendig ist. Sie können entweder ein von einer vertrauenswürdigen Zertifizierungsstelle signiertes Zertifikat (empfohlen) oder ein selbstsigniertes Zertifikat verwenden. (Ein selbstsigniertes Zertifikat bewirkt, dass RTVS Warnungen auslöst, wenn eine Verbindung besteht). Unabhängig davon, für welches Sie sich entscheiden, muss das Zertifikat auf dem Computer installiert werden und den Zugriff auf seinen privaten Schlüssel ermöglichen.

### <a name="obtaining-a-trusted-certificate"></a>Abrufen eines vertrauenswürdigen Zertifikats

Ein vertrauenswürdiges Zertifikat wird von einer Zertifizierungsstelle ausgestellt (Informationen finden Sie auf [Wikipedia zu Zertifizierungsstellen](https://en.wikipedia.org/wiki/Certificate_authority)). Wie bei der Ausstellung eines Personalausweises ist auch der Prozess der Ausstellung eines vertrauenswürdigen Zertifikats länger und es fallen mögliche Gebühren an, dafür wird die Echtheit der Anforderung und des Anfordernden überprüft.

Das Schlüsselfeld, das im Zertifikat enthalten sein muss, ist der vollqualifizierte Domainname Ihres R-Servercomputers. Die Zertifizierungsstelle fordert einen Nachweis, dass Sie berechtigt sind, einen neuen Server für die Domäne zu erstellen, zu der Ihr Server gehört.

Weitere Informationen finden Sie auf Wikipedia unter [Public-Key-Zertifikat](https://en.wikipedia.org/wiki/Public_key_certificate).

### <a name="obtaining-a-self-signed-certificate"></a>Selbstsignierte Zertifikate

Verglichen mit einem Zertifikat von einer vertrauenswürdigen Zertifizierungsstelle ist ein selbstsigniertes Zertifikat wie ein selbst erstellter Ausweis. Dieser Prozess ist zwar einfacher als die Zusammenarbeit mit einer vertrauenswürdigen Zertifikatsstelle, entbehrt aber auch einer starken Authentifizierung. Das bedeutet, dass ein Angreifer ein nicht signiertes Zertifikat durch ein eigenes ersetzen und den gesamten Verkehr zwischen dem Client und dem Server abfangen kann. *Selbstsignierte Zertifikate sollten daher nur für Testszenarios innerhalb eines vertrauenswürdigen Netzwerks eingesetzt werden, niemals in der Produktion.*

Aus diesem Grund gibt RTVS immer die folgende Warnung aus, wenn eine Verbindung mit einem Server mit einem selbstsignierten Zertifikat hergestellt wird:

![Dialogfeld „Warnung zu selbstsigniertem Zertifikat“](media/workspaces-remote-self-signed-certificate-warning.png)

So erstellen Sie ein selbstsigniertes Zertifikat

1. Melden Sie sich mit einem Administratorkonto auf dem R-Servercomputer an.
1. Öffnen Sie eine neue PowerShell-Administratorbefehlszeile, führen Sie den folgenden Befehl aus, und ersetzen Sie dabei `"remote-machine-name"` durch den vollqualifizierten Domänennamen des Servercomputers.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Wenn Sie PowerShell zuvor noch nie auf dem R-Servercomputer ausgeführt haben, führen Sie den folgenden Befehl aus, um die explizite Ausführung von Befehlen zu aktivieren:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Hintergrundinformationen finden Sie auf Wikipedia unter [Self-signed certificate](https://en.wikipedia.org/wiki/Self-signed_certificate).

### <a name="installing-the-certificate"></a>Installieren des Zertifikats

Um das Zertifikat auf dem Remotecomputer zu installieren, führen Sie `certlm.msc` (Zertifikat-Manager) über eine Befehlszeile aus. Klicken Sie mit der rechten Maustaste auf den Ordner **Eigene Zertifikate**, und wählen Sie den Befehl **Alle Aufgaben > Import** aus:

![Befehl „Zertifikat importieren“](media/workspaces-remote-certificate-import.png)


### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>Gewähren von Leseberechtigungen für den privaten Schlüssel des SSL-Zertifikats

Sobald das Zertifikat importiert wurde, gewährt das `NETWORK SERVICE`-Konto Leseberechtigungen für den privaten Schlüssel, wie im Folgenden beschrieben. `NETWORK_SERVICE` ist das Konto, das für die Ausführung des R Services-Brokers verwendet wird. Mit diesem Dienst werden eingehende SSL-Verbindungen mit dem Servercomputer beendet.

1. Führen Sie `certlm.msc` (Zertifikat-Manager) an einer Administratorbefehlszeile aus.
1. Erweitern Sie **Personal > Certificates** (Persönlich > Zertifikate), klicken Sie mit der rechten Maustaste auf das Zertifikat, und wählen Sie **Alle Aufgaben > Privatschlüssel verwalten**.
1. Klicken Sie mit der rechten Maustaste auf das Zertifikat, und wählen Sie unter „Alle Aufgaben“ den Befehl „Private Schlüssel verwalten“ aus.
1. Wählen Sie im sich daraufhin öffnenden Dialogfeld **Hinzufügen** aus, und geben Sie `NETWORK SERVICE` als Kontoname ein:

    ![Dialogfeld „Private Schlüssel verwalten“, NETWORK_SERVICE wird hinzugefügt](media/workspaces-remote-manage-private-key-dialog.png)

1. Wählen Sie **OK** zweimal aus, um die Dialogfelder zu schließen und die Änderungen zu übernehmen.


## <a name="install-r-services"></a>Installieren von R Services

Um R-Code auszuführen, muss auf dem Remotecomputer ein R-Interpreter wie folgt installiert sein:

1. Laden Sie einen der folgenden herunter, und installieren Sie ihn:

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R für Windows](https://cran.r-project.org/bin/windows/base/)

    Beide verfügen über identische Funktionen, aber Microsoft R Open profitiert von zusätzlichen hardwarebeschleunigten Bibliotheken für Lineare Algebra, die durch die [Intel Math Kernel Library](https://software.intel.com/intel-mkl) bereitgestellt werden.

1. Führen Sie den [R Services-Installer](https://aka.ms/rtvs-services) aus, und starten Sie den Computer neu, wenn Sie dazu aufgefordert werden. Der Installer führt die folgenden Aktionen aus:

    -   Unter `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` einen Ordner erstellen und alle erforderlichen Binärdateien kopieren
    -   `RHostBrokerService` und `RUserProfileService` installieren und für den automatischen Start konfigurieren
    -   Den `seclogon`-Dienst für automatischen Start konfigurieren
    -   Den eingehenden Firewallregeln auf dem Standardport 5444 `Microsoft.R.Host.exe` und `Microsoft.R.Host.Broker.exe` hinzufügen

R Services wird automatisch gestartet, wenn der Computer neu startet:

- Der **R-Hostbrokerdienst** verarbeitet den gesamten HTTPS-Datenverkehr zwischen Visual Studio und dem Prozess, in dem der R-Code auf dem Computer ausgeführt wird.
- **R User Profile Service** ist eine privilegierte Komponente, die für die Erstellung von Windows-Benutzerprofilen zuständig ist. Dieser Dienst wird aufgerufen, wenn ein neuer Benutzer sich zum ersten Mal auf dem R-Servercomputer anmeldet.

Sie können diese Dienste in der Diensteverwaltungskonsole (`compmgmt.msc`) anzeigen.  

## <a name="configure-r-services"></a>Konfigurieren von R Services

Wenn R Services auf dem Remotecomputer ausgeführt wird, müssen Sie auch Benutzerkonten erstellen, Firewallregeln festlegen und Azure-Netzwerke sowie das SSL-Zertifikat konfigurieren.

1. Benutzerkonten: Erstellen Sie ein Konto für jeden Benutzer, der auf den Remotecomputer zugreift. Sie können entweder ein lokales Standardbenutzerkonto (ohne Berechtigungen) erstellen, oder Sie können Ihren R-Servercomputer mit Ihrer Domäne verknüpfen und der `Users`-Sicherheitsgruppe die angemessenen Sicherheitsgruppen hinzufügen.
1. Firewallregeln: `R Host Broker` lauscht standardmäßig an TCP-Port 5444. Daher müssen Sie sicherstellen, dass die Windows-Firewallregeln für eingehenden und ausgehenden Datenverkehr aktiviert sind (der ausgehende Verkehr ist für die Installation von Paketen und ähnliche Szenarios notwendig).  Der R Services-Installer legt diese Regeln automatisch für die integrierte Windows-Firewall fest. Wenn Sie eine Drittanbieter-Firewall verwenden, müssen Sie Port 5444 für den `R Host Broker` jedoch manuell öffnen.
1. Azure-Konfiguration: Wenn der Remotecomputer ein virtueller Azure-Computer ist, müssen Sie Port 5444 für eingehenden Datenverkehr auch innerhalb von Azure-Netzwerken öffnen, die unabhängig von der Windows-Firewall sind. Weitere Informationen finden Sie in der Azure-Dokumentation unter [Filtern des Netzwerkdatenverkehrs mit Netzwerksicherheitsgruppen](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg).
1. Weisen Sie den R-Hostbroker an, ein bestimmtes SSL-Zertifikat zu laden: Wenn Sie das Zertifikat auf einem Intranetserver installieren, ist der vollqualifizierte Domänenname Ihres Servers wahrscheinlich mit dem NETBIOS-Namen identisch. In diesem Fall müssen Sie nichts tun, da das Standardzertifikat geladen wird.

    Wenn Sie Ihr Zertifikat allerdings auf einem Server mit Internetzugriff (z.B. einer Azure-VM) installieren, verwenden Sie den vollqualifizierten Domänenname (Fully Qualified Domain Name, FQDN) des Servers, da der FQDN eines mit dem Internet verbundenen Servers nie mit dem NETBIOS-Namen übereinstimmt.

    Navigieren Sie zum Verwenden des FQDN zum Speicherort von R Services (standardmäßig `%PROGRAM FILES%\R Remote Service for Visual Studio\1.0`), öffnen Sie die Datei `Microsoft.R.Host.Broker.Config.json` in einem Text-Editor, ersetzen Sie deren Inhalt durch Folgendes, und weisen Sie dabei CN dem FQDN Ihres Servers zu, z.B. `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Speichern Sie die Datei, und starten Sie den Computer neu, um die Änderungen zu übernehmen.

## <a name="troubleshooting"></a>Problembehandlung

**Der R-Servercomputer reagiert nicht, was kann ich tun?**

Versuchen Sie, den Remotecomputer über die Befehlszeile zu pingen: `ping remote-machine-name`. Wenn der Ping fehlschlägt, stellen Sie sicher, dass der Computer angeschaltet ist.

**F. Das interaktive R-Fenster meldet, dass der Remotecomputer an ist. Aber warum wird der Dienst nicht ausgeführt?**

Es gibt drei mögliche Gründe:

-   [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) oder höher ist nicht auf dem Computer installiert.
-   Für eingehende und ausgehende Verbindungen an Port 5444 sind keine Firewallregeln für `Microsoft.R.Host.Broker` und `Microsoft.R.Host` aktiviert.
-   Es wurde kein SSL-Zertifikat mit `CN=<remote-machine-name>` installiert.

Starten Sie den Computer nach einer der oben beschriebenen Änderungen neu. Stellen Sie dann sicher, dass `RHostBrokerService` und `RUserPofileService` entweder über den Task-Manager (Registerkarte „Dienste“) oder `services.msc` ausgeführt werden.

**F. Warum meldet das interaktive Fenster während der Verbindungserstellung mit dem R-Server „401 Zugriff verweigert“?**

Es gibt zwei mögliche Ursachen:

- Es ist sehr wahrscheinlich, dass das `NETWORK SERVICE`-Konto keinen Zugriff auf den privaten Schlüssel des SSL-Zertifikats hat. Folgen Sie der vorherigen Anleitung, um sicherzustellen, dass `NETWORK SERVICE` Zugriff auf den privaten Schlüssel hat.
- Stellen Sie sicher, dass der `seclogon`-Dienst ausgeführt wird. Verwenden Sie `services.msc`, um `seclogon` für den automatischen Start zu konfigurieren.                                                         
**F. Warum meldet das interaktive Fenster während der Verbindungserstellung mit dem R-Server „404 Nicht gefunden“?**

Dieser Fehler liegt wahrscheinlich an fehlenden verteilbaren Visual C++-Bibliotheken. Überprüfen Sie das interaktive R-Fenster, um festzustellen, ob eine Meldung über eine fehlende Bibliothek (DLL) vorliegt. Überprüfen Sie dann, ob Visual C++ Redistributable für Visual Studio 2015 und R installiert sind.

**F. Ich kann über das interaktive R-Fenster nicht auf Internet/Ressource zugreifen. Was kann ich tun?**

Stellen Sie sicher, dass die Firewallregeln für `Microsoft.R.Host.Broker` und `Microsoft.R.Host` ausgehenden Zugriff auf Port 5444 zulassen. Starten Sie den Computer neu, nachdem Sie die Änderungen vorgenommen haben.

**F. Ich habe alle genannten Lösungen ausprobiert, und es funktioniert trotzdem nicht. Was nun?**

Sehen Sie in den Protokolldateien in `C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp` nach. Dieser Ordner enthält eine separate Protokolldatei für jede Instanz des R-Brokerdiensts, die ausgeführt wurde. Immer wenn der Dienst neu gestartet wird, wird eine neue Protokolldatei erstellt. Überprüfen Sie die aktuellste Protokolldatei auf Anzeichen, wo der Fehler liegen könnte.

