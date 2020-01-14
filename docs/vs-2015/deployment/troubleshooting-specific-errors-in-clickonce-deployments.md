---
title: Problembehandlung bei bestimmten Fehlern in ClickOnce-bereit Stellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: troubleshooting
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
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81bb9bcecf37d2ed3fca29a4edc57738732de1a5
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917280"
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die folgenden allgemeinen Fehler aufgelistet, die bei der Bereitstellung einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung auftreten können, und es werden Schritte zum Beheben der einzelnen Probleme beschrieben.  
  
## <a name="general-errors"></a>Allgemeine Fehler  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Wenn Sie versuchen, eine Anwendungsdatei zu finden, geschieht nichts, oder XML wird in Internet Explorer gerendert, oder Sie erhalten ein Dialogfeld "ausführen" oder "Speichern unter".  
 Dieser Fehler wird wahrscheinlich durch Inhaltstypen (auch als MIME-Typen bezeichnet) verursacht, die nicht ordnungsgemäß auf dem Server oder Client registriert sind.  
  
 Stellen Sie zunächst sicher, dass der Server so konfiguriert ist, dass die Erweiterung ". Application" mit dem Inhaltstyp "application/x-ms-application" verknüpft wird.  
  
 Wenn der Server ordnungsgemäß konfiguriert ist, stellen Sie sicher, dass die [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] auf dem Computer installiert ist. Wenn die [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] installiert ist und dieses Problem weiterhin auftritt, deinstallieren Sie die [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], und installieren Sie Sie erneut, um den Inhaltstyp auf dem Client erneut zu registrieren.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Die Fehlermeldung besagt, dass die Anwendung nicht abgerufen werden kann. In der Bereitstellung fehlende Dateien oder der Anwendungs Download wurde unterbrochen. Überprüfen Sie, ob Netzwerkfehler vorliegen, und versuchen Sie es später noch mal.  
 Diese Meldung gibt an, dass eine oder mehrere Dateien, auf die die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifeste verweist, nicht heruntergeladen werden können. Die einfachste Möglichkeit zum Debuggen dieses Fehlers besteht darin, die URL herunterzuladen, die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sagt, dass Sie nicht heruntergeladen werden kann. Folgende Ursachen sind möglich:  
  
