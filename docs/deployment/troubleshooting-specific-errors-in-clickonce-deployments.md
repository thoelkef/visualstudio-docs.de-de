---
title: Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 40c679811f137e77909395042d91d0458c874d90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen
Dieses Thema listet die folgenden allgemeinen Fehler, die auftreten können, während der Bereitstellung einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung, und beschreibt die Schritte, um jedes Problem zu beheben.  
  
## <a name="general-errors"></a>Allgemeine Fehler  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Wenn Sie versuchen, eine Application-Datei zu finden, geschieht nichts, oder in Internet Explorer XML gerendert oder erhalten Sie ein Dialogfeld Ausführen oder Speichern unter  
 Dieser Fehler wird wahrscheinlich durch nicht korrekt auf dem Server oder Client registriert Inhaltstypen (auch bekannt als MIME-Typen) verursacht.  
  
 Stellen Sie zunächst sicher, dass der Server konfiguriert ist, um die Erweiterung .application Inhaltstyp "Application/X-ms-Application" zuzuordnen.  
  
 Wenn der Server ordnungsgemäß konfiguriert ist, stellen Sie sicher, dass die [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] auf Ihrem Computer installiert ist. Wenn die [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] installiert ist, und Sie werden weiterhin angezeigt wird dieses Problem deinstallieren und Neuinstallieren von der [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] den Inhaltstyp auf dem Client erneut zu registrieren.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Fehlermeldung lautet: "kann nicht zum Abrufen der Anwendung. Dateien fehlt in der Bereitstellung"oder"Anwendungsdownloads wurde unterbrochen, überprüfen Sie Netzwerkfehler und versuchen Sie es später"  
 Diese Meldung gibt an, dass eine oder mehrere Dateien, die darauf verweist die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste können nicht heruntergeladen werden. Die einfachste Möglichkeit zum Debuggen dieses Fehlers ist die URL übertragen, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] heruntergeladen werden kann. Hier sind einige möglichen Ursachen:  
  
