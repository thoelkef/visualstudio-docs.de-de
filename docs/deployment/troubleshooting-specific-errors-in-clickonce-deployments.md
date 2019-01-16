---
title: Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fdd69b83702b07aae8a1c39c6c9298201c2f048
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862165"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen
Dieser Artikel führt die folgenden allgemeinen Fehler, die auftreten können, bei der Bereitstellung einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung sowie Schritte, um jedes Problem zu beheben.  

## <a name="general-errors"></a>Allgemeine Fehler  

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Wenn Sie versuchen, eine Anwendungsdatei zu suchen, geschieht nichts, XML, die in Internet Explorer gerendert oder erhalten Sie ein Dialogfeld Ausführen oder Speichern unter  
 Dieser Fehler wird wahrscheinlich durch nicht ordnungsgemäß auf dem Server oder Client registriert Inhaltstypen (auch bekannt als MIME-Typen) verursacht.  

 Stellen Sie zunächst sicher, dass der Server, zum Zuordnen konfiguriert ist der *.application* Erweiterungstyp mit Inhalt "Application/X-ms-Anwendung."  

 Wenn der Server ordnungsgemäß konfiguriert ist, überprüfen Sie, ob die [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] auf Ihrem Computer installiert ist. Wenn die [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] installiert ist, und werden weiterhin angezeigt. dieses Problem, versuchen Sie es, Deinstallation und Neuinstallation der [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] den Inhaltstyp auf dem Client erneut zu registrieren.  

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Fehlermeldung "kann nicht zum Abrufen der Anwendung. Dateien fehlt in der Bereitstellung"oder"Anwendungsdownloads unterbrochen wurde für Netzwerkfehler auftreten, und versuchen Sie es später noch Mal"  
 Diese Meldung gibt an, dass eine oder mehrere Dateien verweist auf die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste können nicht heruntergeladen werden. Die einfachste Möglichkeit zum Debuggen dieses Fehlers ist, um zu versuchen, laden die URL, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] heruntergeladen werden kann. Hier sind einige möglichen Ursachen:  

