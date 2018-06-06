---
title: Problembehandlung bei Office-projektmappenbereitstellung
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 854264da676ec52d93030371213fa3d8d57eb69f
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693207"
---
# <a name="troubleshoot-office-solution-deployment"></a>Problembehandlung bei Office-projektmappenbereitstellung
  Dieses Thema enthält Informationen zur Lösung von allgemeinen Problemen, die beim Bereitstellen von Office-Projektmappen auftreten können.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Problembehandlung bei Office-Projektmappen mithilfe der Ereignisanzeige  
 Beim Installieren oder Deinstallieren von Office-Lösungen werden von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Fehlermeldungen protokolliert, die Sie mit der Ereignisanzeige in Windows anzeigen können. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations- und Bereitstellungsprobleme zu beheben. Weitere Informationen finden Sie unter [ereignisprotokollierung für Office-Projektmappen](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="change-the-assembly-name-causes-conflicts"></a>Ändern Sie den Assemblynamen führt dazu, dass Konflikte  
 Wenn Sie ändern die **Assemblyname** Wert in der **Anwendung** auf der Seite der **Projekt-Designer** Veröffentlichungstools werden geändert, nachdem bereits eine Projektmappe bereitgestellt wurde, die Setup-Paket in einem *Setup.exe* Datei- und zwei Bereitstellungsmanifeste. Wenn Sie zwei Manifestdateien bereitstellen, treten möglicherweise die folgenden Bedingungen ein:  
  
-   Wenn der Endbenutzer beide Versionen installiert, werden von der Anwendung beide VSTO-Add-Ins geladen.  
  
-   Wurde das VSTO-Add-In vor Änderung des Assemblynamens installiert, empfängt der Endbenutzer niemals Updates.  
  
 Um dies zu verhindern, ändern Sie nicht der Projektmappe **Assemblyname** Wert nach der Bereitstellung der Lösung.  
  
## <a name="check-for-updates-takes-a-long-time"></a>Überprüfen Sie, ob Updates hinweg dauert sehr lange  
 Visual Studio 2010-Tools für Office-Laufzeit bietet es sich um einen Registrierungseintrag, mit denen Administratoren können den Timeoutwert für das Herunterladen der Manifeste und der Projektmappe festlegen.  
  
#### <a name="to-set-the-time-out-value"></a>So legen Sie den Timeoutwert fest  
  
1.  Navigieren Sie in der Registrierung zu folgendem Schlüssel:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**  
  
2.  Legen Sie im Unterschlüssel **AddInTimeout** den Timeoutwert in Millisekunden fest.  
  
     Ist der Unterschlüssel **AddInTimeout** nicht vorhanden, erstellen Sie ihn als DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Kann nicht aktualisiert oder in einer Netzwerkdateifreigabe veröffentlichen  
 Office-Projektmappen, die auf einer Dateifreigabe im Netzwerk möglicherweise eine irreführende Nachricht während eines Updates angezeigt, wenn der Projektmappe *Setup.exe* Datei wird in einem Prozess gesperrt, während das Update veröffentlicht wird. In der Meldung wird möglicherweise Folgendes angezeigt: "Die Datei 'setup.exe' konnte dem Web nicht hinzugefügt werden. Die Datei 'setup.exe' ist in diesem Web bereits vorhanden."  
  
 Eine Dateisperrung verhindern Sie dadurch, dass Sie die Freigabe Endbenutzern nur schreibgeschützt zur Verfügung stellen. Befinden sich Dokumente allerdings in der Freigabe, stehen sie Endbenutzern ebenfalls schreibgeschützt zur Verfügung.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Erforderliche Komponenten für Microsoft Office nicht installiert.  
 Sie können dem Setup-Paket .NET Framework, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]und die primären Interop-Assemblys von Office als erforderliche Komponenten hinzufügen, die mit der Office-Projektmappe bereitgestellt werden. Informationen zum Installieren von primären Interopassemblys finden Sie unter [konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md) und [Vorgehensweise: primären Interopassemblys von Office installieren](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publish-using-localhost-can-cause-installation-problems"></a>Veröffentlichen mithilfe von 'Localhost' kann dazu führen, dass Probleme bei der Installation  
 Bei Verwendung von "http://localhost" als Speicherort Veröffentlichungs- oder Installationsort für Projektmappen auf Dokumentebene, die **Veröffentlichungs-Assistenten** nicht konvertieren der Zeichenfolge in den tatsächlichen Computernamen. In diesem Fall muss die Projektmappe nur auf dem Entwicklungscomputer installiert werden. Damit bereitgestellte Projektmappen auf dem Entwicklungscomputer Internetinformationsdienste verwenden, muss anstelle von localhost der vollqualifizierte Name für alle HTTP/HTTPS/FTP-Speicherorte verwendet werden.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Zwischengespeicherte Assemblys werden anstelle von aktualisierten Assemblys geladen  
 Fusion, das Assemblyladeprogramm von .NET Framework, lädt die zwischengespeicherte Kopie der Assemblys, wenn sich der Projektausgabepfad in einer Netzwerkdateifreigabe befindet, die Assembly mit einem starken Namen signiert ist und die Assemblyversion der Anpassung nicht geändert wird. Wird eine Assembly aktualisiert, die diese Bedingungen erfüllt, wird das Update erst bei der nächsten Ausführung des Projekts angezeigt, da die zwischengespeicherte Kopie geladen wird.  
  
 Visual Studio kann so konfiguriert werden, dass bei jeder Ausführung des Projekts Assemblys von Fusion heruntergeladen werden.  
  
### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>So laden Sie Assemblys herunter, anstatt zwischengespeicherte Kopien zu laden  
  
1.  Wählen Sie in der Menüleiste **Projekt**, * Projektname ***Eigenschaften**.  
  
2.  Wählen Sie auf der Seite **Anwendung** die Option **Assemblyinformationen**.  
  
3.  Im ersten **Assemblyversion** Geben Sie ein Sternchen (\*), und wählen Sie dann die **OK** Schaltfläche.  
  
 Nach dem Ändern der Assemblyversion kann die Signatur der Assembly mit einem starken Namen fortgesetzt werden, und die aktuellste Version der Anpassung wird geladen.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Installationsfehler, wenn der URI-Zeichen enthält, die nicht von US-ASCII-sind  
 Wird eine Office-Projektmappe in einem HTTP/HTTPS/FTP-Speicherort veröffentlicht, darf der Pfad keine Unicode-Zeichen enthalten, die nicht in US-ASCII vorliegen. Solche Zeichen können zu inkonsistentem Verhalten im Setup-Programm führen. Verwenden Sie für den Installationspfad US-ASCII-Zeichen.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Eingabeaufforderung zum manuellen deinstallieren wird angezeigt, beim Veröffentlichen und installieren eine Projektmappe auf dem Entwicklungscomputer  
 Wenn Sie eine Office-Projektmappe erstellen, wird die erstellte Version automatisch registriert. Wenn Sie dieselbe Projektmappe bereits auf dem Entwicklungscomputer veröffentlicht und installiert haben, erkennt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nach der nächsten Erstellung, erneuten Erstellung oder Veröffentlichung der Projektmappe, dass der Installationspfad für die veröffentlichte Version und die erstellte Version unterschiedlich sind. Die Fehlermeldung lautet wie folgt: "Die Anpassung kann nicht installiert werden, weil derzeit eine andere Version installiert ist und von diesem Speicherort nicht aktualisiert werden kann." Die Registrierungsschlüssel werden aktualisiert, wenn eine Projektmappe neu erstellt wird. Daher müssen Sie die frühere Version deinstallieren, bevor Sie die neue Version veröffentlichen, debuggen oder ausführen.  
  
 Um zu verhindern, dass diese Meldung angezeigt wird, erstellen Sie auf dem Entwicklungscomputer ein weiteres Benutzerkonto zum Testen der Bereitstellung. Sie können jedoch auch die Version aus der Liste der auf dem Computer installierten Programme entfernen, bevor Sie die Projektmappe wieder veröffentlichen, debuggen oder erneut erstellen.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nicht abgefangene Ausnahme oder eine Methode nicht gefunden – Fehler bei der Installation einer Projektmappe  
 Wenn Sie Office-Projektmappen installieren, durch Öffnen des Bereitstellungsmanifests (eine *".VSTO"* Datei), Office-Anwendung, ein Dokument oder die Arbeitsmappe, Fehlermeldungen für die folgenden Bedingungen können angezeigt werden:  
  
-   Methode wurde nicht gefunden.  
  
-   MissingMethodException.  
  
-   Nicht abgefangene Ausnahme.  
  
 Um diese Fehler zu vermeiden, installieren Sie die Projektmappe, indem Sie das Setupprogramm ausführen.  
  
 Wenn Sie die Projektmappe installieren, ohne das Setupprogramm auszuführen, werden die erforderlichen Komponenten vom Installationsprogramm nicht überprüft oder installiert. Das Setupprogramm sucht nach der entsprechenden Version der erforderlichen Komponenten und installiert sie gegebenenfalls.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest-Registrierungsschlüssel für Add-Ins ändern, nachdem ein InstallShield Limited Edition-Projekt erstellt wurde  
 Der manifest-Registrierungsschlüssel, die Teil eines VSTO-Add-in-Setupprogramms ist Programmieren in einigen Fällen Änderungen von *".VSTO"* auf *. dll.manifest* Wenn Sie ein InstallShield Limited Edition-Projekt erstellen.  
  
 Um dieses Problem zu umgehen, müssen Sie das InstallShield Limited Edition-Projekt in einer anderen Projektmappe erstellen oder für den Registrierungsschlüssel, der den Namen des VSTO-Add-Ins enthält, CompanyName.AddinName als Wert angeben.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>ClickOnce-Installationsprogramm für die Office-Projektmappe die primären Interop-Assemblys nicht installiert werden.  
 Wenn Sie das Setupprogramm ausführen, das von ClickOnce für die Office-Projektmappe erstellt wird, wird das Installationsprogramm für die primären Interop-Assemblys von Office (PIAs) nur ausgeführt, wenn noch keine PIAs installiert sind.  
  
 Wenn das Setup-Programm ordnungsgemäß installiert wird nicht, installieren Sie diese manuell durch Ausführen der Installationsdatei mit dem Namen *o2007pia.msi* aus dem Installationsverzeichnis.  
  
## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Installieren von Office-Projektmappen Ursachen Argument außerhalb des zulässigen Bereichs  
 Wenn Sie eine Office-Projektmappe neu installieren, wird möglicherweise eine <xref:System.ArgumentOutOfRangeException> -Ausnahme mit der Fehlermeldung "Das angegebene Argument liegt außerhalb des gültigen Wertebereichs" angezeigt.  
  
 Dieser Fall tritt ein, wenn sich die Groß-/Kleinschreibung für die Installationspfad-URL unterscheidet. Angenommen, dieser Fehler angezeigt, wenn Sie eine Office-Projektmappe aus installiert [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) erstmalig und verwendet dann [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) ein zweites Mal.  
  
 Sie können diesen Fehler vermeiden, indem Sie beim Installieren von Office-Projektmappen die gleiche Groß-/Kleinschreibung verwenden.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Eine ClickOnce-Projektmappe kann nicht installiert werden, indem Sie das Bereitstellungsmanifest aus dem Web öffnen  
 Benutzer können Office-Projektmappen installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Allerdings einige Installationen von Internetinformationsdienste (Internet Information Services, IIS) blockiert das *".VSTO"* Dateinamenerweiterung. Sie müssen den MIME-Typ in IIS definieren, bevor Sie ihn zum Bereitstellen einer Office-Projektmappe verwenden.  
  
 Informationen darüber, wie Sie den MIME-Typ in IIS 6 definieren, finden Sie im Abschnitt zum [Konfigurieren von MIME-Typen (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Informationen dazu, wie Sie den MIME-Typ in IIS 7 definieren, finden Sie unter [Hinzufügen eines MIME-Typs (IIS7)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Legen Sie die Erweiterung auf **.vsto** und den MIME-Typ auf **application/x-ms-vsto**fest.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  