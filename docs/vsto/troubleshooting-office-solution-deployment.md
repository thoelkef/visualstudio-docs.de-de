---
title: Fehlerbehebung bei der Bereitstellung von Office-Lösungen
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
ms.openlocfilehash: de036ce9b0b566a6028b0ccfe45cfe5f2ac49da9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444933"
---
# <a name="troubleshoot-office-solution-deployment"></a>Fehlerbehebung bei der Bereitstellung von Office-Lösungen
  Dieses Thema enthält Informationen zur Lösung von allgemeinen Problemen, die beim Bereitstellen von Office-Projektmappen auftreten können.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Beheben von Office-Lösungen mithilfe der Ereignisanzeige
 Beim Installieren oder Deinstallieren von Office-Lösungen werden von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Fehlermeldungen protokolliert, die Sie mit der Ereignisanzeige in Windows anzeigen können. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations- und Bereitstellungsprobleme zu beheben. Weitere Informationen finden Sie unter [Ereignisprotokollierung für Office-Lösungen](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Ändern des Assemblynamens verursacht Konflikte
 Wenn Sie den Wert **Assemblyname** auf der **Anwendungsseite** des **Projekt-Designers** ändern, nachdem Sie bereits eine Projektmappe bereitgestellt haben, ändern die Veröffentlichungstools das Setuppaket so, dass es über eine *Setup.exe-Datei* und zwei Bereitstellungsmanifeste verfügt. Wenn Sie zwei Manifestdateien bereitstellen, treten möglicherweise die folgenden Bedingungen ein:

- Wenn der Endbenutzer beide Versionen installiert, werden von der Anwendung beide VSTO-Add-Ins geladen.

- Wurde das VSTO-Add-In vor Änderung des Assemblynamens installiert, empfängt der Endbenutzer niemals Updates.

  Um diese Bedingungen zu vermeiden, ändern Sie den **Assemblynamenwert** der Lösung nicht, nachdem Sie die Lösung bereitgestellt haben.

## <a name="check-for-updates-takes-a-long-time"></a>Überprüfung auf Aktualisierungen dauert lange
 Visual Studio 2010 Tools for Office-Laufzeit bietet einen Registrierungseintrag, mit dem Administratoren den Timeoutwert für das Herunterladen der Manifeste und der Lösung festlegen können.

#### <a name="to-set-the-time-out-value"></a>So legen Sie den Timeoutwert fest

1. Navigieren Sie in der Registrierung zu folgendem Schlüssel:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. Legen Sie im Unterschlüssel **AddInTimeout** den Timeoutwert in Millisekunden fest.

     Ist der Unterschlüssel **AddInTimeout** nicht vorhanden, erstellen Sie ihn als DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>Kann nicht aktualisiert oder in einer Netzwerkdateifreigabe veröffentlicht werden
 Office-Lösungen, die sich auf einer Netzwerkdateifreigabe befinden, zeigen möglicherweise eine irreführende Meldung während aktualisierungen an, wenn die *Datei Setup.exe* der Projektmappe während der Veröffentlichung des Updates in einem Prozess gesperrt ist. In der Meldung wird möglicherweise Folgendes angezeigt: "Die Datei 'setup.exe' konnte dem Web nicht hinzugefügt werden. Die Datei 'setup.exe' ist in diesem Web bereits vorhanden."

 Eine Dateisperrung verhindern Sie dadurch, dass Sie die Freigabe Endbenutzern nur schreibgeschützt zur Verfügung stellen. Befinden sich Dokumente allerdings in der Freigabe, stehen sie Endbenutzern ebenfalls schreibgeschützt zur Verfügung.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Voraussetzungen für Microsoft Office sind nicht installiert
 Sie können dem Setup-Paket .NET Framework, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]und die primären Interop-Assemblys von Office als erforderliche Komponenten hinzufügen, die mit der Office-Projektmappe bereitgestellt werden. Informationen zum Installieren der primären Interopassemblys finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office-Lösungen](../vsto/configuring-a-computer-to-develop-office-solutions.md) und [Gewusst wie: Installieren der primären Interopassemblys von Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>Die Veröffentlichung mit Localhost kann Installationsprobleme verursachen
 Wenn Sie `http://localhost` als Veröffentlichungs- oder Installationsspeicherort für Lösungen auf Dokumentebene verwenden, konvertiert der **Veröffentlichungs-Assistent** die Zeichenfolge nicht in den echten Computernamen. In diesem Fall muss die Projektmappe nur auf dem Entwicklungscomputer installiert werden. Damit bereitgestellte Projektmappen auf dem Entwicklungscomputer Internetinformationsdienste verwenden, muss anstelle von localhost der vollqualifizierte Name für alle HTTP/HTTPS/FTP-Speicherorte verwendet werden.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Zwischengespeicherte Assemblys werden anstelle aktualisierter Assemblys geladen
 Fusion, das Assemblyladeprogramm von .NET Framework, lädt die zwischengespeicherte Kopie der Assemblys, wenn sich der Projektausgabepfad in einer Netzwerkdateifreigabe befindet, die Assembly mit einem starken Namen signiert ist und die Assemblyversion der Anpassung nicht geändert wird. Wird eine Assembly aktualisiert, die diese Bedingungen erfüllt, wird das Update erst bei der nächsten Ausführung des Projekts angezeigt, da die zwischengespeicherte Kopie geladen wird.

 Visual Studio kann so konfiguriert werden, dass bei jeder Ausführung des Projekts Assemblys von Fusion heruntergeladen werden.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>So laden Sie Assemblys herunter, anstatt zwischengespeicherte Kopien zu laden

1. Wählen Sie in der Menüleiste **Project**, _ProjectName_**Properties**aus.

2. Wählen Sie auf der Seite **Anwendung** die Option **Assemblyinformationen**.

3. Legen Sie die Revisionsnummer, das dritte Feld der\* **Assemblyversion**, auf eine Platzhalterkarte fest ( ). Beispiel: "1.0.*".  Wählen Sie dann die **Schaltfläche OK.**

   Nach dem Ändern der Assemblyversion kann die Signatur der Assembly mit einem starken Namen fortgesetzt werden, und die aktuellste Version der Anpassung wird geladen.

 [!NOTE]
> Ab Visual Studio 2017 tritt ein Buildfehler auf, wenn Sie versuchen, Platzhalter in der Assemblyversion zu verwenden.  Dies liegt daran, dass Platzkarten in der Assemblyversion die MSBuild Deterministic-Funktion aufbrechen. Sie werden angewiesen, entweder die Platzhalter aus der Assemblyversion zu entfernen oder den Determinismus zu deaktivieren.  Weitere Informationen zur Deterministischen Funktion finden Sie unter: [Allgemeine MSBuild-Projekteigenschaften](../msbuild/common-msbuild-project-properties.md) und [Anpassen Ihres Builds](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Die Installation schlägt fehl, wenn der URI Zeichen enthält, die nicht US-ASCII sind
 Wird eine Office-Projektmappe in einem HTTP/HTTPS/FTP-Speicherort veröffentlicht, darf der Pfad keine Unicode-Zeichen enthalten, die nicht in US-ASCII vorliegen. Solche Zeichen können zu inkonsistentem Verhalten im Setup-Programm führen. Verwenden Sie für den Installationspfad US-ASCII-Zeichen.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Beim Veröffentlichen und Installieren einer Lösung auf dem Entwicklungscomputer wird die Aufforderung zur manuellen Deinstallation angezeigt.
 Wenn Sie eine Office-Projektmappe erstellen, wird die erstellte Version automatisch registriert. Wenn Sie dieselbe Projektmappe bereits auf dem Entwicklungscomputer veröffentlicht und installiert haben, erkennt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nach der nächsten Erstellung, erneuten Erstellung oder Veröffentlichung der Projektmappe, dass der Installationspfad für die veröffentlichte Version und die erstellte Version unterschiedlich sind. Die Fehlermeldung lautet wie folgt: "Die Anpassung kann nicht installiert werden, weil derzeit eine andere Version installiert ist und von diesem Speicherort nicht aktualisiert werden kann." Die Registrierungsschlüssel werden aktualisiert, wenn eine Projektmappe neu erstellt wird. Daher müssen Sie die frühere Version deinstallieren, bevor Sie die neue Version veröffentlichen, debuggen oder ausführen.

 Um zu verhindern, dass diese Meldung angezeigt wird, erstellen Sie auf dem Entwicklungscomputer ein weiteres Benutzerkonto zum Testen der Bereitstellung. Sie können jedoch auch die Version aus der Liste der auf dem Computer installierten Programme entfernen, bevor Sie die Projektmappe wieder veröffentlichen, debuggen oder erneut erstellen.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Nicht abgefangene Ausnahme oder Methode wurde beim Installieren einer Lösung nicht gefunden
 Wenn Sie Office-Lösungen installieren, indem Sie das Bereitstellungsmanifest (eine *.vsto-Datei),* eine Office-Anwendung, ein Dokument oder eine Arbeitsmappe öffnen, werden möglicherweise Fehlermeldungen zu den folgenden Bedingungen angezeigt:

- Methode wurde nicht gefunden.

- MissingMethodException.

- Nicht abgefangene Ausnahme.

  Um diese Fehler zu vermeiden, installieren Sie die Projektmappe, indem Sie das Setupprogramm ausführen.

  Wenn Sie die Projektmappe installieren, ohne das Setupprogramm auszuführen, werden die erforderlichen Komponenten vom Installationsprogramm nicht überprüft oder installiert. Das Setupprogramm sucht nach der entsprechenden Version der erforderlichen Komponenten und installiert sie gegebenenfalls.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifestregistrierungsschlüssel für Add-Ins ändern sich, nachdem ein InstallShield Limited Edition-Projekt erstellt wurde
 Der Manifestregistrierungsschlüssel, der Teil eines VSTO-Add-In-Setupprogramms ist, ändert sich manchmal von *.vsto* zu *.dll.manifest,* wenn Sie ein InstallShield Limited Edition-Projekt erstellen.

 Um dieses Problem zu umgehen, müssen Sie das InstallShield Limited Edition-Projekt in einer anderen Projektmappe erstellen oder für den Registrierungsschlüssel, der den Namen des VSTO-Add-Ins enthält, CompanyName.AddinName als Wert angeben.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>Der ClickOnce Installer für Ihre Office-Lösung installiert nicht die primären Interopassemblys
 Wenn Sie das Setupprogramm ausführen, das von ClickOnce für die Office-Projektmappe erstellt wird, wird das Installationsprogramm für die primären Interop-Assemblys von Office (PIAs) nur ausgeführt, wenn noch keine PIAs installiert sind.

 Wenn das Setupprogramm die PIAs nicht ordnungsgemäß installiert, installieren Sie sie manuell, indem Sie die Installationsdatei mit dem Namen *o2007pia.msi* aus dem Installationsverzeichnis ausführen.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>Neuinstallieren von Office-Lösungen verursacht ein Argument a-range-Ausnahme
 Wenn Sie eine Office-Projektmappe neu installieren, wird möglicherweise eine <xref:System.ArgumentOutOfRangeException> -Ausnahme mit der Fehlermeldung "Das angegebene Argument liegt außerhalb des gültigen Wertebereichs" angezeigt.

 Dieser Fall tritt ein, wenn sich die Groß-/Kleinschreibung für die Installationspfad-URL unterscheidet. Dieser Fehler wird z. B. angezeigt, `http://fabrikam.com/ExcelSolution.vsto` wenn Sie eine `http://fabrikam.com/excelsolution.vsto` Office-Lösung vom ersten Mal installiert und dann das zweite Mal verwendet haben.

 Sie können diesen Fehler vermeiden, indem Sie beim Installieren von Office-Projektmappen die gleiche Groß-/Kleinschreibung verwenden.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Eine ClickOnce-Lösung kann nicht installiert werden, indem das Bereitstellungsmanifest aus dem Web geöffnet wird.
 Benutzer können Office-Projektmappen installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Einige Installationen von InternetInformationsdiensten (Internet Information Services, IIS) blockieren jedoch die *Erweiterung .vsto-Dateinamen.* Sie müssen den MIME-Typ in IIS definieren, bevor Sie ihn zum Bereitstellen einer Office-Lösung verwenden.

 Informationen zum Definieren des MIME-Typs in IIS 7 finden Sie [unter Hinzufügen eines MIME-Typs (IIS7)](https://technet.microsoft.com/library/cc725608(WS.10).aspx).

 Legen Sie die Erweiterung auf **.vsto** und den MIME-Typ auf **application/x-ms-vsto**fest.

## <a name="see-also"></a>Weitere Informationen

- [Fehlerbehebung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
- [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)