- Wenn die Protokolldatei meldet, dass "(403) verboten" oder "(404) nicht gefunden," Stellen Sie sicher, dass der Webserver ist so konfiguriert, dass Herunterladen dieser Datei nicht blockiert wird. Weitere Informationen finden Sie unter [Probleme mit der Server- und Clientkonfiguration in ClickOnce-Bereitstellungen](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  

- Wenn die *config* Datei vom Server blockiert wird, finden Sie im Abschnitt "Fehler beim Herunterladen, wenn Sie versuchen, installieren Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung mit einer .config-Datei" weiter unten in diesem Artikel.  

- Bestimmen, ob dieser Fehler ist aufgetreten, da die `deploymentProvider` -URL in das Bereitstellungsmanifest verweist auf einen anderen Speicherort als die URL, die für die Aktivierung verwendet.  

- Stellen Sie sicher, dass alle Dateien auf dem Server vorhanden sind; die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Protokoll sollte Ihnen sagen, welche Datei nicht gefunden wurde.  

- Festzustellen Sie, ob es Probleme mit der Netzwerkkonnektivität; Sie können diese Meldung erhalten, wenn es sich bei Ihrem Client-Computer offline geschaltet, während des Downloads.  

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Herunterladen Sie Fehler beim, wenn Sie versuchen, eine ClickOnce-Anwendung zu installieren, die ist von einer config-Datei  
 Standardmäßig enthält eine Visual Basic-Windows-basierte Anwendung eine Datei "App.config". Es wird ein Problem sein, wenn ein Benutzer versucht, die von einem Webserver, die Windows Server 2003 verwendet installiert werden, da das Betriebssystem die Installation von blockiert *config* Dateien aus Sicherheitsgründen. So aktivieren Sie die *config* Datei installiert werden, klicken Sie auf **Dateierweiterung ".deploy" verwenden** in die **Veröffentlichungsoptionen** Dialogfeld.  

 Sie müssen die Inhaltstypen (auch bekannt als MIME-Typen) auch für die .application ". manifest" und ".deploy"-Dateien entsprechend festlegen. Weitere Informationen finden Sie in der Dokumentation zu Ihrem Webserver.  

 Weitere Informationen finden Sie unter "Windows Server 2003: Gesperrte Inhaltstypen"im [Server und Client-Konfigurationsprobleme in ClickOnce-Bereitstellungen](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Fehlermeldung: "Der Anwendung ist nicht ordnungsgemäß formatiert." Protokolldatei enthält "XML-Signatur ist ungültig."  
 Stellen Sie sicher, dass Sie die Manifestdatei aktualisiert und erneut signiert. Erneutes Veröffentlichen der Anwendung mithilfe von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder verwenden Sie Mage zum Signieren der Anwendung erneut aus.  

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Die Anwendung auf dem Server aktualisiert, aber der Client wird das Update nicht heruntergeladen  
 Dieses Problem möglicherweise gelöst werden, indem Sie einen der folgenden Aufgaben:  

- Überprüfen Sie die `deploymentProvider` URL im Bereitstellungsmanifest. Stellen Sie sicher, dass Sie die Bits im am selben Standort aktualisieren, `deploymentProvider` verweist auf.  

- Vergewissern Sie sich das Updateintervall im Bereitstellungsmanifest. Wenn dieses Intervall auf einem regelmäßigen Intervall, z. B. ein Mal alle sechs Stunden festgelegt ist [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scannt keine für ein Update, bis dieses Intervall verstrichen ist. Sie können ändern, dass das Manifest, um nach einem Update jedes Mal zu suchen, die die Anwendung gestartet wird. Ändern das Updateintervall ist eine praktische Möglichkeit während der Entwicklungszeit, um zu überprüfen, ob Updates installiert werden, aber er verlangsamt die Aktivierung von Anwendungen.  

- Starten Sie erneut die Anwendung im Startmenü zu verwenden. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Möglicherweise wurde das Update im Hintergrund festgestellt, aber werden Sie aufgefordert, die Bits auf der nächsten Aktivierung zu installieren.  

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Während des Updates erhalten Sie einen Fehler, der die folgenden Protokolleintrag hat: "Der Verweis in der Bereitstellung entspricht nicht die Identität, die im Manifest Anwendung definierte"  
 Dieser Fehler kann auftreten, da Sie die bereitstellungs- und Anwendungsmanifeste manuell bearbeitet haben und die Beschreibung der Identität einer Assembly in einem Manifest zu nicht mehr synchron mit den anderen verursacht haben. Die Identität einer Assembly besteht aus der Name, Version, Kultur und Token des öffentlichen Schlüssels. Überprüfen Sie die Identity-Beschreibungen in den Manifesten, und beseitigen Sie die Unterschiede.  

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Erste Aktivierung aus dem lokalen Datenträger oder CD-ROM ist erfolgreich, aber nachfolgende Aktivierung über das Menü "Start" nicht erfolgreich ist  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet die Bereitstellungsanbieter-URL zum Empfangen von Updates für die Anwendung an. Stellen Sie sicher, dass der Speicherort, dem die URL zeigt korrekt ist.  

#### <a name="error-cannot-start-the-application"></a>Fehler: "Die Anwendung kann nicht gestartet werden."  
 Diese Fehlermeldung wird in der Regel gibt an, dass es liegt ein Problem mit dem Installieren dieser Anwendung in der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zu speichern. Die Anwendung einen Fehler aufweist oder der Speicher ist beschädigt. Die Protokolldatei könnte sich herausstellen, in dem der Fehler aufgetreten ist.  

 Sie sollten die folgenden Schritte ausführen:  

-   Stellen Sie sicher, dass die Identität des Bereitstellungsmanifests, des Anwendungsmanifests und der Hauptanwendungsdatei exe-Datei alle eindeutig sind.  

-   Stellen Sie sicher, dass die Dateipfade nicht mehr als 100 Zeichen sind. Wenn Ihre Anwendung Dateipfade, die zu lang sind enthält, können Sie die Einschränkungen für die maximale Pfadlänge überschreiten, die Sie speichern können. Verkürzen Sie die Pfade, und installieren.  

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>PrivatePath-Einstellungen in der Konfigurationsdatei der Anwendung werden nicht berücksichtigt.  
 Um PrivatePath (Überprüfungspfade Fusion) zu verwenden, muss die Anwendung volle Vertrauenswürdigkeit anfordern. Versuchen Sie das Manifest der Anwendung volle Vertrauenswürdigkeit anfordern, und wiederholen dann erneut zu ändern.  

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Während der Deinstallation eine Meldung angezeigt, dass "Fehler beim Deinstallieren der Anwendung"  
 Diese Meldung bedeutet normalerweise, dass die Anwendung bereits entfernt wurde wurde oder der Speicher ist beschädigt. Nachdem Sie auf **OK**, **Programm hinzufügen/entfernen** Eintrag entfernt werden.  

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Während der Installation wird eine Meldung angezeigt, die besagt, dass die plattformabhängigkeiten nicht installiert werden  
 Sie fehlen erforderliche Komponente im globalen Assemblycache (global Assemblycache), die die Anwendung benötigt, um ausgeführt werden.  

## <a name="publishing-with-visual-studio"></a>Veröffentlichen mit Visual Studio  

#### <a name="publishing-in-visual-studio-fails"></a>Veröffentlichung in Visual Studio ein Fehler auftritt  
 Stellen Sie sicher, dass Sie berechtigt sind, auf dem Server veröffentlichen, die das Ziel. Beispielsweise, wenn Sie bei einem terminal Server-Computer als normaler Benutzer, nicht als Administrator angemeldet sind müssen wahrscheinlich nicht die erforderlichen Benutzerrechten zum Veröffentlichen an den lokalen Webserver Sie.  

 Wenn Sie mit einer URL veröffentlichen, stellen Sie sicher, dass der Zielcomputer FrontPage Server Extensions aktiviert ist.  

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Fehlermeldung: Kann nicht zum Erstellen der Website "\<Site >". Die Komponenten für die Kommunikation mit FrontPage-Servererweiterungen sind nicht installiert.  
 Stellen Sie sicher, dass Sie die Microsoft Visual Studio Web Authoring-Komponente auf dem Computer, dem Sie veröffentlichen aus installiert haben. Für Express-Benutzer ist diese Komponente nicht standardmäßig installiert. Weitere Informationen finden Sie unter [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Fehlermeldung: Datei wurde nicht gefunden "Microsoft.Windows.Common-Steuerelemente, Version 6.0.0.0, Kultur = = *, PublicKeyToken 6595b64144ccf1df, ProcessorArchitecture = =\*, Typ = win32"  
 Diese Fehlermeldung wird angezeigt, wenn Sie versuchen, veröffentlichen Sie eine WPF-Anwendung mit aktivierten visuellen Stilen. Um dieses Problem zu beheben, finden Sie unter [Vorgehensweise: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)  

## <a name="using-mage"></a>Verwenden von Mage  

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sie haben versucht, sich mit einem Zertifikat in Ihrem Zertifikatspeicher und ein Meldungsfeld der empfangenen leeren  
 In der **Signierung** müssen Sie im Dialogfeld:  

-   Wählen Sie **mit gespeichertem Zertifikat signieren**, und  

-   Wählen Sie ein Zertifikat aus der Liste aus. das erste Zertifikat ist nicht die Standardeinstellung.  

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Klicken auf die Schaltfläche "Signieren" löst eine Ausnahme  
 Dieses Problem ist ein bekanntes Problem. Alle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Manifeste signiert werden müssen. Wählen Sie einfach eine der Signierungsoptionen, und klicken Sie dann auf **OK**.  

## <a name="additional-errors"></a>Weitere Fehler  
 Die folgende Tabelle zeigt einige häufige Fehlermeldungen, die ein Clientcomputer Benutzer erhalten kann, wenn der Benutzer installiert eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Jede Fehlermeldung wird neben einer Beschreibung des die wahrscheinlichste Ursache für den Fehler aufgeführt.  


| Fehlermeldung | Beschreibung |
| - | - |
| Anwendung kann nicht gestartet werden. Wenden Sie sich an den Herausgeber der Anwendung.<br /><br /> Die Anwendung kann nicht gestartet werden. Wenden Sie sich an den Hersteller der Anwendung, um Unterstützung zu erhalten. | Hierbei handelt es sich um generische Fehlermeldungen, die auftreten, wenn die Anwendung kann nicht gestartet werden und keine weitere Ursache gefunden werden kann. Häufig bedeutet dies, dass die Anwendung aus irgendeinem Grund beschädigt ist, oder dass die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Speicher ist beschädigt. |
| Kann nicht fortgesetzt werden. Die Anwendung ist falsch formatiert. Wenden Sie sich an den Herausgeber der Anwendung, um Unterstützung zu erhalten.<br /><br /> Validierung der Anwendung war nicht erfolgreich. Kann nicht fortgesetzt.<br /><br /> Fehler beim Abrufen der Dateien der Anwendung. Dateien, die in der Bereitstellung beschädigt werden. | Eine der manifest-Dateien in der Bereitstellung ist ungültig oder enthält einen Hash, der mit der entsprechenden Datei abgestimmt werden kann. Dieser Fehler möglicherweise auch, dass das in einer Assembly eingebettete Manifest beschädigt ist. Erstellen Sie die Bereitstellung neu zu und Rekompilieren Sie Ihre Anwendung, oder suchen Sie und beheben Sie die Fehler manuell in den Manifesten. |
| Anwendung kann nicht abgerufen werden. Authentifizierungsfehler.<br /><br /> Installation der Anwendung war nicht erfolgreich. Anwendungsdateien auf dem Server wurde nicht gefunden. Wenden Sie sich an den Herausgeber der Anwendung oder an Ihren Administrator, um Unterstützung zu erhalten. | Eine oder mehrere Dateien in der Bereitstellung können nicht heruntergeladen werden, da Sie nicht über die Zugriffsberechtigung verfügen. Dies kann verursacht werden, um einen 403 Verboten-Fehler zurückgegeben wird, von einem Webserver, die auftreten können, wenn eine der Dateien in Ihrer Bereitstellung mit der Erweiterung endet, die den Webserver als eine geschützte Datei behandelt wird. Darüber hinaus kann ein Verzeichnis, das eine oder mehrere der die Dateien der Anwendung enthält einen Benutzernamen und ein Kennwort benötigen, um zuzugreifen. |
| Die Anwendung kann nicht heruntergeladen werden. Die Anwendung fehlen die erforderlichen Dateien. Wenden Sie sich an den Hersteller der Anwendung oder der Systemadministrator, um Unterstützung zu erhalten. | Eine oder mehrere Dateien aufgeführt, die im Manifest Anwendung kann nicht auf dem Server nicht gefunden werden. Überprüfen Sie, dass Sie alle Dateien der Bereitstellung des abhängigen hochgeladen haben, und versuchen Sie es erneut. |
| Zum Herunterladen war nicht erfolgreich. Überprüfen Sie Ihre Netzwerkverbindung, oder wenden Sie sich an Ihren Systemadministrator oder den Netzwerk-Dienstanbieter. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eine Netzwerkverbindung mit dem Server kann nicht erstellt werden. Überprüfen Sie die Verfügbarkeit des Servers und der Status des Netzwerks. |
| URLDownloadToCacheFile mit HRESULT-Fehler '\<Anzahl > ". Fehler beim Herunterladen "\<Datei >". | Wenn ein Benutzer Erweiterte Sicherheitskonfiguration für Internet Explorer-Option festgelegt hat, "Warnung, wenn der Wechsel vom sicheren und nicht sicheren Modus" auf dem Zielcomputer der Bereitstellung und die Setup-URL, der die ClickOnce-Anwendung installiert wird aus einem unsicheren an eine sichere Website umgeleitet wird (oder umgekehrt), schlägt die Installation fehl, da er die Warnung von Internet Explorer die unterbricht.<br /><br /> Um diesen Fehler zu beheben, können Sie eine der folgenden Aufgaben ausführen:<br /><br /> – Deaktivieren Sie die Sicherheitsoption ein.<br />-Stellen Sie sicher, dass die Setup-URL nicht so die Sicherheitsmodi geändert umgeleitet wird.<br />-Entfernen Sie die Umleitung vollständig, und zeigen Sie auf die eigentliche Setup-URL. |
| Ein Fehler ist beim Schreiben in die Festplatte aufgetreten. Es gibt möglicherweise nicht genügend Speicherplatz verfügbar auf dem Datenträger. Wenden Sie sich an den Hersteller der Anwendung oder der Systemadministrator, um Unterstützung zu erhalten. | Dies kann darauf hinweisen, nicht genügend Speicherplatz zum Speichern der Anwendung, aber es kann außerdem einen Weitere allgemeinen e/a-Fehler angezeigt, wenn Sie die Anwendungsdateien auf das Laufwerk speichern möchten. |
| Die Anwendung kann nicht gestartet werden. Es ist nicht genügend Speicherplatz auf dem Datenträger. | Die Festplatte ist voll. Sie Speicherplatz frei, und wiederholen Sie die Anwendung erneut ausführen. |
| Zu viele bereitgestellte Aktivierungen versuchen, gleichzeitig laden. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] beschränkt die Anzahl von anderen Anwendungen, die zur gleichen Zeit gestartet werden kann. Dies ist zum größten Teil zum Schutz vor böswilligen Versuch sollen Denial-of-Service-Angriffe auf den lokalen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Service; Benutzer, die versuchen, dieselbe Anwendung wiederholt in rascher Folge zu starten, wird nur am Ende einer einzelnen Instanz der die Anwendung. |
| Verknüpfungen können nicht über das Netzwerk aktiviert werden. | Verknüpfungen zu einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung kann nur auf der lokalen Festplatte gestartet werden. Sie können nicht gestartet werden, öffnen Sie eine URL, die auf eine Verknüpfungsdatei auf einem Remoteserver verweist. |
| Die Anwendung ist zu groß, um online bei teilweiser Vertrauenswürdigkeit ausgeführt. Wenden Sie sich an den Hersteller der Anwendung oder der Systemadministrator, um Unterstützung zu erhalten. | Eine Anwendung, die bei teilweiser Vertrauenswürdigkeit ausgeführt wird darf nicht größer als die Hälfte der Größe der online-Anwendung das Kontingent sein, die standardmäßig 250 MB ist. |

## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)