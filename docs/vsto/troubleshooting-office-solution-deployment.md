---
title: "Problembehandlung bei der Office-Projektmappenbereitstellung"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ClickOnce-Bereitstellung [Office-Entwicklung in Visual Studio], Problembehandlung"
  - "Office-Entwicklung in Visual Studio, Problembehandlung"
  - "Bereitstellen von Anwendungen [Office-Entwicklung in Visual Studio], Problembehandlung"
ms.assetid: 2206aeb6-44b3-4786-ba99-9c7dad5cce7c
caps.latest.revision: 74
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 73
---
# Problembehandlung bei der Office-Projektmappenbereitstellung
  Dieses Thema enthält Informationen zur Lösung von allgemeinen Problemen, die beim Bereitstellen von Office\-Projektmappen auftreten können.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Problembehandlung für Office\-Projektmappen mit der Ereignisanzeige  
 Beim Installieren oder Deinstallieren von Office\-Lösungen werden von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Fehlermeldungen protokolliert, die Sie mit der Ereignisanzeige in Windows anzeigen können. Sie können diese Meldungen aus der Ereignisprotokollierung verwenden, um Installations\- und Bereitstellungsprobleme zu beheben. Weitere Informationen finden Sie unter [Ereignisprotokollierung für Office-Lösungen](../vsto/event-logging-for-office-solutions.md).  
  
## Konflikte nach Änderung des Assemblynamens  
 Wird der Wert **Assemblyname** auf der Seite **Anwendung** von **Projekt\-Designer** geändert, nachdem bereits eine Projektmappe bereitgestellt wurde, wird das Setup\-Paket von Veröffentlichungstools so geändert, dass es eine Datei vom Typ Setup.exe und zwei Bereitstellungsmanifeste beinhaltet. Wenn Sie zwei Manifestdateien bereitstellen, treten möglicherweise die folgenden Bedingungen ein:  
  
-   Wenn der Endbenutzer beide Versionen installiert, werden von der Anwendung beide VSTO\-Add\-Ins geladen.  
  
-   Wurde das VSTO\-Add\-In vor Änderung des Assemblynamens installiert, empfängt der Endbenutzer niemals Updates.  
  
 Um dies zu verhindern, darf der Wert **Assemblyname** der Projektmappe nach deren Bereitstellung nicht geändert werden.  
  
## Die Suche nach Updates nimmt viel Zeit in Anspruch  
 Visual Studio 2010\-Tools für Office\-Laufzeit stellt einen Registrierungseintrag zur Verfügung, mit dem Administratoren den Timeoutwert für das Herunterladen der Manifeste und der Projektmappe festlegen können.  
  
#### So legen Sie den Timeoutwert fest  
  
1.  Navigieren Sie in der Registrierung zu folgendem Schlüssel:  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\VSTA  
  
2.  Legen Sie im Unterschlüssel **AddInTimeout** den Timeoutwert in Millisekunden fest.  
  
     Ist der Unterschlüssel **AddInTimeout** nicht vorhanden, erstellen Sie ihn als DWORD.  
  
## Aktualisieren oder Veröffentlichen auf einer Netzwerkdateifreigabe nicht möglich  
 Office\-Projektmappen in einer Netzwerkdateifreigabe zeigen während Updates unter Umständen eine irreführende Meldung an, falls die Datei Setup.exe der Projektmappe bei Veröffentlichung des Updates in einem Prozess gesperrt ist. In der Meldung wird möglicherweise Folgendes angezeigt: "Die Datei 'setup.exe' konnte dem Web nicht hinzugefügt werden. Die Datei 'setup.exe' ist in diesem Web bereits vorhanden."  
  
 Eine Dateisperrung verhindern Sie dadurch, dass Sie die Freigabe Endbenutzern nur schreibgeschützt zur Verfügung stellen. Befinden sich Dokumente allerdings in der Freigabe, stehen sie Endbenutzern ebenfalls schreibgeschützt zur Verfügung.  
  
