---
title: Installation und Verwendung hinter einer Firewall oder einem Proxy
description: Überprüfen Sie die Domänen-URLs, Ports und Protokolle, die Sie möglicherweise auf die Whitelist setzen oder öffnen möchten, wenn Ihre Organisation eine Firewall oder einen Proxyserver verwendet.
ms.date: 07/10/2018
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bf4e4b1828253d002ab15f80584d7a8c2b2894a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954646"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Installieren und Verwenden von Visual Studio und Azure-Diensten hinter einer Firewall oder einem Proxyserver

Wenn Ihre Organisation Sicherheitsmechanismen wie eine Firewall oder einen Proxyserver verwendet, dann sollten Sie einige Domänen-URLs in die Whitelist aufnehmen und verschiedene Ports und Protokolle öffnen bzw. deren Verwendung zulassen, um eine optimale Installation und Verwendung von Visual Studio und Azure-Diensten zu gewährleisten.

* **[Installieren von Visual Studio](#install-visual-studio)**: Diese Tabellen enthalten die Domänen-URLs, die Sie in die Whitelist aufnehmen müssen, um Zugriff auf alle gewünschten Komponenten und Workloads zu erhalten.

* **[Verwenden von Visual Studio und Azure-Diensten](#use-visual-studio-and-azure-services)**: Diese Tabellen enthalten die Domänen-URLs, die Sie in die Whitelist aufnehmen sollten, sowie die Ports und Protokolle, die Sie öffnen bzw. zulassen müssen, um Zugriff auf alle gewünschten Features und Dienste zu erhalten.

> [!NOTE]
> Dieser Artikel wurde für Visual Studio unter Windows geschrieben. Bestimmte Informationen gelten jedoch auch für die [Installation von Visual Studio für Mac](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) hinter einer Firewall oder einem Proxy-Server.

## <a name="install-visual-studio"></a>Installieren von Visual Studio

### <a name="urls-to-whitelist"></a>URLs für die Whitelist

Der Visual Studio-Installer lädt Dateien aus verschiedenen Domänen und den zugehörigen Downloadservern herunter, deshalb müssen Sie die folgenden URLs unter Verwendung der Benutzeroberfläche oder in Ihren Bereitstellungsskripts als vertrauenswürdige URLs in die Whitelist aufnehmen.

#### <a name="microsoft-domains"></a>Microsoft-Domänen

| Domäne | Zweck |
| - | - |
| go.microsoft.com | Einrichten der URL-Lösung |
| aka.ms | Einrichten der URL-Lösung |
| download.visualstudio.microsoft.com | Einrichten des Speicherorts für den Paketdownload |
| 0download.microsoft.com | Einrichten des Speicherorts für den Paketdownload |
| download.visualstudio.com | Einrichten des Speicherorts für den Paketdownload |
| dl.xamarin.com | Einrichten des Speicherorts für den Paketdownload |
| marketplace.visualstudio.com | Speicherort des Downloads der Visual Studio-Erweiterungen |
| visualstudio.microsoft.com | Speicherort der Dokumentation |
| docs.microsoft.com | Speicherort der Dokumentation |
| msdn.microsoft.com | Speicherort der Dokumentation |
| www\.microsoft.com | Speicherort der Dokumentation |
| \*.windows.net | Anmeldeort |
| \*.microsoftonline.com | Anmeldeort |
| \*.live.com | Anmeldeort |
| | |

#### <a name="non-microsoft-domains"></a>Nicht-Microsoft-Domänen

| Domäne | Installieren dieser Workloads |
| - | - |
| archive.apache.org | Mobile Entwicklung mit JavaScript (Cordova) |
| cocos2d-x.org | Spieleentwicklung mit C++ (Cocos) |
| download.epicgames.com | Spieleentwicklung mit C++ (Unreal Engine) |
| download.oracle.com | Mobile Entwicklung mit JavaScript (Java SDK) <br /><br />Mobile Entwicklung mit .NET (Java SDK) |
| download.unity3d.com | Spieleentwicklung mit Unity (Unity) |
| netstorage.unity3d.com | Spieleentwicklung mit Unity (Unity) |
| dl.google.com | Mobile Entwicklung mit JavaScript (Android SDK und NDK, Emulator) <br /><br />Mobile Entwicklung mit .NET (Android SDK und NDK, Emulator) |
| www\.incredibuild.com | Spieleentwicklung mit C++ (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Spieleentwicklung mit C++ (IncrediBuild) |
| www\.python.org | Python-Entwicklung (Python) <br /><br />Data Science und analytische Anwendungen (Python) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Verwenden von Visual Studio und Azure-Diensten

### <a name="urls-to-whitelist-and-ports-and-protocols-to-open"></a>URLs für Whitelist und zu öffnende Ports und Protokolle

Um sicherzustellen, dass Sie bei Verwendung von Visual Studio oder Azure-Diensten hinter einer Firewall oder einem Proxyserver Zugriff auf alle benötigten Komponenten haben, müssen Sie die folgenden URLs in die Whitelist aufnehmen und diese Ports und Protokolle öffnen bzw. zulassen.

| Dienst oder Szenario | DNS-Endpunkt | Protokoll | Port | Beschreibung |
| - | - | - | - | - |
| URL<br>Auflösung | go.microsoft.com<br><br>aka.ms | | | Dient dem Verkürzen von URLs, die anschließend in längere URLs aufgelöst werden. |
| Startseite | vsstartpage.blob.core.windows.net | | 443 | Dient der Anzeige Neuigkeiten für Entwickler auf der Startseite in Visual Studio. |
| Ziel-<br> benachrichtigungs- <br>Dienst | targetednotifications.azurewebsites.net <br><br>www.research.net | | 80<br><br>443 | Dient zum Filtern einer globalen Liste mit Benachrichtigungen in eine Liste, die nur für bestimmte Computertypen/Verwendungsszenarien gilt. |
| Erweiterung <br>auf Update überprüfen | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | | 443 | Dient zum Bereitstellen von Benachrichtigungen wenn für eine installierte Erweiterung ein Update verfügbar ist. <br><br> Wird als Anmeldestandort verwendet. |
| AI-Projekt <br>Integration | az861674.vo.msecnd.net | | 443<br> | Wird zum Konfigurieren neuer Projekte und zum Senden von Nutzungsdaten an Ihr registriertes Application Insights-Konto verwendet. |
| Code Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | | 443 | Wird verwendet, um im Editor Informationen anzuzeigen: letzte Aktualisierung einer Datei, Zeitachse der Änderungen, von den Änderungen betroffene Arbeitselemente, Autoren usw. |
| Experimentell <br>Featureaktivierung | visualstudio-devdiv-c2s.msedge.net | | 80 | Wird zum Aktivieren experimenteller neuer Features oder Featureänderungen verwendet. |
| Identitätsbadge <br>(Benutzername und Avatar)<br>und <br>Roamingeinstellungen | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net | | 443 | Wird verwendet, um den Benutzernamen und Avatar in der IDE anzuzeigen. <br><br> Stellt sicher, dass Einstellungsänderungen von Computer zu Computer übernommen werden. |
| Remoteeinstellungen | az700632.vo.msecnd.net | | 443 | Dient dem Deaktivieren von Erweiterungen, die bekanntermaßen Probleme in Visual Studio verursachen. |
| Windows-Tools | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https | 443 | Wird für Windows-App Store-Szenarien verwendet. |
| JSON-Schema <br>Suche <br><br>JSON-Schema <br>Definition<br><br>JSON-Schema <br>Unterstützung für <br>Azure-Ressourcen | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http<br>https<br><br>http<br><br>https | 80<br>443 <br><br> 443<br><br>443 | Wird zum Ermitteln und Herunterladen von JSON-Schemas verwendet, die der Benutzer beim Bearbeiten von JSON-Dokumenten möglicherweise verwendet. <br><br>Dient dem Abruf des Schemas zur Metavalidierung für JSON.<br><br>Wird zum Abrufen des aktuellen Schemas für Azure Resource Manager-Bereitstellungsvorlagen verwendet. |
| NPM-Paket <br>Erkennung | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https<br><br>http/s<br><br>https | 443<br><br>80/443<br><br>443 | Wird zur Suche nach NPM-Paketen benötigt und zur clientseitigen Skriptpaketinstallation in Webprojekten verwendet. |
| Bower-Paket<br> Symbole<br><br>Bower-Paket <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https | 80<br><br>443<br>80<br>443 | Stellt das standardmäßige Bower-Paketsymbol bereit.  <br><br>Ermöglicht die Suche nach Bower-Paketen. |
| NuGet<br><br>NuGet-Paket<br> Erkennung | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https<br><br>http/s | 443<br><br>80/443<br> | Dient der Überprüfung von signierten NuGet-Paketen.<br><br>Erforderlich für die Suche nach NuGet-Paketen und -Versionen. |
| GitHub-Repositoryinformationen | api.github.com | https | 443 | Erforderlich zum Abrufen zusätzlicher Informationen zu Bower-Paketen. |
| Weblinter | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http | 80 | |
| Cookiecutter<br>Explorer-Vorlage<br>Erkennung <br><br>Cookiecutter <br>Explorer-Projekt<br> Erstellung | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https | 443<br> | Wird zum Ermitteln von Onlinevorlagen im empfohlenen Feed sowie in GitHub-Repositorys verwendet. <br><br>Dient zum Erstellen eines Projekts aus einer Cookiecutter-Vorlage, die eine einmalige Installation eines Cookiecutter-Python-Pakets aus dem Python-Paketindex (PyPI) erfordert. |
| Python-Paket <br>Erkennung<br><br>Python-Paket <br>Verwaltung<br><br>Python <br>Neues Projekt <br>Vorlagen | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https | 443 | Ermöglicht die Suche nach PIP-Paketen.<br><br>Installiert PIP automatisch, sofern nicht vorhanden. <br><br> Wird zur Erstellung verwendet. <br><br>Wird zum Auflösen der folgenden Python-Projektvorlagen im Dialogfeld für ein neues Projekt in Cookiecutter-Vorlagen-URLs verwendet:<br> – Klassifiziererprojekt<br>– Clusteringprojekt <br> – Regressionsprojekt <br> – PyGame unter Verwendung von PyKinect <br> – Pyvot-Projekt |
| Office Web <br>Add-In <br> Manifest <br>Überprüfung <br>Dienst | verificationservice.osi.office.net | https | 443 | Wird zum Validieren von Manifesten für Office Web-Add-Ins verwendet. |
| SharePoint- und  <br>Office-Add-ins | sharepoint.com | https | 443 | Wird zum Veröffentlichen und Testen von SharePoint- und Office-Add-Ins in SharePoint Online verwendet. |
| Workflow-Manager- <br>Testdienst-<br> Host | | http | 12292 | Eine Firewall, die zum Testen von SharePoint-Add-Ins mit Workflows automatisch erstellt wird. |
| Automatisch gesammelte <br>Zuverlässigkeitsstatistiken <br>und weitere Daten des <br>Programms zur Verbesserung <br>der Benutzerfreundlichkeit<br> für Azure SDK und <br>SQL-Tools <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https | 443 | Wird zum Senden von Zuverlässigkeitsstatistiken (Daten zu Abstürzen/Stillständen) vom Benutzer an Microsoft verwendet. Die eigentlichen Abbilder zu Abstürzen/Stillständen werden weiterhin hochgeladen, wenn die Windows-Fehlerberichterstattung aktiviert ist. Es werden lediglich statistische Informationen unterdrückt. <br>Wird verwendet, um anonyme Nutzungsmuster der Azure-Tools SDK-Erweiterung sowie Nutzungsmuster der SQL-Tools für Visual Studio offenzulegen. |
| Visual Studio <br> Programm zur Verbesserung <br>der Benutzerfreundlichkeit (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https | 443 | Dient zum Sammeln von anonymen Nutzungsmustern und Fehlerprotokollen. <br><br>Hiermit werden Probleme mit einer nicht reagierenden Benutzeroberfläche nachverfolgt. |
| Erstellung und<br>Verwaltung von <br>Azure-Ressourcen | management.azure.com <br>management.core.windows.net | https | 443 | Wird verwendet, um Azure-Websites oder andere Ressourcen zur Unterstützung der Veröffentlichung von Webanwendungen, Azure-Funktionen oder WebJobs zu unterstützen. |
| Überprüfung auf aktualisierte Tools <br>und Erweiterungsempfehlungen <br>für die Webveröffentlichung | marketplace.visualstudio.com | https | 443 | Wird verwendet, um nach aktualisierten Veröffentlichungstools zu suchen. Sofern deaktiviert, wird eine potenziell empfohlene Erweiterung für die Webveröffentlichung möglicherweise nicht angezeigt. |
| Aktualisierte Informationen zu Endpunkten <br>für die Erstellung von Azure-Ressourcen | \*.blob.core.windows.net | https | 443 | Hiermit werden die Endpunkte für die Erstellung von Azure-Ressourcen für bestimmte Azure-Dienste aktualisiert. Sofern deaktiviert, werden stattdessen die zuletzt heruntergeladenen oder integrierten Endpunktstandorte verwendet. |
| Remotedebuggen und <br>Remoteprofilerstellung für <br>Azure Websites | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | | 4022 | Hiermit wird der Remotedebugger an Azure Websites angefügt. Sofern deaktiviert, funktioniert das Anfügen des Remotedebuggers an Azure Websites nicht. |
| Active Directory <br>Graph | graph.windows.net | https | 443 | Wird verwendet, um neue Azure Active Directory-Anwendungen bereitzustellen. Wird auch vom verbundenen Office 365 MSGraph-Dienstanbieter verwendet. |
| Überprüfung auf <br>CLI-Update für <br>Azure Functions | functionscdn.azureedge.net | https | 443 | Wird verwendet, um nach aktualisierten Versionen der Azure Functions-CLI zu suchen. Sofern deaktiviert, wird stattdessen eine zwischengespeicherte Kopie (oder die Kopie der Azure Functions-Komponente) der CLI verwendet. |
| Cordova | npmjs.org<br>gradle.org | http/s | 80/443 | HTTP wird für Gradle-Downloads während der Builderstellung verwendet; HTTP wird zum Einschließen von Cordova-Plug-Ins in Projekten genutzt. |
| Cloud-Explorer | 1. &#60;Clusterendpunkt&#62; <br>Service Fabric <br>2. &#60;Verwaltungsendpunkt&#62;<br>Allgemeine Cloudoberfläche <br>3. &#60;Graph-Endpunkt&#62;<br>Allgemeine Cloudoberfläche<br>4. &#60;Speicherkontoendpunkt&#62;<br>Speicherknoten <br>5. &#60;Azure-Portal-URLs&#62;<br>Allgemeine Cloudoberfläche <br>6. &#60;Key Vault-Endpunkte&#62; <br>Azure Resource Manager-VM-Knoten<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric-Remotedebuggen und ETW-Ablaufverfolgungen | <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7: TCP | 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. Dynamisch | 1. Beispiel: test12.eastus.cloudapp.com<br>2. Ruft Abonnements ab und ruft Azure-Ressourcen ab bzw. verwaltet sie.<br>3. Ruft Azure Stack-Abonnements ab.<br>4. Verwaltet Speicherressourcen (Beispiel: mystorageaccount.blob.core.windows.net).<br>5. Kontextmenüoption „In Portal öffnen“ (öffnet eine Ressource im Azure-Portal).<br>6. Erstellt und verwaltet Schlüsselspeicher für das VM-Debugging (Beispiel: myvault.vault.azure.net). <br><br>7. Hiermit wird ein Portblock basierend auf der Anzahl von Knoten im Cluster sowie den verfügbaren Ports dynamisch zugewiesen. <br><br>Ein Portblock versucht, die dreifache Anzahl von Knoten mit mindestens zehn Ports abzurufen.<br><br>Für Streamingablaufverfolgungen wird versucht, den Portblock ab 810 zu erhalten. Wenn einer dieser Ports bereits verwendet wird, wird versucht, den nächsten Block abzurufen usw. (Wenn der Load Balancer leer ist, werden die Ports ab 810 sehr wahrscheinlich verwendet.) <br><br>Ähnlich werden für das Debugging vier Sätze an Portblocks reserviert: <br>– connectorPort: 30398, <br>– forwarderPort: 31398, <br>– forwarderPortx86: 31399,<br>– fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3.  management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;Benutzerclouddienst&#62;.cloudapp.net <br> &#60;Benutzer-VM&#62;.&#60;Region&#62;.azure.com | 1. RDP <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. TCP | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6. a) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1.  Remotedesktop zu Cloud Services-VM <br><br> 2.  Speicherkontokomponente der privaten Diagnosekonfiguration <br><br> 3.  Azure-Portal <br><br> 4. Server-Explorer – Azure Storage &#42; entspricht dem vom Kunden benannten Speicherkonto  <br><br> 5.  Links zum Öffnen des Portals &#47; Download des Abonnementzertifikats &#47; Veröffentlichen der Einstellungsdatei <br><br>6. a) Lokaler Connectorport für das Remotedebuggen von Clouddienst und VM<br> 6. b) Öffentlicher Connectorport für das Remotedebuggen von Clouddienst und VM <br> 6. c) Lokaler Weiterleitungsport für das Remotedebuggen von Clouddienst und VM <br> 6. d) Öffentlicher Weiterleitungsport für das Remotedebuggen von Clouddienst und VM  <br> 6. e) Lokaler Port des Programms zum Hochladen von Dateien für das Remotedebuggen von Clouddienst und VM <br> 6. f) Öffentlicher Port des Programms zum Hochladen von Dateien für das Remotedebuggen von Clouddienst und VM |
| Service Fabric | 1. <br>ocs.Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https | 443 | 1. Dokumentation <br><br> 2. Feature zur Clustererstellung <br><br>3. &#42; ist der Azure Key Vault-Name (Beispiel: test11220180112110108.vault.azure.net)  <br><br>  4. &#42; ist dynamisch (Beispiel: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Snapshot <br>Debugger | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. Concord <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (abhängig von Visual Studio-Version) | 1. Abfrage-JSON-Datei für App Service-SKU-Größe <br>2. Verschiedene Azure-RM-Aufrufe <br>3. Aufruf zur Standortaufwärmung über  <br>4. Vom Kunden festgelegter App Service-Kudu-Endpunkt <br>5. Auf nuget.org veröffentlichte Erweiterungsversion für die Abfragewebsite <br>6. Kanal für Remotedebuggen |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https | 443 | Dient zum Anzeigen, Übermitteln, Ausführen und Verwalten von ASA-Aufträgen. <br><br> Wird verwendet, um HDI-Cluster zu durchsuchen und HDI-Aufträge zu übermitteln, zu diagnostizieren und zu debuggen. |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Wird verwendet, um Auftrage zu kompilieren, zu übermitteln, anzuzeigen, zu diagnostizieren und zu debuggen. Dient zum Durchsuchen von ADLS-Dateien und zum Hoch- und Herunterladen von Dateien. |
| Paketerstellungsdienst | [account].visualstudio.com <br/> [Konto].\*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | Die Domänen \*.npmjs.org, \*.nuget.org und \*.nodejs.org sind nur für bestimmte Buildtaskszenarios erforderlich (z. B.: NuGet-Toolinstaller, Node Tool-Installationsprogramm) oder wenn Sie öffentliche Upstreams mit Ihren Feeds verwenden müssen. Die anderen drei Domänen werden für wichtige Funktionen des Paketerstellungsdiensts benötigt. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com | | | Wird zum Herstellen einer Verbindung mit Azure DevOps Services verwendet. |
| | | | | |

## <a name="troubleshoot-network-related-errors"></a>Behandlung netzwerkbezogener Fehler

Gelegentlich kann es zu netzwerk- oder proxybezogenen Fehlern kommen, wenn Sie Visual Studio hinter einer Firewall oder einem Proxyserver installieren oder verwenden. Weitere Informationen zu Lösungen für diese Fehlermeldungen finden Sie unter [Beheben von Netzwerkfehlern beim Installieren oder Verwenden von Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="get-support"></a>Support aufrufen

Für installationsbezogene Probleme wird außerdem ein [**Livechat**](https://visualstudio.microsoft.com/vs/support/#talktous) (nur auf Englisch) als Supportoption angeboten.

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Schlagen Sie ein Feature vor, verfolgen Sie Produktprobleme nach, und finden Sie Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/).
* Sie können Ihr [GitHub](https://github.com/)-Konto verwenden, um über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufzunehmen.

## <a name="see-also"></a>Siehe auch

* [Erstellen einer Netzwerkinstallation von Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Beheben von Netzwerkfehlern in Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Installieren hinter einer Firewall oder einem Proxy-Server (Visual Studio für Mac)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