- Wenn die Protokolldatei "(403) verboten" oder "(404) nicht gefunden" lautet, überprüfen Sie, ob der Webserver so konfiguriert ist, dass er das Herunterladen dieser Datei nicht blockiert. Weitere Informationen finden Sie unter [Probleme mit der Server- und Clientkonfiguration in ClickOnce-Bereitstellungen](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
- Wenn die config-Datei vom Server blockiert wird, finden Sie weitere Informationen im Abschnitt "Download Fehler beim Versuch, eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung zu installieren, die über eine. config-Datei verfügt" weiter unten in diesem Thema.  
  
- Bestimmen Sie, ob dies aufgetreten ist, da die `deploymentProvider`-URL im Bereitstellungs Manifest auf einen anderen Speicherort als die für die Aktivierung verwendete URL verweist.  
  
- Stellen Sie sicher, dass alle Dateien auf dem Server vorhanden sind. Das [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Protokoll sollte Ihnen mitteilen, welche Datei nicht gefunden wurde.  
  
- Überprüfen Sie, ob Probleme mit der Netzwerk Konnektivität bestehen. Sie können diese Meldung erhalten, wenn der Client Computer während des Downloads offline geschaltet wurde.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Fehler beim Herunterladen, wenn Sie versuchen, eine ClickOnce-Anwendung mit einer config-Datei zu installieren  
 Standardmäßig enthält eine Visual Basic Windows-basierte Anwendung eine APP. config-Datei. Es tritt ein Problem auf, wenn ein Benutzer versucht, von einem Webserver zu installieren, der Windows Server 2003 verwendet, da das Betriebssystem die Installation von. config-Dateien aus Sicherheitsgründen blockiert. Um die Installation der config-Datei zu aktivieren, klicken Sie im Dialogfeld **Veröffentlichungs Optionen** auf **Dateierweiterung** bereitstellen.  
  
 Außerdem müssen Sie die Inhaltstypen (auch als MIME-Typen bezeichnet) ordnungsgemäß für Anwendungs-, Manifest-und Bereitstellungs Dateien festlegen. Weitere Informationen finden Sie in der Dokumentation zum Webserver.  
  
 Weitere Informationen finden Sie unter "Windows Server 2003: gesperrte Inhaltstypen" Unterprobleme mit der [Server-und Client Konfiguration in ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)-bereit Stellungen.  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Fehlermeldung: "die Anwendung ist nicht ordnungsgemäß formatiert;" Die Protokolldatei enthält eine ungültige XML-Signatur.  
 Stellen Sie sicher, dass Sie die Manifest-Datei aktualisiert und erneut signiert haben. Veröffentlichen Sie Ihre Anwendung erneut mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], oder verwenden Sie Mage, um die Anwendung erneut zu signieren.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Sie haben Ihre Anwendung auf dem Server aktualisiert, aber der Client lädt das Update nicht herunter.  
 Dieses Problem kann behoben werden, indem Sie eine der folgenden Aufgaben ausführen:  
  
- Überprüfen Sie die `deploymentProvider`-URL im Bereitstellungs Manifest. Stellen Sie sicher, dass Sie die Bits an demselben Speicherort aktualisieren, auf den `deploymentProvider` verweist.  
  
- Überprüfen Sie das Aktualisierungs Intervall im Bereitstellungs Manifest. Wenn dieses Intervall auf ein periodisches Intervall festgelegt wird, z. b. einmal alle sechs Stunden, werden [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] erst nach einem Update suchen, wenn dieses Intervall abgelaufen ist. Sie können das Manifest so ändern, dass jedes Mal, wenn die Anwendung gestartet wird, auf ein Update überprüft wird. Das Ändern des Aktualisierungs Intervalls ist während der Entwicklungszeit eine bequeme Option, um zu überprüfen, ob Updates installiert werden, aber die Anwendungs Aktivierung wird dadurch verlangsamt.  
  
- Versuchen Sie, die Anwendung erneut im Startmenü zu starten. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] haben das Update möglicherweise im Hintergrund erkannt, werden Sie jedoch zur Installation der Bits bei der nächsten Aktivierung aufgefordert.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Während des Updates erhalten Sie eine Fehlermeldung mit dem folgenden Protokolleintrag: "der Verweis in der Bereitstellung stimmt nicht mit der Identität, die im Anwendungs Manifest definiert ist".  
 Dieser Fehler kann auftreten, wenn Sie die Bereitstellungs-und Anwendungs Manifeste manuell bearbeitet haben und die Beschreibung der Identität einer Assembly in einem Manifest nicht mehr mit dem anderen Manifest synchronisiert wurde. Die Identität einer Assembly besteht aus dem Namen, der Version, der Kultur und dem öffentlichen Schlüssel Token. Überprüfen Sie die Identitäts Beschreibungen in ihren Manifesten, und korrigieren Sie alle Unterschiede.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Die erstmalige Aktivierung von lokalem Datenträger oder CD-Rom ist erfolgreich, aber die nachfolgende Aktivierung über das Startmenü ist nicht erfolgreich.  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verwendet die Bereitstellungs Anbieter-URL, um Updates für die Anwendung zu empfangen. Vergewissern Sie sich, dass der Speicherort, auf den die URL verweist, korrekt ist.  
  