## Erforderliche Komponenten für Microsoft Office sind nicht installiert  
 Sie können dem Setup\-Paket .NET Framework, die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] und die primären Interop\-Assemblys von Office als erforderliche Komponenten hinzufügen, die mit der Office\-Projektmappe bereitgestellt werden. Informationen zum Installieren der primären Interopassemblys finden Sie unter [Konfigurieren eines Computers zum Entwickeln von Office-Lösungen](../vsto/configuring-a-computer-to-develop-office-solutions.md) und [Gewusst wie: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## Veröffentlichungen mithilfe von 'Localhost' können zu Installationsproblemen führen  
 Bei Verwendung von "http:\/\/localhost" als Veröffentlichungs\- oder Installationsort für Projektmappen auf Anwendungsebene konvertiert der **Veröffentlichungs\-Assistent** die Zeichenfolge nicht in den tatsächlichen Computernamen. In diesem Fall muss die Projektmappe nur auf dem Entwicklungscomputer installiert werden. Damit bereitgestellte Projektmappen auf dem Entwicklungscomputer Internetinformationsdienste verwenden, muss anstelle von localhost der vollqualifizierte Name für alle HTTP\/HTTPS\/FTP\-Speicherorte verwendet werden.  
  
## Anstelle von aktualisierten Assemblys werden zwischengespeicherte Assemblys geladen  
 Fusion, das Assemblyladeprogramm von .NET Framework, lädt die zwischengespeicherte Kopie der Assemblys, wenn sich der Projektausgabepfad in einer Netzwerkdateifreigabe befindet, die Assembly mit einem starken Namen signiert ist und die Assemblyversion der Anpassung nicht geändert wird. Wird eine Assembly aktualisiert, die diese Bedingungen erfüllt, wird das Update erst bei der nächsten Ausführung des Projekts angezeigt, da die zwischengespeicherte Kopie geladen wird.  
  
 Visual Studio kann so konfiguriert werden, dass bei jeder Ausführung des Projekts Assemblys von Fusion heruntergeladen werden.  
  
#### So laden Sie Assemblys herunter, anstatt zwischengespeicherte Kopien zu laden  
  
1.  Wählen Sie in der Menüleiste **Projekt** und die Option *ProjectName***\-Eigenschaften** aus.  
  
2.  Wählen Sie auf der Seite **Anwendung** die Option **Assemblyinformationen**.  
  
3.  Geben Sie im ersten Feld **Assemblyversion** ein Sternchen \(\*\) ein, und wählen Sie dann die Schaltfläche **OK**.  
  
 Nach dem Ändern der Assemblyversion kann die Signatur der Assembly mit einem starken Namen fortgesetzt werden, und die aktuellste Version der Anpassung wird geladen.  
  
## Installationsfehler, wenn der URI andere Zeichen als US\-ASCII beinhaltet  
 Wird eine Office\-Projektmappe in einem HTTP\/HTTPS\/FTP\-Speicherort veröffentlicht, darf der Pfad keine Unicode\-Zeichen enthalten, die nicht in US\-ASCII vorliegen. Solche Zeichen können zu inkonsistentem Verhalten im Setup\-Programm führen. Verwenden Sie für den Installationspfad US\-ASCII\-Zeichen.  
  
## Eingabeaufforderung zum manuellen Deinstallieren wird angezeigt, wenn Sie eine Projektmappe auf dem Entwicklungscomputer veröffentlichen und installieren  
 Wenn Sie eine Office\-Projektmappe erstellen, wird die erstellte Version automatisch registriert. Wenn Sie dieselbe Projektmappe bereits auf dem Entwicklungscomputer veröffentlicht und installiert haben, erkennt [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nach der nächsten Erstellung, erneuten Erstellung oder Veröffentlichung der Projektmappe, dass der Installationspfad für die veröffentlichte Version und die erstellte Version unterschiedlich sind. Die Fehlermeldung lautet wie folgt: "Die Anpassung kann nicht installiert werden, weil derzeit eine andere Version installiert ist und von diesem Speicherort nicht aktualisiert werden kann." Die Registrierungsschlüssel werden aktualisiert, wenn eine Projektmappe neu erstellt wird. Daher müssen Sie die frühere Version deinstallieren, bevor Sie die neue Version veröffentlichen, debuggen oder ausführen.  
  
 Um zu verhindern, dass diese Meldung angezeigt wird, erstellen Sie auf dem Entwicklungscomputer ein weiteres Benutzerkonto zum Testen der Bereitstellung. Sie können jedoch auch die Version aus der Liste der auf dem Computer installierten Programme entfernen, bevor Sie die Projektmappe wieder veröffentlichen, debuggen oder erneut erstellen.  
  
## Fehler mit nicht abgefangener Ausnahme oder nicht gefundener Methode beim Installieren einer Projektmappe  
 Wenn Sie Office\-Projektmappen installieren, indem Sie das Bereitstellungsmanifest \(eine VSTO\-Datei\), eine Office\-Anwendung, ein Dokument oder eine Arbeitsmappe öffnen, werden möglicherweise Fehlermeldungen für die folgenden Bedingungen angezeigt:  
  
-   Methode wurde nicht gefunden.  
  
-   MissingMethodException.  
  
-   Nicht abgefangene Ausnahme.  
  
 Um diese Fehler zu vermeiden, installieren Sie die Projektmappe, indem Sie das Setupprogramm ausführen.  
  
 Wenn Sie die Projektmappe installieren, ohne das Setupprogramm auszuführen, werden die erforderlichen Komponenten vom Installationsprogramm nicht überprüft oder installiert. Das Setupprogramm sucht nach der entsprechenden Version der erforderlichen Komponenten und installiert sie gegebenenfalls.  
  
## Manifest\-Registrierungsschlüssel für Add\-Ins ändern, nachdem ein InstallShield Limited Edition\-Projekt erstellt wurde  
 Der Manifest\-Registrierungsschlüssel, der Teil eines VSTO\-Add\-In\-Setupprogramms ist, wird beim Erstellen des InstallShield Limited Edition\-Projekts gelegentlich von ".vsto" in ".dll.manifest" geändert.  
  
 Um dieses Problem zu umgehen, müssen Sie das InstallShield Limited Edition\-Projekt in einer anderen Projektmappe erstellen oder für den Registrierungsschlüssel, der den Namen des VSTO\-Add\-Ins enthält, CompanyName.AddinName als Wert angeben.  
  
## Die primären Interop\-Assemblys werden vom ClickOnce\-Installationsprogramm für die Office\-Projektmappe nicht installiert  
 Wenn Sie das Setupprogramm ausführen, das von ClickOnce für die Office\-Projektmappe erstellt wird, wird das Installationsprogramm für die primären Interop\-Assemblys von Office \(PIAs\) nur ausgeführt, wenn noch keine PIAs installiert sind.  
  
 Wenn die PIAs vom Setupprogramm nicht ordnungsgemäß installiert werden, installieren Sie diese manuell, indem Sie die Installationsdatei o2007pia.msi aus dem Installationsverzeichnis ausführen.  
  
## Neuinstallation von Office\-Projektmappen löst eine Ausnahme \(Argument außerhalb des gültigen Bereichs\) aus  
 Wenn Sie eine Office\-Projektmappe neu installieren, wird möglicherweise eine <xref:System.ArgumentOutOfRangeException>\-Ausnahme mit der Fehlermeldung "Das angegebene Argument liegt außerhalb des gültigen Wertebereichs" angezeigt.  
  
 Dieser Fall tritt ein, wenn sich die Groß\-\/Kleinschreibung für die Installationspfad\-URL unterscheidet. Beispielsweise wird dieser Fehler angezeigt, wenn Sie eine Office\-Projektmappe das erste Mal von [http:\/\/fabrikam.com\/ExcelSolution.vsto](http://fabrikam.com/ExcelSolution.vsto) installiert und anschließend [http:\/\/fabrikam.com\/excelsolution.vsto](http://fabrikam.com/excelsolution.vsto) verwendet haben.  
  
 Sie können diesen Fehler vermeiden, indem Sie beim Installieren von Office\-Projektmappen die gleiche Groß\-\/Kleinschreibung verwenden.  
  
## Installieren einer ClickOnce\-Projektmappe durch Öffnen des Bereitstellungsmanifests aus dem Web nicht möglich  
 Benutzer können Office\-Projektmappen installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Einige Installationen von Internetinformationsdienste \(IIS\) blockieren jedoch die Dateinamenerweiterung .vsto. Sie müssen den MIME\-Typ in IIS definieren, bevor Sie ihn zur Bereitstellung einer Office\-Projektmappe verwenden.  
  
 Informationen darüber, wie Sie den MIME\-Typ in IIS 6 definieren, finden Sie im Abschnitt zum [Konfigurieren von MIME\-Typen \(IIS 6.0\)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Informationen darüber, wie Sie den MIME\-Typ in IIS 7 definieren, finden Sie unter [Hinzufügen eines MIME\-Typs \(IIS7\)](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Legen Sie die Erweiterung auf **.vsto** und den MIME\-Typ auf **application\/x\-ms\-vsto** fest.  
  
## Siehe auch  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
  