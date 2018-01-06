---
title: Problembehandlung bei der Office-Projektmappenbereitstellung | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
ms.assetid: 2206aeb6-44b3-4786-ba99-9c7dad5cce7c
caps.latest.revision: "74"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a778aa9e257773ca186bba8b99d5e426f8f26aed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-office-solution-deployment"></a>Problembehandlung bei der Office-Projektmappenbereitstellung
  Dieses Thema enthält Informationen zur Lösung von allgemeinen Problemen, die beim Bereitstellen von Office-Projektmappen auftreten können.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshooting-office-solutions-by-using-the-event-viewer"></a>Problembehandlung für Office-Projektmappen mit der Ereignisanzeige  
 Beim Installieren oder Deinstallieren von Office-Lösungen werden von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Fehlermeldungen protokolliert, die Sie mit der Ereignisanzeige in Windows anzeigen können. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations- und Bereitstellungsprobleme zu beheben. Weitere Informationen finden Sie unter [Event Logging for Office Solutions](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="changing-the-assembly-name-causes-conflicts"></a>Konflikte nach Änderung des Assemblynamens  
 Wenn Sie ändern die **Assemblyname** Wert in der **Anwendung** auf der Seite der **Projekt-Designer** Veröffentlichungstools werden geändert, nachdem bereits eine Projektmappe bereitgestellt wurde, die Setup-Paket, um eine Setup.exe-Datei und zwei Bereitstellungsmanifeste beinhaltet. Wenn Sie zwei Manifestdateien bereitstellen, treten möglicherweise die folgenden Bedingungen ein:  
  
-   Wenn der Endbenutzer beide Versionen installiert, werden von der Anwendung beide VSTO-Add-Ins geladen.  
  
-   Wurde das VSTO-Add-In vor Änderung des Assemblynamens installiert, empfängt der Endbenutzer niemals Updates.  
  
 Um dies zu verhindern, ändern Sie nicht der Projektmappe **Assemblyname** Wert nach der Bereitstellung der Lösung.  
  
## <a name="checking-for-updates-takes-a-long-time"></a>Die Suche nach Updates nimmt viel Zeit in Anspruch  
 Visual Studio 2010-Tools für Office-Laufzeit stellt einen Registrierungseintrag zur Verfügung, mit dem Administratoren den Timeoutwert für das Herunterladen der Manifeste und der Projektmappe festlegen können.  
  
#### <a name="to-set-the-time-out-value"></a>So legen Sie den Timeoutwert fest  
  
1.  Navigieren Sie in der Registrierung zu folgendem Schlüssel:  
  
     HKEY_CURRENT_USER\Software\Microsoft\VSTA  
  
2.  Legen Sie im Unterschlüssel **AddInTimeout** den Timeoutwert in Millisekunden fest.  
  
     Ist der Unterschlüssel **AddInTimeout** nicht vorhanden, erstellen Sie ihn als DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Aktualisieren oder Veröffentlichen auf einer Netzwerkdateifreigabe nicht möglich  
 Office-Projektmappen in einer Netzwerkdateifreigabe zeigen während Updates unter Umständen eine irreführende Meldung an, falls die Datei Setup.exe der Projektmappe bei Veröffentlichung des Updates in einem Prozess gesperrt ist. In der Meldung wird möglicherweise Folgendes angezeigt: "Die Datei 'setup.exe' konnte dem Web nicht hinzugefügt werden. Die Datei 'setup.exe' ist in diesem Web bereits vorhanden."  
  
 Eine Dateisperrung verhindern Sie dadurch, dass Sie die Freigabe Endbenutzern nur schreibgeschützt zur Verfügung stellen. Befinden sich Dokumente allerdings in der Freigabe, stehen sie Endbenutzern ebenfalls schreibgeschützt zur Verfügung.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Erforderliche Komponenten für Microsoft Office sind nicht installiert  
 Sie können dem Setup-Paket .NET Framework, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]und die primären Interop-Assemblys von Office als erforderliche Komponenten hinzufügen, die mit der Office-Projektmappe bereitgestellt werden. Informationen zum Installieren von primären Interopassemblys finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md) und [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publishing-using-localhost-can-cause-installation-problems"></a>Veröffentlichungen mithilfe von 'Localhost' können zu Installationsproblemen führen  
 Bei Verwendung von "http://localhost" als Veröffentlichungs- oder Installationsort für Projektmappen auf Anwendungsebene konvertiert der **Veröffentlichungs-Assistent** die Zeichenfolge nicht in den tatsächlichen Computernamen. In diesem Fall muss die Projektmappe nur auf dem Entwicklungscomputer installiert werden. Damit bereitgestellte Projektmappen auf dem Entwicklungscomputer Internetinformationsdienste verwenden, muss anstelle von localhost der vollqualifizierte Name für alle HTTP/HTTPS/FTP-Speicherorte verwendet werden.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Anstelle von aktualisierten Assemblys werden zwischengespeicherte Assemblys geladen  
 Fusion, das Assemblyladeprogramm von .NET Framework, lädt die zwischengespeicherte Kopie der Assemblys, wenn sich der Projektausgabepfad in einer Netzwerkdateifreigabe befindet, die Assembly mit einem starken Namen signiert ist und die Assemblyversion der Anpassung nicht geändert wird. Wird eine Assembly aktualisiert, die diese Bedingungen erfüllt, wird das Update erst bei der nächsten Ausführung des Projekts angezeigt, da die zwischengespeicherte Kopie geladen wird.  
  
 Visual Studio kann so konfiguriert werden, dass bei jeder Ausführung des Projekts Assemblys von Fusion heruntergeladen werden.  
  
#### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>So laden Sie Assemblys herunter, anstatt zwischengespeicherte Kopien zu laden  
  
1.  Wählen Sie in der Menüleiste **Projekt**, *Projektname***Eigenschaften**.  
  
2.  Wählen Sie auf der Seite **Anwendung** die Option **Assemblyinformationen**.  
  
3.  Im ersten **Assemblyversion** Geben Sie ein Sternchen (\*), und wählen Sie dann die **OK** Schaltfläche.  
  
 Nach dem Ändern der Assemblyversion kann die Signatur der Assembly mit einem starken Namen fortgesetzt werden, und die aktuellste Version der Anpassung wird geladen.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-aret-us-ascii"></a>Installationsfehler, wenn der URI andere Zeichen als US-ASCII beinhaltet  
 Wird eine Office-Projektmappe in einem HTTP/HTTPS/FTP-Speicherort veröffentlicht, darf der Pfad keine Unicode-Zeichen enthalten, die nicht in US-ASCII vorliegen. Solche Zeichen können zu inkonsistentem Verhalten im Setup-Programm führen. Verwenden Sie für den Installationspfad US-ASCII-Zeichen.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Eingabeaufforderung zum manuellen Deinstallieren wird angezeigt, wenn Sie eine Projektmappe auf dem Entwicklungscomputer veröffentlichen und installieren  
 Wenn Sie eine Office-Projektmappe erstellen, wird die erstellte Version automatisch registriert. Wenn Sie dieselbe Projektmappe bereits auf dem Entwicklungscomputer veröffentlicht und installiert haben, erkennt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nach der nächsten Erstellung, erneuten Erstellung oder Veröffentlichung der Projektmappe, dass der Installationspfad für die veröffentlichte Version und die erstellte Version unterschiedlich sind. Die Fehlermeldung lautet wie folgt: "Die Anpassung kann nicht installiert werden, weil derzeit eine andere Version installiert ist und von diesem Speicherort nicht aktualisiert werden kann." Die Registrierungsschlüssel werden aktualisiert, wenn eine Projektmappe neu erstellt wird. Daher müssen Sie die frühere Version deinstallieren, bevor Sie die neue Version veröffentlichen, debuggen oder ausführen.  
  
 Um zu verhindern, dass diese Meldung angezeigt wird, erstellen Sie auf dem Entwicklungscomputer ein weiteres Benutzerkonto zum Testen der Bereitstellung. Sie können jedoch auch die Version aus der Liste der auf dem Computer installierten Programme entfernen, bevor Sie die Projektmappe wieder veröffentlichen, debuggen oder erneut erstellen.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Fehler mit nicht abgefangener Ausnahme oder nicht gefundener Methode beim Installieren einer Projektmappe  
 Wenn Sie Office-Projektmappen installieren, indem Sie das Bereitstellungsmanifest (eine VSTO-Datei), eine Office-Anwendung, ein Dokument oder eine Arbeitsmappe öffnen, werden möglicherweise Fehlermeldungen für die folgenden Bedingungen angezeigt:  
  
-   Methode wurde nicht gefunden.  
  
-   MissingMethodException.  
  
-   Nicht abgefangene Ausnahme.  
  
 Um diese Fehler zu vermeiden, installieren Sie die Projektmappe, indem Sie das Setupprogramm ausführen.  
  
 Wenn Sie die Projektmappe installieren, ohne das Setupprogramm auszuführen, werden die erforderlichen Komponenten vom Installationsprogramm nicht überprüft oder installiert. Das Setupprogramm sucht nach der entsprechenden Version der erforderlichen Komponenten und installiert sie gegebenenfalls.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest-Registrierungsschlüssel für Add-Ins ändern, nachdem ein InstallShield Limited Edition-Projekt erstellt wurde  
 Der Manifest-Registrierungsschlüssel, der Teil eines VSTO-Add-In-Setupprogramms ist, wird beim Erstellen des InstallShield Limited Edition-Projekts gelegentlich von ".vsto" in ".dll.manifest" geändert.  
  
 Um dieses Problem zu umgehen, müssen Sie das InstallShield Limited Edition-Projekt in einer anderen Projektmappe erstellen oder für den Registrierungsschlüssel, der den Namen des VSTO-Add-Ins enthält, CompanyName.AddinName als Wert angeben.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Die primären Interop-Assemblys werden vom ClickOnce-Installationsprogramm für die Office-Projektmappe nicht installiert  
 Wenn Sie das Setupprogramm ausführen, das von ClickOnce für die Office-Projektmappe erstellt wird, wird das Installationsprogramm für die primären Interop-Assemblys von Office (PIAs) nur ausgeführt, wenn noch keine PIAs installiert sind.  
  
 Wenn die PIAs vom Setupprogramm nicht ordnungsgemäß installiert werden, installieren Sie diese manuell, indem Sie die Installationsdatei o2007pia.msi aus dem Installationsverzeichnis ausführen.  
  
## <a name="reinstalling-office-solutions-causes-an-argument-out-of-range-exception"></a>Neuinstallation von Office-Projektmappen löst eine Ausnahme (Argument außerhalb des gültigen Bereichs) aus  
 Wenn Sie eine Office-Projektmappe neu installieren, wird möglicherweise eine <xref:System.ArgumentOutOfRangeException> -Ausnahme mit der Fehlermeldung "Das angegebene Argument liegt außerhalb des gültigen Wertebereichs" angezeigt.  
  
 Dieser Fall tritt ein, wenn sich die Groß-/Kleinschreibung für die Installationspfad-URL unterscheidet. Beispielsweise wird dieser Fehler angezeigt, wenn Sie eine Office-Projektmappe das erste Mal von [http://fabrikam.com/ExcelSolution.vsto](http://fabrikam.com/ExcelSolution.vsto) installiert und anschließend [http://fabrikam.com/excelsolution.vsto](http://fabrikam.com/excelsolution.vsto) verwendet haben.  
  
 Sie können diesen Fehler vermeiden, indem Sie beim Installieren von Office-Projektmappen die gleiche Groß-/Kleinschreibung verwenden.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Installieren einer ClickOnce-Projektmappe durch Öffnen des Bereitstellungsmanifests aus dem Web nicht möglich  
 Benutzer können Office-Projektmappen installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Einige Installationen von Internetinformationsdienste (IIS) blockieren jedoch die Dateinamenerweiterung .vsto. Sie müssen den MIME-Typ in IIS definieren, bevor Sie ihn zur Bereitstellung einer Office-Projektmappe verwenden.  
  
 Informationen darüber, wie Sie den MIME-Typ in IIS 6 definieren, finden Sie im Abschnitt zum [Konfigurieren von MIME-Typen (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Informationen darüber, wie Sie den MIME-Typ in IIS 7 definieren, finden Sie unter [Hinzufügen eines MIME-Typs (IIS7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Legen Sie die Erweiterung auf **.vsto** und den MIME-Typ auf **application/x-ms-vsto**fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  