#### <a name="error-cannot-start-the-application"></a>Fehler: "die Anwendung kann nicht gestartet werden"  
 Diese Fehlermeldung weist in der Regel darauf hin, dass ein Problem bei der Installation dieser Anwendung im [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Speicher vorliegt. Entweder hat die Anwendung einen Fehler, oder der Speicher ist beschädigt. In der Protokolldatei wird Ihnen möglicherweise mitgeteilt, wo der Fehler aufgetreten ist.  
  
 Gehen Sie folgendermaßen vor:  
  
- Vergewissern Sie sich, dass die Identität des Bereitstellungs Manifests, der Identität des Anwendungs Manifests und der Identität der Haupt Anwendungs-exe eindeutig sind.  
  
- Vergewissern Sie sich, dass die Dateipfade nicht länger als 100 Zeichen sind. Wenn die Anwendung Dateipfade enthält, die zu lang sind, können Sie die Einschränkungen für den maximalen Pfad überschreiten, den Sie speichern können. Verkürzen Sie die Pfade, und installieren Sie Sie neu.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Die PrivatePath-Einstellungen in der Anwendungs Konfigurationsdatei werden nicht berücksichtigt.  
 Um privatePath (Fusion-probingpfade) verwenden zu können, muss die Anwendung die Berechtigung "volle Vertrauenswürdigkeit" anfordern. Ändern Sie das Anwendungs Manifest, um volle Vertrauenswürdigkeit anzufordern, und wiederholen Sie dann den Vorgang.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Während der Deinstallation wird die Meldung "Fehler beim Deinstallieren der Anwendung" angezeigt.  
 Diese Meldung gibt in der Regel an, dass die Anwendung bereits entfernt wurde oder dass der Speicher beschädigt ist. Nachdem Sie auf " **OK**" geklickt haben, wird der Eintrag " **Programm hinzufügen/entfernen** " entfernt.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Während der Installation wird eine Meldung angezeigt, die besagt, dass die Platt Form Abhängigkeiten nicht installiert sind.  
 Im globalen Assemblycache (GAC) fehlt eine Voraussetzung, die die Anwendung benötigt, um ausgeführt zu werden.  
  
## <a name="publishing-with-visual-studio"></a>Veröffentlichen mit Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Fehler beim Veröffentlichen in Visual Studio  
 Stellen Sie sicher, dass Sie über das Recht verfügen, auf dem Zielserver zu veröffentlichen. Wenn Sie z. b. bei einem Terminal Server Computer als normaler Benutzer, nicht als Administrator angemeldet sind, haben Sie wahrscheinlich nicht die erforderlichen Rechte, um auf dem lokalen Webserver zu veröffentlichen.  
  
 Wenn Sie mit einer URL veröffentlichen, stellen Sie sicher, dass der Zielcomputer FrontPage-Servererweiterungen aktiviert ist.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Fehlermeldung: die Website "\<Site >" konnte nicht erstellt werden. Die Komponenten für die Kommunikation mit FrontPage-Servererweiterungen sind nicht installiert.  
 Stellen Sie sicher, dass auf dem Computer, von dem aus Sie veröffentlichen, die Microsoft Visual Studio Web Authoring-Komponente installiert ist. Für Express-Benutzer wird diese Komponente standardmäßig nicht installiert.  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Fehlermeldung: die Datei ' Microsoft. Windows. Common-Controls, Version = 6.0.0.0, Culture = *, PublicKeyToken = 6595b64144ccf 1DF, ProcessorArchitecture =\*, Type = Win32 ' wurde nicht gefunden.  
 Diese Fehlermeldung wird angezeigt, wenn Sie versuchen, eine WPF-Anwendung mit aktivierten visuellen Stilen zu veröffentlichen. Informationen zum Beheben dieses Problems finden Sie unter Gewusst [wie: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Verwenden von Mage  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sie haben versucht, sich mit einem Zertifikat in Ihrem Zertifikat Speicher und einem empfangenen leeren Meldungs Feld anzumelden.  
 Im Dialogfeld **Signierung** müssen Sie folgende Schritte ausführen:  
  
- Wählen Sie **mit einem gespeicherten Zertifikat signieren**aus.  
  
- Wählen Sie ein Zertifikat aus der Liste aus. beim ersten Zertifikat handelt es sich nicht um die Standardauswahl.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Durch Klicken auf die Schaltfläche "nicht signieren" wird eine Ausnahme ausgelöst  
 Dieses Problem ist ein bekannter Fehler. Alle [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifeste müssen signiert werden. Wählen Sie einfach eine der Signierungs Optionen aus, und klicken Sie dann auf **OK**.  
  
## <a name="additional-errors"></a>Weitere Fehler  
 In der folgenden Tabelle werden einige häufige Fehlermeldungen angezeigt, die ein Benutzer eines Client Computers möglicherweise empfängt, wenn der Benutzer eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung installiert. Jede Fehlermeldung wird neben einer Beschreibung der wahrscheinlichsten Ursache für den Fehler aufgeführt.  
  
|Fehlermeldung|Beschreibung|  
|-------------------|-----------------|  
|Die Anwendung kann nicht gestartet werden. Wenden Sie sich an den Anwendungs Verleger.<br /><br /> Die Anwendung kann nicht gestartet werden. Wenden Sie sich für Unterstützung an den Hersteller der Anwendung.|Dabei handelt es sich um generische Fehlermeldungen, die auftreten, wenn die Anwendung nicht gestartet werden kann, und es kann kein anderer spezifischer Grund gefunden werden. Dies bedeutet häufig, dass die Anwendung irgendwie beschädigt ist, oder dass der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Speicher beschädigt ist.|  
|Der Vorgang kann nicht fortgesetzt werden. Die Anwendung ist nicht ordnungsgemäß formatiert. Wenden Sie sich an den Anwendungs Herausgeber.<br /><br /> Die Anwendungs Überprüfung war nicht erfolgreich. Vorgang kann nicht fortgesetzt werden.<br /><br /> Anwendungs Dateien können nicht abgerufen werden. Dateien sind bei der Bereitstellung beschädigt.|Eine der Manifest-Dateien in der Bereitstellung ist syntaktisch ungültig oder enthält einen Hash, der nicht mit der entsprechenden Datei abgestimmt werden kann. Dieser Fehler kann auch darauf hindeuten, dass das in eine Assembly eingebettete Manifest beschädigt ist. Erstellen Sie die Bereitstellung neu, und kompilieren Sie Ihre Anwendung neu, oder suchen und beheben Sie die Fehler manuell in ihren Manifesten.|  
|Die Anwendung kann nicht abgerufen werden. Authentifizierungsfehler.<br /><br /> Die Anwendungs Installation war nicht erfolgreich. Es wurden keine Anwendungs Dateien auf dem Server gefunden. Wenden Sie sich an den Anwendungs Herausgeber oder Ihren Administrator.|Mindestens eine Datei in der Bereitstellung kann nicht heruntergeladen werden, da Sie nicht über die entsprechende Zugriffsberechtigung verfügen. Dies kann durch einen 403-Fehler verursacht werden, der von einem Webserver zurückgegeben wird. Dies kann vorkommen, wenn eine der Dateien in der Bereitstellung mit einer Erweiterung endet, die den Webserver als geschützte Datei behandelt. Außerdem erfordert ein Verzeichnis, das eine oder mehrere Dateien der Anwendung enthält, möglicherweise einen Benutzernamen und ein Kennwort, um auf zuzugreifen.|  
|Die Anwendung kann nicht heruntergeladen werden. In der Anwendung fehlen erforderliche Dateien. Wenden Sie sich an den Hersteller der Anwendung oder an den Systemadministrator.|Mindestens eine der Dateien, die im Anwendungs Manifest aufgelistet sind, kann auf dem Server nicht gefunden werden. Vergewissern Sie sich, dass Sie alle abhängigen Dateien der Bereitstellung hochgeladen haben, und wiederholen Sie den Vorgang.|  
|Das Herunterladen der Anwendung war nicht erfolgreich. Überprüfen Sie Ihre Netzwerkverbindung, oder wenden Sie sich an Ihren Systemadministrator oder den Netzwerk Dienstanbieter.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kann keine Netzwerkverbindung mit dem Server herstellen. Überprüfen Sie die Verfügbarkeit des Servers und den Status Ihres Netzwerks.|  
|Fehler bei urldownloaddecachefile mit HRESULT "\<Nummer >". Fehler beim Herunterladen von "\<Datei >".|Wenn ein Benutzer auf dem Bereitstellungs Zielcomputer die Option Erweiterte Sicherheit von Internet Explorer (Warnung bei Wechsel zwischen sicherem und unsicherem Modus) festgelegt hat und die Setup-URL der zu installierenden ClickOnce-Anwendung von einem nicht sicheren an einen sicheren Standort umgeleitet wird (oder umgekehrt) schlägt die Installation fehl, da Sie von der Internet Explorer-Warnung unterbrochen wird.<br /><br /> Um dieses Problem zu beheben, können Sie eine der folgenden Aktionen ausführen:<br /><br /> -Deaktivieren Sie die Option Sicherheit.<br />-Stellen Sie sicher, dass die Setup-URL nicht so umgeleitet wird, dass die Sicherheitsmodi geändert werden.<br />-Entfernen Sie die Umleitung vollständig, und zeigen Sie auf die tatsächliche Setup-URL.|  
|Fehler beim Schreiben auf die Festplatte. Auf dem Datenträger ist möglicherweise nicht genügend Speicherplatz verfügbar. Wenden Sie sich an den Hersteller der Anwendung oder an den Systemadministrator.|Dies weist möglicherweise auf unzureichenden Speicherplatz zum Speichern der Anwendung hin, kann jedoch auch einen allgemeineren e/a-Fehler angeben, wenn Sie versuchen, die Anwendungs Dateien auf dem Laufwerk zu speichern.|  
|Die Anwendung kann nicht gestartet werden. Es ist nicht genügend Speicherplatz auf dem Datenträger verfügbar.|Die Festplatte ist voll. Löschen Sie den Speicherplatz, und versuchen Sie erneut, die Anwendung auszuführen.|  
|Zu viele bereitgestellte Aktivierungen versuchen gleichzeitig zu laden.|[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] schränkt die Anzahl der verschiedenen Anwendungen ein, die gleichzeitig gestartet werden können. Dies dient größtenteils zum Schutz gegen böswillige Versuche, Denial-of-Service-Angriffe gegen den lokalen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dienst zu initiieren. Benutzer, die versuchen, dieselbe Anwendung wiederholt in schneller Folge zu starten, erhalten nur eine einzige Instanz der Anwendung.|  
|Verknüpfungen können nicht über das Netzwerk aktiviert werden.|Verknüpfungen zu einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung können nur auf der lokalen Festplatte gestartet werden. Sie können nicht gestartet werden, indem Sie eine URL öffnen, die auf eine Verknüpfungs Datei auf einem Remote Server verweist.|  
|Die Anwendung ist zu groß, um in teilweiser Vertrauenswürdigkeit online auszuführen. Wenden Sie sich an den Hersteller der Anwendung oder an den Systemadministrator.|Eine Anwendung, die mit teilweiser Vertrauenswürdigkeit ausgeführt wird, darf nicht größer als die Hälfte der Größe des Online Anwendungs Kontingents sein, das standardmäßig 250 MB beträgt.|  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
