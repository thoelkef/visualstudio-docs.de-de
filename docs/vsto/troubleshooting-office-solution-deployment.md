---
title: Problembehandlung bei Office-projektmappenbereitstellung
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bcd102d8717b455a402bceb98e7ce85a2907e3bb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694982"
---
# <a name="troubleshoot-office-solution-deployment"></a>Problembehandlung bei Office-projektmappenbereitstellung
  Dieses Thema enthält Informationen zur Lösung von allgemeinen Problemen, die beim Bereitstellen von Office-Projektmappen auftreten können.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Problembehandlung bei Office-Projektmappen mithilfe der Ereignisanzeige
 Beim Installieren oder Deinstallieren von Office-Lösungen werden von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Fehlermeldungen protokolliert, die Sie mit der Ereignisanzeige in Windows anzeigen können. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations- und Bereitstellungsprobleme zu beheben. Weitere Informationen finden Sie unter [ereignisprotokollierung für Office-Projektmappen](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Ändern Sie den Assemblynamen führt dazu, dass Konflikte
 Wenn Sie ändern die **Assemblyname** Wert in der **Anwendung** auf der Seite die **Projekt-Designer** Veröffentlichungstools werden geändert, nachdem Sie eine Lösung bereits bereitgestellt haben, die Setup-Paket einen *Setup.exe* Datei- und zwei Bereitstellungsmanifeste. Wenn Sie zwei Manifestdateien bereitstellen, treten möglicherweise die folgenden Bedingungen ein:

- Wenn der Endbenutzer beide Versionen installiert, werden von der Anwendung beide VSTO-Add-Ins geladen.

- Wurde das VSTO-Add-In vor Änderung des Assemblynamens installiert, empfängt der Endbenutzer niemals Updates.

  Um dies zu verhindern, ändern Sie nicht der Projektmappe **Assemblyname** Wert nach der Bereitstellung der Lösung.

## <a name="check-for-updates-takes-a-long-time"></a>Überprüfen Sie, ob Updates dauert sehr lange
 Visual Studio 2010-Tools für Office-Laufzeit stellt einen Registrierungseintrag, mit denen Administratoren den Timeoutwert für das Herunterladen der Manifeste und der Projektmappe festlegen.

#### <a name="to-set-the-time-out-value"></a>So legen Sie den Timeoutwert fest

1. Navigieren Sie in der Registrierung zu folgendem Schlüssel:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. Legen Sie im Unterschlüssel **AddInTimeout** den Timeoutwert in Millisekunden fest.

     Ist der Unterschlüssel **AddInTimeout** nicht vorhanden, erstellen Sie ihn als DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Kann nicht aktualisiert oder in einer Netzwerkdateifreigabe veröffentlichen
 Office-Projektmappen, die auf einer Netzwerkdateifreigabe befinden könnte eine irreführende Meldung während eines Updates angezeigt, wenn der Projektmappe *Setup.exe* Datei ist in einem Prozess gesperrt, während das Update veröffentlicht wird. Die Nachricht könnte Folgendes: "Kann nicht'setup.exe' zum Web hinzugefügt. Die Datei 'setup.exe' ist in diesem Web bereits vorhanden."

 Eine Dateisperrung verhindern Sie dadurch, dass Sie die Freigabe Endbenutzern nur schreibgeschützt zur Verfügung stellen. Befinden sich Dokumente allerdings in der Freigabe, stehen sie Endbenutzern ebenfalls schreibgeschützt zur Verfügung.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Voraussetzungen für die Microsoft Office nicht installiert.
 Sie können dem Setup-Paket .NET Framework, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]und die primären Interop-Assemblys von Office als erforderliche Komponenten hinzufügen, die mit der Office-Projektmappe bereitgestellt werden. Informationen zum Installieren von primären interop-Assemblys finden Sie unter [konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/configuring-a-computer-to-develop-office-solutions.md) und [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Veröffentlichen mithilfe von 'Localhost' kann dazu führen, dass Probleme bei der Installation
 Bei Verwendung von "<http://localhost>" als die Veröffentlichungs- oder Installationsort für Projektmappen auf Anwendungsebene, die **Veröffentlichungs-Assistenten** konvertieren Sie die Zeichenfolge nicht in den tatsächlichen Computernamen. In diesem Fall muss die Projektmappe nur auf dem Entwicklungscomputer installiert werden. Damit bereitgestellte Projektmappen auf dem Entwicklungscomputer Internetinformationsdienste verwenden, muss anstelle von localhost der vollqualifizierte Name für alle HTTP/HTTPS/FTP-Speicherorte verwendet werden.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Werden zwischengespeicherte Assemblys geladen, anstelle von aktualisierten Assemblys
 Fusion, das Assemblyladeprogramm von .NET Framework, lädt die zwischengespeicherte Kopie der Assemblys, wenn sich der Projektausgabepfad in einer Netzwerkdateifreigabe befindet, die Assembly mit einem starken Namen signiert ist und die Assemblyversion der Anpassung nicht geändert wird. Wird eine Assembly aktualisiert, die diese Bedingungen erfüllt, wird das Update erst bei der nächsten Ausführung des Projekts angezeigt, da die zwischengespeicherte Kopie geladen wird.

 Visual Studio kann so konfiguriert werden, dass bei jeder Ausführung des Projekts Assemblys von Fusion heruntergeladen werden.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>So laden Sie Assemblys herunter, anstatt zwischengespeicherte Kopien zu laden

1. Wählen Sie auf der Menüleiste **Projekt**, _ProjectName_**Eigenschaften**.

2. Wählen Sie auf der Seite **Anwendung** die Option **Assemblyinformationen**.

3. In der ersten **Assemblyversion** Geben Sie ein Sternchen (\*), und wählen Sie dann die **OK** Schaltfläche.

   Nach dem Ändern der Assemblyversion kann die Signatur der Assembly mit einem starken Namen fortgesetzt werden, und die aktuellste Version der Anpassung wird geladen.

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Installation schlägt fehl, wenn der URI, die nicht von US-ASCII-Zeichen verfügt über
 Wird eine Office-Projektmappe in einem HTTP/HTTPS/FTP-Speicherort veröffentlicht, darf der Pfad keine Unicode-Zeichen enthalten, die nicht in US-ASCII vorliegen. Solche Zeichen können zu inkonsistentem Verhalten im Setup-Programm führen. Verwenden Sie für den Installationspfad US-ASCII-Zeichen.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Eingabeaufforderung zum manuellen deinstallieren, das angezeigt wird, wenn Sie veröffentlichen und installieren Sie eine Lösung auf dem Entwicklungscomputer
 Wenn Sie eine Office-Projektmappe erstellen, wird die erstellte Version automatisch registriert. Wenn Sie dieselbe Projektmappe bereits auf dem Entwicklungscomputer veröffentlicht und installiert haben, erkennt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nach der nächsten Erstellung, erneuten Erstellung oder Veröffentlichung der Projektmappe, dass der Installationspfad für die veröffentlichte Version und die erstellte Version unterschiedlich sind. Die Fehlermeldung lautet wie folgt: "Die Anpassung kann nicht installiert werden, weil derzeit eine andere Version installiert ist und von diesem Speicherort nicht aktualisiert werden kann." Die Registrierungsschlüssel werden aktualisiert, wenn eine Projektmappe neu erstellt wird. Daher müssen Sie die frühere Version deinstallieren, bevor Sie die neue Version veröffentlichen, debuggen oder ausführen.

 Um zu verhindern, dass diese Meldung angezeigt wird, erstellen Sie auf dem Entwicklungscomputer ein weiteres Benutzerkonto zum Testen der Bereitstellung. Sie können jedoch auch die Version aus der Liste der auf dem Computer installierten Programme entfernen, bevor Sie die Projektmappe wieder veröffentlichen, debuggen oder erneut erstellen.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nicht abgefangene Ausnahme oder eine Methode nicht gefunden – Fehler bei der Installation einer lösungs
 Bei der Installation von Office-Projektmappen öffnen Sie das Bereitstellungsmanifest (eine *".VSTO"* Datei), können Office-Anwendung, Dokument oder eine Arbeitsmappe, Fehlermeldungen für die folgenden Bedingungen angezeigt werden:

- Methode wurde nicht gefunden.

- MissingMethodException.

- Nicht abgefangene Ausnahme.

  Um diese Fehler zu vermeiden, installieren Sie die Projektmappe, indem Sie das Setupprogramm ausführen.

  Wenn Sie die Projektmappe installieren, ohne das Setupprogramm auszuführen, werden die erforderlichen Komponenten vom Installationsprogramm nicht überprüft oder installiert. Das Setupprogramm sucht nach der entsprechenden Version der erforderlichen Komponenten und installiert sie gegebenenfalls.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifest-Registrierungsschlüssel für Add-Ins ändern, nachdem ein InstallShield Limited Edition-Projekt erstellt wird
 Der manifest-Registrierungsschlüssel, der einem VSTO-Add-in-Setup gehört, Programmieren in einigen Fällen Änderungen von *".VSTO"* zu *. dll.manifest* Wenn Sie ein InstallShield Limited Edition-Projekt erstellen.

 Um dieses Problem zu umgehen, müssen Sie das InstallShield Limited Edition-Projekt in einer anderen Projektmappe erstellen oder für den Registrierungsschlüssel, der den Namen des VSTO-Add-Ins enthält, CompanyName.AddinName als Wert angeben.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>ClickOnce-Installationsprogramms für die Office-Projektmappe die primären Interopassemblys nicht installiert werden.
 Wenn Sie das Setupprogramm ausführen, das von ClickOnce für die Office-Projektmappe erstellt wird, wird das Installationsprogramm für die primären Interop-Assemblys von Office (PIAs) nur ausgeführt, wenn noch keine PIAs installiert sind.

 Wenn das Setup-Programm die PIAs nicht ordnungsgemäß installiert nicht ist, installieren Sie sie manuell durch Ausführen der Installationsdatei mit dem Namen *o2007pia.msi* aus dem Installationsverzeichnis.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Installieren von Office-Projektmappen bewirkt, dass ein Argument außerhalb des zulässigen Bereichs
 Wenn Sie eine Office-Projektmappe neu installieren einer <xref:System.ArgumentOutOfRangeException> Ausnahme möglicherweise mit der folgenden Fehlermeldung angezeigt: Angegebene Argument wurde außerhalb des Bereichs der gültigen Werte.

 Dieser Fall tritt ein, wenn sich die Groß-/Kleinschreibung für die Installationspfad-URL unterscheidet. Angenommen, dieser Fehler angezeigt, wenn Sie über eine Office-Projektmappe installiert [ http://fabrikam.com/ExcelSolution.vsto ](http://fabrikam.com/ExcelSolution.vsto) beim ersten dann [ http://fabrikam.com/excelsolution.vsto ](http://fabrikam.com/excelsolution.vsto) beim zweiten Mal.

 Sie können diesen Fehler vermeiden, indem Sie beim Installieren von Office-Projektmappen die gleiche Groß-/Kleinschreibung verwenden.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Eine ClickOnce-Projektmappe kann nicht installiert werden, indem Sie das Bereitstellungsmanifest aus dem Web öffnen
 Benutzer können Office-Projektmappen installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Einige Installationen von Internet Information Services (IIS) blockiert jedoch die *".VSTO"* Dateinamenerweiterung. Sie müssen den MIME-Typ in IIS definieren, bevor Sie sie zum Bereitstellen einer Office-Projektmappe verwenden.

 Informationen dazu, wie Sie den MIME-Typ in IIS 7 definieren, finden Sie unter [Hinzufügen eines MIME-Typs (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Legen Sie die Erweiterung auf **.vsto** und den MIME-Typ auf **application/x-ms-vsto**fest.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
- [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)