-   Wenn die Protokolldatei "(403) unzulässig" den Text oder "(404) nicht gefunden," Überprüfen Sie, ob der Webserver ist so konfiguriert, dass es Herunterladen dieser Datei nicht blockiert. Weitere Informationen finden Sie unter [Probleme mit der Server- und Clientkonfiguration in ClickOnce-Bereitstellungen](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Wenn Sie die config-Datei vom Server blockiert wird, finden Sie im Abschnitt "Fehler herunterladen, wenn Sie versuchen, installieren eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung mit einer .config-Datei" weiter unten in diesem Thema.  
  
-   Bestimmen, ob dies aufgetreten ist, da die `deploymentProvider` URL im Bereitstellungsmanifest verweist auf einen anderen Speicherort als die URL für die Aktivierung verwendet.  
  
-   Stellen Sie sicher, dass alle Dateien auf dem Server vorhanden sind; die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Protokoll sollte Aufschluss darüber, welche Datei nicht gefunden wurde.  
  
-   Sehen Sie, ob Probleme mit der Netzwerkkonnektivität vorhanden sind; Diese Meldung kann angezeigt werden, wenn Ihre Clientcomputer während des Downloads offline geschaltet.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Herunterladen Sie Fehler, wenn Sie versuchen, eine ClickOnce-Anwendung zu installieren, die eine config-Datei  
 Standardmäßig enthält eine Visual Basic-Windows-basierte Anwendung eine Datei "App.config". Wenn ein Benutzer versucht, die von einem Webserver, der mithilfe von Windows Server 2003 installiert werden, da das Betriebssystem die Installation der config-Dateien aus Sicherheitsgründen blockiert werden ein Problem vor. Damit kann die config-Datei installiert werden, klicken Sie auf **Dateierweiterung ".deploy" verwenden** in der **Veröffentlichungsoptionen** (Dialogfeld).  
  
 Sie müssen die Inhaltstypen (auch bekannt als MIME-Typen) auch für .application, Manifest und Dateien ".deploy" entsprechend festlegen. Weitere Informationen finden Sie in der Dokumentation zu Ihrem Webserver.  
  
 Weitere Informationen finden Sie unter "Windows Server 2003: Gesperrte Inhaltstypen" im [Server- und Client-Konfigurationsprobleme in ClickOnce-Bereitstellungen](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Fehlermeldung: "Der Anwendung ist nicht ordnungsgemäß formatiert." Protokolldatei enthält "XML-Signatur ist ungültig."  
 Stellen Sie sicher, dass Sie die Manifestdatei aktualisiert und erneut signiert. Veröffentlichen Sie die Anwendung mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder verwenden Sie Mage zum Signieren der Anwendung erneut aus.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Die Anwendung auf dem Server aktualisiert, aber der Client wird das Update nicht heruntergeladen  
 Dieses Problem möglicherweise gelöst werden, indem Sie eines der folgenden Aufgaben:  
  
-   Überprüfen Sie die `deploymentProvider` URL im Bereitstellungsmanifest. Stellen Sie sicher, dass Sie die Bits am gleichen Speicherort aktualisiert werden, die `deploymentProvider` verweist auf.  
  
-   Überprüfen Sie das Updateintervall im Bereitstellungsmanifest. Wenn dieses Intervall auf einem regelmäßigen Intervall aus, z. B. einmal alle sechs Stunden festgelegt ist [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wird nicht für ein Update überprüft, bis dieses Intervall verstrichen ist. Sie können ändern, das Manifest, um ein Update jedes Mal überprüft, die die Anwendung gestartet wird. Ändern das Updateintervall ist eine praktische Möglichkeit während der Entwicklungszeit Updates installiert sind, aber er verlangsamt anwendungsaktivierung überprüfen.  
  
-   Wiederholen Sie dann die Anwendung im Startmenü erneut zu starten. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]hat das Update möglicherweise im Hintergrund erkannt, jedoch werden Sie aufgefordert, die Bits auf die nächste Aktivierung zu installieren.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Während der Aktualisierung tritt einen Fehler mit dem folgenden Protokolleintrag: "der Verweis in der Bereitstellung entspricht nicht die Identität, die im Manifest Anwendung definiert"  
 Dieser Fehler kann auftreten, da Sie die bereitstellungs- und Anwendungsmanifeste manuell bearbeitet haben, und die Beschreibung der Identität einer Assembly in einem Manifest synchron mit den anderen sind verursacht haben. Die Identität einer Assembly, besteht der Name, Version, Kultur und öffentliches Schlüsseltoken ab. Überprüfen Sie die Identität Beschreibungen in den Manifesten, und beheben Sie etwaige Unterschiede.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Erstmaligen Aktivierung von lokalen Datenträger oder CD-ROM ist erfolgreich, aber nachfolgende Aktivierung aus dem Startmenü nicht erfolgreich ist  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]verwendet die Bereitstellungsanbieter-URL zum Empfangen von Updates für die Anwendung an. Stellen Sie sicher, dass der Speicherort, dem die URL verweist richtig ist.  
  
#### <a name="error-cannot-start-the-application"></a>Fehler: "kann nicht die Anwendung gestartet."  
 Diese Fehlermeldung gibt normalerweise an, dass es liegt ein Problem mit dem Installieren dieser Anwendung in der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zu speichern. Entweder die Anwendung einen Fehler aufweist, oder der Speicher ist beschädigt. Die Protokolldatei möglicherweise Aufschluss darüber, wo der Fehler aufgetreten ist.  
  
 Sie sollten die folgenden Schritte ausführen:  
  
-   Stellen Sie sicher, dass die Identität des Bereitstellungsmanifests, die Identität des Anwendungsmanifests und die Identität der EXE-Datei der Anwendung alle eindeutig sind.  
  
-   Stellen Sie sicher, dass die Dateipfade nicht länger als 100 Zeichen sind. Wenn Ihre Anwendung Dateipfade enthält, die zu lang sind, können Sie die Einschränkungen für die maximale Pfadlänge überschreiten, gespeichert werden können. Verkürzen Sie die Pfade, und installieren.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>PrivatePath-Einstellungen in der Konfigurationsdatei der Anwendung werden nicht berücksichtigt.  
 Um PrivatePath (Prüfpfade Fusion) zu verwenden, muss die Anwendung volle Vertrauenswürdigkeit anfordern. Versuchen Sie, das Anwendungsmanifest, um die volle Vertrauenswürdigkeit anfordern, und wiederholen Sie den Vorgang zu ändern.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Während der Deinstallation eine Meldung angezeigt, dass "Fehler beim Deinstallieren der Anwendung"  
 Diese Meldung gibt normalerweise an, dass die Anwendung bereits entfernt wurde oder der Speicher ist beschädigt. Nachdem Sie auf **OK**, **Systemsteuerungsoption** Eintrag wird entfernt.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Während der Installation wird eine Meldung angezeigt, die besagt, dass die plattformabhängigkeiten nicht installiert werden  
 Sie sind eine Voraussetzung im globalen Assemblycache (global Assemblycache) fehlt, die die Anwendung ausführen erforderliches Sitzungsverzeichnis.  
  
## <a name="publishing-with-visual-studio"></a>Veröffentlichen mit Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Veröffentlichung in Visual Studio schlägt fehl  
 Stellen Sie sicher, dass Sie das Recht zum Veröffentlichen auf dem Server verfügen, die das Ziel. Z. B. Wenn Sie bei einer terminal Server-Computer als normaler Benutzer, nicht als Administrator angemeldet sind müssen wahrscheinlich nicht die erforderlichen Benutzerrechten zum Veröffentlichen auf dem lokalen Webserver Sie.  
  
 Wenn Sie mit einer URL veröffentlichen, stellen Sie sicher, dass der Zielcomputer die FrontPage-Servererweiterungen aktiviert wurde.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Fehlermeldung: Kann nicht zum Erstellen der Website "\<Site >". Die Komponenten für die Kommunikation mit FrontPage-Servererweiterungen sind nicht installiert.  
 Stellen Sie sicher, dass Sie die Microsoft Visual Studio Web Authoring-Komponente auf dem Computer, dem Sie veröffentlichen aus installiert haben. Für Express-Benutzer wird diese Komponente nicht standardmäßig installiert. Weitere Informationen finden Sie unter [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Fehlermeldung: Die Datei nicht gefunden "Microsoft.Windows.Common-Steuerelemente, Version 6.0.0.0, Culture = = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, Typ = win32"  
 Diese Fehlermeldung wird angezeigt, wenn Sie versuchen, eine WPF-Anwendung mit aktivierten visuellen Stilen zu veröffentlichen. Um dieses Problem zu beheben, finden Sie unter [Vorgehensweise: Veröffentlichen einer WPF-Anwendung mit visuelle Stile aktiviert](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Verwenden von Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sie haben versucht, sich mit einem Zertifikat in Ihrem Zertifikatspeicher und eine leere Meldung  
 In der **Signierung** (Dialogfeld), müssen Sie:  
  
-   Wählen Sie **mit gespeichertem Zertifikat signieren**, und  
  
-   Wählen Sie ein Zertifikat aus der Liste aus. das erste Zertifikat ist nicht die Standardauswahl.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Klicken auf die Schaltfläche "Signieren" bewirkt, dass eine Ausnahme  
 Dieses Problem ist ein bekanntes Problem. Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Manifeste signiert werden müssen. Wählen Sie einfach eine der Optionen signieren, und klicken Sie dann auf **OK**.  
  
## <a name="additional-errors"></a>Weitere Fehler  
 Die folgende Tabelle zeigt einige allgemeine Fehlermeldungen, die ein Client-Computerbenutzer erhalten kann, wenn der Benutzer installiert eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Jede Fehlermeldung ist neben einer Beschreibung, der die wahrscheinlichste Ursache für den Fehler aufgeführt.  
  
|Fehlermeldung|Beschreibung|  
|-------------------|-----------------|  
|Anwendung kann nicht gestartet werden. Wenden Sie sich an den Herausgeber der Anwendung.<br /><br /> Die Anwendung kann nicht gestartet werden. Wenden Sie sich an den Anwendungshersteller, um Unterstützung zu erhalten.|Hierbei handelt es sich um generische Fehlermeldungen, die auftreten, wenn die Anwendung kann nicht gestartet werden und keine weitere Ursache gefunden werden kann. Häufig bedeutet dies, dass die Anwendung aus irgendeinem Grund beschädigt ist oder dass die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Speicher ist beschädigt.|  
|Kann nicht fortgesetzt werden. Die Anwendung ist falsch formatiert. Wenden Sie sich an den Herausgeber der Anwendung, um Unterstützung zu erhalten.<br /><br /> Validierung der Anwendung war nicht erfolgreich. Kann nicht fortgesetzt werden.<br /><br /> Fehler beim Abrufen der Anwendungsdateien. Dateien in der Bereitstellung beschädigt.|Einer der in der Bereitstellung die Manifestdateien jedoch Abfragesyntax ist ungültig oder enthält einen Hash, der mit der entsprechenden Datei abgestimmt werden kann. Dieser Fehler kann auch angeben, das in einer Assembly eingebettete Manifest beschädigt ist. Neuerstellen der Bereitstellung und die Anwendung neu kompilieren oder suchen und beheben Sie die Fehler manuell in den Manifesten.|  
|Anwendung kann nicht abgerufen werden. Authentifizierungsfehler.<br /><br /> Schlägt die Installation war nicht erfolgreich. Anwendungsdateien auf dem Server wurde nicht gefunden. Wenden Sie sich an den Herausgeber der Anwendung oder an Ihren Administrator, um Unterstützung zu erhalten.|Eine oder mehrere Dateien in der Bereitstellung können nicht heruntergeladen werden, da Sie nicht für den Zugriff berechtigt sind. Dies kann verursacht werden, von einem 403 Forbidden-Fehler zurückgegeben wird, von einem Webserver, die auftreten können, wenn eine der Dateien in Ihrer Bereitstellung mit der Erweiterung endet, die der Web-Server als eine geschützte Datei behandelt wird. Außerdem kann ein Verzeichnis, das eine oder mehrere Dateien der Anwendung enthält einen Benutzernamen und ein Kennwort erfordern, Zugriff auf.|  
|Die Anwendung kann nicht heruntergeladen werden. Die Anwendung fehlen die erforderlichen Dateien. Wenden Sie sich an den Hersteller der Anwendung oder sich an den Systemadministrator, um Unterstützung zu erhalten.|Eine oder mehrere der im Anwendungsmanifest aufgelisteten Dateien kann nicht auf dem Server gefunden werden. Stellen Sie sicher, dass Sie alle abhängigen Bereitstellungsdateien hochgeladen haben, und wiederholen Sie den Vorgang.|  
|Herunterladen der Anwendung war nicht erfolgreich. Überprüfen Sie Ihre Netzwerkverbindung, oder wenden Sie sich an Ihren Systemadministrator oder den Netzwerkdienstanbieter.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]eine Netzwerkverbindung mit dem Server kann nicht erstellt werden. Überprüfen Sie die Verfügbarkeit des Servers und der Status des Netzwerks.|  
|URLDownloadToCacheFile mit HRESULT-Fehler "\<Anzahl >". Fehler beim Herunterladen "\<Datei >".|Wenn ein Benutzer Erweiterte Sicherheitskonfiguration für Internet Explorer-Option festgelegt hat "Warnen, wenn zwischen sicherem und nicht sicheren Modus" auf dem Zielcomputer für die Bereitstellung und die Setup-URL der ClickOnce-Anwendung installiert wird, eines sicheren Standorts aus einer nicht sicheren umgeleitet wird (oder umgekehrt), schlägt die Installation fehl, da die Internet Explorer-Warnung er unterbricht.<br /><br /> Zum Beheben dieses Problems können Sie eine der folgenden Aktionen ausführen:<br /><br /> -Deaktivieren Sie die Sicherheitsoption.<br />-Stellen Sie sicher, dass die Setup-URL nicht so umgeleitet wird, die von Sicherheitsmodi ändert.<br />-Entfernen Sie die Umleitung vollständig, und zeigen Sie auf die tatsächliche Setup-URL.|  
|Das Schreiben in die Festplatte Fehler. Es gibt möglicherweise nicht genügend Speicherplatz verfügbar auf dem Datenträger. Wenden Sie sich an den Hersteller der Anwendung oder sich an den Systemadministrator, um Unterstützung zu erhalten.|Dies kann darauf hindeuten, nicht genügend Speicherplatz zum Speichern von der Anwendung, aber einen Weitere allgemeinen e/a-Fehler können auch angeben, wenn Sie die Anwendungsdateien auf dem Laufwerk speichern möchten.|  
|Die Anwendung kann nicht gestartet werden. Es ist nicht genügend Speicherplatz auf dem Datenträger.|Die Festplatte ist voll. Sie Speicherplatz frei, und führen Sie die Anwendung erneut aus.|  
|Zu viele bereitgestellte Aktivierungen versuchen, gleichzeitig geladen werden.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Schränkt die Anzahl von anderen Anwendungen, die zur selben Zeit gestartet werden kann. Dies wird hauptsächlich zum Schutz vor böswilligen Versuche sollen Denial-of-Service-Angriffe auf den lokalen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Service; Benutzer, die versuchen, dieselbe Anwendung wiederholt in rascher zu starten, wird nur am Ende einer einzelnen Instanz von der die Anwendung.|  
|Verknüpfungen können nicht über das Netzwerk aktiviert werden.|Verknüpfungen zu einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung nur auf der lokalen Festplatte gestartet werden kann. Sie können nicht gestartet werden, öffnen Sie eine URL, die auf eine Verknüpfungsdatei auf einem Remoteserver verweist.|  
|Die Anwendung ist zu groß, um Sie online unter teilweiser Vertrauenswürdigkeit ausführen. Wenden Sie sich an den Hersteller der Anwendung oder sich an den Systemadministrator, um Unterstützung zu erhalten.|Größer als die Hälfte der Größe der Quote für die online-Anwendung eine Anwendung, die unter teilweiser Vertrauenswürdigkeit ausgeführt wird dürfen nicht sein standardmäßig 250 MB.|  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)