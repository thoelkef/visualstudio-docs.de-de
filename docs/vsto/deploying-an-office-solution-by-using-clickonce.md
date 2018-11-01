---
title: Bereitstellen einer Office-Projektmappe mit ClickOnce
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e46a0bdc23ee16c4821d3da751d5a90aa62a14c3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673067"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Bereitstellen einer Office-Projektmappe mit ClickOnce
  Wenn Sie ClickOnce verwenden, können Sie die Office-Projektmappe in weniger Schritten bereitstellen. Wenn Sie Updates veröffentlichen, erkennt die Projektmappe sie automatisch und installiert sie. Für ClickOnce ist es jedoch erforderlich, die Projektmappe für jeden Benutzer eines Computers separat zu installieren. Aus diesem Grund sollten Sie erwägen, mithilfe von Windows Installer (*MSI*), wenn mehr als ein Benutzer die Lösung auf dem gleichen Computer ausgeführt wird.  

## <a name="in-this-topic"></a>In diesem Thema  

- [Veröffentlichen Sie die Projektmappe](#Publish)  

- [Entscheiden Sie, wie der Projektmappe Vertrauenswürdigkeit gewährt werden sollen.](#Trust)  

- [Unterstützen von Benutzern, die die Lösung installieren](#Helping)  

- [Kopieren des Dokuments einer Projektmappe auf der Endbenutzer Computer (nur Anpassungen auf Dokumentebene)](#Put)  

- [Kopieren des Dokuments einer Projektmappe auf einem Server mit SharePoint (nur Anpassungen auf Dokumentebene)](#SharePoint)  

- [Erstellen eines benutzerdefinierten Installationsprogramms](#Custom)  

- [Veröffentlichen eines Updates](#Update)  

- [Ändern des Installationspfads einer Projektmappe](#Location)  

- [Zurücksetzen der Projektmappe auf eine frühere version](#Roll)  

  Weitere Informationen zum Bereitstellen einer Office-Projektmappe durch Erstellung einer Windows Installer-Datei finden Sie unter [Bereitstellen einer Office-Projektmappe mit Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  

##  <a name="Publish"></a> Veröffentlichen Sie die Projektmappe  
 Sie können Ihre Lösung veröffentlichen, mit der **Veröffentlichungs-Assistenten** oder **Projekt-Designer**. In diesem Verfahren verwenden Sie die **Projekt-Designer** da es sich um den vollständigen Satz von Veröffentlichungsoptionen bereitstellt. Finden Sie unter [Veröffentlichungs-Assistenten &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  

#### <a name="to-publish-the-solution"></a>So veröffentlichen Sie die Projektmappe  

1. In **Projektmappen-Explorer**, wählen Sie den Knoten, die für Ihr Projekt benannt ist.  

2. Wählen Sie auf der Menüleiste **Projekt**, *ProjectName* **Eigenschaften**.  

3. In der **Projekt-Designer**, wählen Sie die **veröffentlichen** Registerkarte, die die folgende Abbildung zeigt.  

    ![Die Registerkarte "Veröffentlichen", Projekt-Designer](../vsto/media/vsto-publishtab.png "die Registerkarte \"Veröffentlichen\", Projekt-Designer")  

4. In der **Veröffentlichungsordners (ftp-Server oder Dateipfad)** Geben Sie den Pfad des Ordners, in denen Sie möchten, die **Projekt-Designer** die Projektmappendateien kopieren.  

    Folgende Pfadtypen sind möglich:  

   -   Ein lokaler Pfad (z. B. *C:\FolderName\FolderName*).  

   -   Ein Uniform Naming Convention (UNC)-Pfad zu einem Ordner in Ihrem Netzwerk (z. B.  *\\\ServerName\FolderName*).  

   -   Ein relativer Pfad (z. B. *Veröffentlichungsordner\\*, das ist der Ordner, in dem das Projekt standardmäßig veröffentlicht wird).  

5. In der **URL des Installationsordners** Geben Sie den vollqualifizierten Pfad des Speicherorts, in dem Endbenutzer die Projektmappe finden.  

    Wenn Sie die noch nicht kennen, geben Sie nicht alles in dieses Feld. Standardmäßig sucht ClickOnce in dem Ordner, von dem aus die Benutzer die Projektmappe installieren, nach Updates.  

6. Klicken Sie auf die Schaltfläche **Erforderliche Komponenten** .  

7. In der **Voraussetzungen** Dialogfeld sicher, dass die **Setupprogramm zur Installation erforderlicher Komponenten erstellen** das Kontrollkästchen aktiviert ist.  

8. In der **Auswählen der erforderlichen Komponenten installieren** wählen Sie die Kontrollkästchen für **Windows Installer 4.5** und das entsprechende .NET Framework-Paket.  

    Beispielsweise wenn Ihre Projektmappe als Zielversion verwendet die [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], wählen Sie die Kontrollkästchen für **Windows Installer 4.5** und **Microsoft .NET Framework 4.5 Full**.  

9. Wenn Ihre Lösung mit .NET Framework 4.5 ausgerichtet ist, wählen Sie auch die **Visual Studio 2010-Tools für Office-Laufzeit** Kontrollkästchen.  

    > [!NOTE]  
    >  Standardmäßig nicht das Kontrollkästchen angezeigt. Damit es angezeigt wird, müssen Sie ein Bootstrapperpaket erstellen. Finden Sie unter [erstellen Sie ein Bootstrapperpaket für ein Office 2013 VSTO-Add-in mit Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).  

10. Klicken Sie unter **Geben Sie den Installationsort für erforderliche Komponenten**, wählen Sie eine der Optionen, die angezeigt werden, und wählen Sie dann die **OK** Schaltfläche.  

     In der folgenden Tabelle sind die einzelnen Optionen beschrieben.  

    |Option|Beschreibung|  
    |------------|-----------------|  
    |**Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**|Der Benutzer wird aufgefordert, diese erforderlichen Komponenten vom Hersteller herunterzuladen und zu installieren.|  
    |**Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**|Die erforderliche Software wird mit der Projektmappe installiert. Wenn Sie diese Option auswählen, kopiert Visual Studio alle erforderlichen Pakete für Sie an den Veröffentlichungsort. Damit diese Option funktioniert, müssen sich die erforderlichen Pakete auf dem Entwicklungscomputer befinden.|  
    |**Erforderliche Komponenten von folgendem Speicherort herunterladen**|Visual Studio kopiert alle erforderlichen Pakete an den angegebenen Speicherort und installiert sie mit der Projektmappe.|  

     Finden Sie unter [erforderliche](/visualstudio/ide/reference/prerequisites-dialog-box).  

11. Wählen Sie die **Updates** Schaltfläche, die angeben, wie oft Sie jedes Endbenutzers VSTO-Add-in oder die Anpassung soll nach Updates suchen, und wählen Sie dann die **OK** Schaltfläche.  

    > [!NOTE]  
    >  Wenn Sie mithilfe einer CD oder eines Wechsellaufwerks bereitstellen möchten, wählen Sie die **nie nach Updates suchen** Optionsfeld aus.  

     Informationen dazu, wie Sie ein Update veröffentlichen, finden Sie unter [Veröffentlichen eines Updates](#Update).  

12. Wählen Sie die **Optionen** Schaltfläche, überprüfen Sie die Optionen in der **Optionen** Dialogfeld ein, und wählen Sie dann die **OK** Schaltfläche.  

13. Wählen Sie die **jetzt veröffentlichen** Schaltfläche.  

     Visual Studio fügt dem Veröffentlichungsordner die folgenden Ordner und Dateien hinzu, die Sie zuvor in dieser Prozedur angegeben haben.  

    - Die **Anwendungsdateien** Ordner.  

    - Das Setupprogramm.  

    - Ein Bereitstellungsmanifest, das auf das Bereitstellungsmanifest der neuesten Version verweist.  

      Die **Anwendungsdateien** Ordner enthält einen Unterordner für jede Version, die Sie veröffentlichen. Jeder versionsspezifische Unterordner enthält die folgenden Dateien.  

    - Ein Anwendungsmanifest.  

    - Ein Bereitstellungsmanifest.  

    - Anpassungsassemblys.  

      Die folgende Abbildung zeigt die Struktur des Veröffentlichungsordners für ein Outlook VSTO-Add-In.  

      ![Struktur des Veröffentlichungsordners](../vsto/media/publishfolderstructure.png "Struktur des Veröffentlichungsordners")  

    > [!NOTE]  
    >  ClickOnce hängt die *".deploy"* Erweiterung auf Assemblys, damit eine gesicherte Installation von Internet Information Services (IIS) die Dateien aufgrund einer unsicheren Dateierweiterung blockiert. Wenn der Benutzer die Projektmappe installiert, entfernt ClickOnce die *".deploy"* Erweiterung.  

14. Kopieren Sie die Projektmappendateien an den Installationspfad, den Sie zuvor in dieser Prozedur angegeben haben.  

##  <a name="Trust"></a> Entscheiden Sie, wie der Projektmappe Vertrauenswürdigkeit gewährt werden sollen.  
 Bevor eine Projektmappe auf Benutzercomputern ausgeführt werden kann, müssen Sie entweder Vertraulichkeit gewähren, oder Benutzer müssen auf eine vertrauenswürdige Eingabeaufforderung antworten, wenn Sie die Projektmappe installieren. Um der Projektmappe Vertraulichkeit zu gewähren, signieren Sie die Manifeste, indem Sie ein Zertifikat verwenden, das einen bekannten und vertrauenswürdigen Herausgeber identifiziert. Finden Sie unter [vertrauen Sie die Projektmappe, indem die Anwendungs- und Bereitstellungsmanifeste zu signieren](../vsto/granting-trust-to-office-solutions.md#Signing).  

 Wenn Sie eine Anpassung auf Dokumentebene bereitstellen, und legen Sie das Dokument in einen Ordner auf dem Computer des Benutzers oder das Dokument auf einer SharePoint-Website verfügbar machen möchten, stellen Sie sicher, dass Office den Speicherort des Dokuments vertraut. Finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  

##  <a name="Helping"></a> Unterstützen von Benutzern, die die Lösung installieren  
 Benutzer können die Projektmappe installieren, indem sie das Setupprogramm ausführen oder das Bereitstellungsmanifest öffnen; im Falle einer Anpassung auf Dokumentebene kann auch das Dokument direkt geöffnet werden. Als empfohlene Vorgehensweise sollten Benutzer die Projektmappe mithilfe des Setupprogramms installieren. Die beiden anderen Ansätze nicht stellen Sie sicher, dass die erforderliche Software installiert ist. Wenn Benutzer das Dokument vom Installationspfad öffnen möchten, müssen sie ihn der Liste vertrauenswürdiger Speicherorte im Sicherheitscenter der Office-Anwendung hinzufügen.  

### <a name="opening-the-document-of-a-document-level-customization"></a>Öffnen des Dokuments einer Anpassung auf Dokumentebene  
 Benutzer können das Dokument einer Anpassung auf Dokumentebene direkt vom Installationspfad öffnen, oder indem Sie das Dokument auf den lokalen Computer kopieren und dann die Kopie öffnen.  

 Empfohlen wird, dass Benutzer eine Kopie des Dokuments auf ihrem Computer öffnen, damit nicht mehrere Benutzer gleichzeitig versuchen, die gleiche Kopie zu öffnen. Um diese Methode zu erzwingen, können Sie das Setupprogramm so konfigurieren, dass das Dokument auf die Benutzercomputer kopiert wird. Finden Sie unter [Kopieren des Dokuments einer Projektmappe auf der Endbenutzer Computer (nur Anpassungen auf Dokumentebene)](#Put).  

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installieren Sie die Projektmappe durch Öffnen des Bereitstellungsmanifests von einer IIS-website  
 Benutzer können eine Office-Projektmappe installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Eine gesicherte Installation von Internet Information Services (IIS) blockiert jedoch Dateien, die die *".VSTO"* Erweiterung. Der MIME-Typ muss in IIS definiert werden, bevor Sie Office-Projektmappen mithilfe von IIS bereitstellen können.  

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>So fügen Sie den .vsto-MIME-Typ zu IIS 6.0 hinzu  

1.  Wählen Sie auf dem Server, auf dem IIS 6.0 ausgeführt wird, **starten** > **Programme** > **Verwaltung**  >   **Internetinformationsdienste (IIS) Manager**. 

2.  Wählen Sie den Namen des Computers die **Websites** Ordner oder die Website, die Sie konfigurieren.  

3.  Wählen Sie auf der Menüleiste **Aktion** > **Eigenschaften**.  

4.  Auf der **HTTP-Header** Registerkarte die **MIME-Typen** Schaltfläche.  

5.  In der **MIME-Typen** Fenster, wählen Sie die **neu** Schaltfläche.  

6.  In der **MIME-Typ** Fenster eingeben **".VSTO"** als Erweiterung und geben Sie **Application/X-ms-Vsto** als MIME-Geben Sie an, und klicken Sie dann die neuen Einstellungen anzuwenden.  

    > [!NOTE]  
    >  Damit die Änderungen wirksam werden, müssen Sie den WWW-Publishingdienst neu starten oder abwarten, bis der Arbeitsprozess wiederverwendet wird. Sie müssen die Datenträgercache des Browsers leeren und anschließend versuchen, öffnen die *".VSTO"* -Datei erneut.  

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>So fügen Sie den .vsto-MIME-Typ zu IIS 7,0 hinzu  

1.  Wählen Sie auf dem Server, auf denen IIS 7.0 ausgeführt wird, **starten** > **Programme** > **Zubehör**.  

2.  Öffnen Sie das Kontextmenü für **Eingabeaufforderung**, und wählen Sie dann **als Administrator ausführen.**  

3.  In der **öffnen** Feld, geben Sie den folgenden Pfad aus, und wählen Sie dann die **OK** Schaltfläche.  

    ```cmd
    %windir%\system32\inetsrv   
    ```  

4.  Geben Sie den folgenden Befehl ein, und wenden Sie dann die neuen Einstellungen an.  

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  

    > [!NOTE]  
    >  Damit die Änderungen wirksam werden, müssen Sie den WWW-Publishingdienst neu starten oder abwarten, bis der Arbeitsprozess wiederverwendet wird. Sie müssen die Datenträgercache des Browsers leeren und anschließend versuchen, öffnen die *".VSTO"* -Datei erneut.  

##  <a name="Put"></a> Kopieren des Dokuments einer Projektmappe auf der Endbenutzer Computer (nur Anpassungen auf Dokumentebene)  
 Sie können das Dokument der Projektmappe auf dem Computer des Endbenutzers kopieren, indem Sie eine Aktion nach der Bereitstellung zu erstellen. Der Benutzer nicht auf diese Weise manuell kopieren Sie das Dokument vom Installationspfad auf ihren Computer nach der Installation Ihrer Lösung. Sie müssen, erstellen Sie eine Klasse, die die Aktion nach der Bereitstellung definiert, erstellen und veröffentlichen Sie die Projektmappe, das Anwendungsmanifest ändern und die Anwendung und das Bereitstellungsmanifest erneut signieren.  

 Die folgenden Verfahren wird davon ausgegangen, dass der Name Ihres Projekts **ExcelWorkbook** und dass Sie die Projektmappe veröffentlichen der **C:\publish** Verzeichnis auf Ihrem Computer.  

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Erstellen einer Klasse, in der die Aktion nach der Bereitstellung definiert wird  

1. Wählen Sie auf der Menüleiste **Datei** > **hinzufügen** > **neues Projekt**.  

2. In der **neues Projekt hinzufügen** Dialogfeld die **installierte Vorlagen** Bereich, wählen Sie die **Windows** Ordner.  

3. In der **Vorlagen** Bereich, wählen Sie die **Klassenbibliothek** Vorlage.  

4. In der **Namen** Feld **FileCopyPDA**, und wählen Sie dann die **OK** Schaltfläche.  

5. In **Projektmappen-Explorer**, wählen Sie die **FileCopyPDA** Projekt.  

6. Wählen Sie in der Menüleiste die Optionen **Projekt** > **Verweis hinzufügen** aus.  

7. Auf der **.NET** Registerkarte, fügen Sie Verweise auf `Microsoft.VisualStudio.Tools.Applications.Runtime` und `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.  

8. Benennen Sie die Klasse in `FileCopyPDA` um, und ersetzen Sie den Inhalt der Datei durch den Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  

   - Kopieren des Dokuments auf den Desktop des Benutzers.  

   - Ändert die _AssemblyLocation-Eigenschaft von einem relativen Pfad in einen vollqualifizierten Pfad für das Bereitstellungsmanifest.  

   - Löschen der Datei, wenn der Benutzer die Projektmappe deinstalliert.  

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  

### <a name="build-and-publish-the-solution"></a>Erstellen und Veröffentlichen der Projektmappe  

1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **FileCopyPDA** Projekt, und wählen Sie dann **erstellen**.  

2.  Öffnen Sie das Kontextmenü für die **ExcelWorkbook** Projekt, und wählen Sie dann **erstellen**.  

3.  Öffnen Sie das Kontextmenü für die **ExcelWorkbook** Projekt, und wählen Sie dann **Verweis hinzufügen**.  

4.  In der **Verweis hinzufügen** Dialogfeld auf die **Projekte** Registerkarte **FileCopyPDA**, und wählen Sie dann die **OK** Schaltfläche.  

5.  In **Projektmappen-Explorer**, wählen Sie die **ExcelWorkbook** Projekt.  

6.  Wählen Sie auf der Menüleiste **Projekt** > **neuer Ordner**.  

7.  Geben Sie **Daten**, und wählen Sie dann die **EINGABETASTE** Schlüssel.  

8.  In **Projektmappen-Explorer**, wählen Sie die **Daten** Ordner.  

9. Wählen Sie auf der Menüleiste **Projekt** > **vorhandenes Element hinzufügen**.  

10. In der **vorhandenes Element hinzufügen** wechseln in das Ausgabeverzeichnis für die Sie im Dialogfeld die **ExcelWorkbook** Projekt, wählen Sie die **ExcelWorkbook.xlsx** Datei, und wählen Sie dann die  **Hinzufügen** Schaltfläche.  

11. In **Projektmappen-Explorer** wählen Sie die **ExcelWorkbook.xlsx** Datei.  

12. In der **Eigenschaften** Ändern der **Buildvorgang** Eigenschaft **Content** und **in Ausgabeverzeichnis kopieren** Eigenschaft  **Kopieren, wenn neuer**.  

     Wenn Sie diese Schritte abgeschlossen haben, wird Ihr Projekt in der folgende Abbildung ähneln.  

     ![Projektstruktur, der die Aktion nach der Bereitstellung. ](../vsto/media/vsto-postdeployment.png "Projektstruktur für die Aktion nach der Bereitstellung.")  

13. Veröffentlichen der **ExcelWorkbook** Projekt.  

### <a name="modify-the-application-manifest"></a>Ändern des Anwendungsmanifests  

1.  Öffnen der **c:\publish** Verzeichnis mit **Datei-Explorer**.  

2.  Öffnen Sie die **Anwendungsdateien** Ordner, und öffnen Sie den Ordner aus, die die letzte veröffentlichte Version der Projektmappe.  

3.  Öffnen der **ExcelWorkbook.dll.manifest** -Datei in einem Text-Editor wie Editor.  

4.  Fügen Sie nach dem `</vstav3:update>`-Element den folgenden Code ein. Für das Klassenattribut des der `<vstav3:entryPoint>` -Element, verwenden Sie die folgende Syntax: *NamespaceName.ClassName*. Im folgenden Beispiel sind der Namespace und die Klassennamen gleich, sodass der Name des resultierenden Einstiegspunkts `FileCopyPDA.FileCopyPDA` lautet.  

    ```xml
    <vstav3:postActions>  
      <vstav3:postAction>  
        <vstav3:entryPoint  
          class="FileCopyPDA.FileCopyPDA">  
          <assemblyIdentity  
            name="FileCopyPDA"  
            version="1.0.0.0"  
            language="neutral"  
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:postActionData>  
        </vstav3:postActionData>  
      </vstav3:postAction>  
    </vstav3:postActions>  
    ```  

### <a name="re-sign-the-application-and-deployment-manifests"></a>Erneutes Signieren der Anwendungs- und Bereitstellungsmanifeste  

1.  In der **%USERPROFILE%\Documents\Visual Studio 2013\projects\excelarbeitsmappe\excelarbeitsmappe** -Ordner, kopieren die **ExcelWorkbook_TemporaryKey.pfx** Zertifikatdatei, und fügen Sie ihn in das  *Veröffentlichungsordner* **\Application Files\ExcelWorkbook**\__Zuletztveröffentlichteversion_ Ordner.

2.  Öffnen Sie die Visual Studio-Eingabeaufforderung, und wechseln Sie dann die **c:\publish\Application Files\ExcelWorkbook**\__Zuletztveröffentlichteversion_ Ordner (z. B. **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  

3.  Signieren Sie das geänderte Anwendungsmanifest, indem Sie den folgenden Befehl ausführen:  

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  

     Die Meldung "ExcelWorkbook.dll.manifest erfolgreich signiert" wird angezeigt.  

4.  Ändern Sie in der **c:\publish** Ordner, und klicken Sie dann Update aus, und melden Sie die Bereitstellung manifest, indem Sie den folgenden Befehl ausführen:  

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  

    > [!NOTE]  
    >  Ersetzen Sie im vorherigen Beispiel "mostrecentversionnumber" durch die Versionsnummer der zuletzt veröffentlichten Version der Projektmappe (z. B. **1_0_0_4**).  

     Die Meldung „ExcelWorkbook.vsto erfolgreich signiert“ wird angezeigt.  

5.  Kopieren der *ExcelWorkbook.vsto* -Datei in die **c:\publish\Application Files\ExcelWorkbook**\__"mostrecentversionnumber"_ Verzeichnis.  

##  <a name="SharePoint"></a> Kopieren des Dokuments einer Projektmappe auf einem Server mit SharePoint (nur Anpassungen auf Dokumentebene)  
 Sie können die Anpassung auf Dokumentebene für Endbenutzer mithilfe von SharePoint veröffentlichen. Wenn Benutzer die SharePoint-Site aufrufen und das Dokument öffnen, installiert die Laufzeit automatisch die Projektmappe aus dem freigegebenen Netzwerkordner auf den lokalen Computer des Benutzers. Nachdem die Projektmappe lokal installiert wurde, funktioniert die Anpassung sogar dann, wenn das Dokument an eine andere Stelle kopiert wird, z. B. auf den Desktop.  

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>So kopieren Sie das Dokument auf einen Server, auf dem SharePoint ausgeführt wird  

1.  Fügen Sie das Projektmappendokument einer Dokumentbibliothek auf einer SharePoint-Site hinzu.  

2.  Führen Sie die Schritte für eines der folgenden Verfahren aus:  

    -   Fügen Sie mit dem Office-Konfigurationstool den Server, auf dem SharePoint ausgeführt wird, auf allen Benutzercomputern dem Sicherheitscenter in Word oder Excel hinzu.  

         Finden Sie unter [Sicherheitsrichtlinien und Einstellungen in Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  

    -   Stellen Sie sicher, dass jeder Benutzer die folgenden Schritte ausführt.  

        1.  Wählen Sie auf dem lokalen Computer, und Öffnen von Word oder Excel die **Datei** Registerkarte, und wählen Sie dann die **Optionen** Schaltfläche.  

        2.  In der **Trust Center** Dialogfeld auf die **vertrauenswürdige Speicherorte** Schaltfläche.  

        3.  Wählen Sie die **vertrauenswürdige Speicherorte in meinem Netzwerk (nicht empfohlen) zulassen** aus, und wählen Sie dann die **neuen Speicherort hinzufügen** Schaltfläche.  

        4.  In der **Pfad** Geben Sie die URL der SharePoint-Dokumentbibliothek, die das Dokument enthält, die Sie hochgeladen haben (z. B. *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  

             Fügen Sie den Namen der standardmäßigen Webseite, z. B. nicht *"default.aspx"* oder *AllItems.aspx*.  

        5.  Wählen Sie die **Unterordner dieses Speicherorts sind ebenfalls vertrauenswürdig** aus, und wählen Sie dann die **OK** Schaltfläche.  

             Wenn Benutzer das Dokument von der SharePoint-Site öffnen, wird das Dokument geöffnet, und die Anpassung wird installiert. Benutzer können das Dokument auf den Desktop kopieren. Die Anpassung wird nach wie vor ausgeführt, da Eigenschaften im Dokument auf den Netzwerkspeicherort des Dokuments verweisen.  

##  <a name="Custom"></a> Erstellen eines benutzerdefinierten Installationsprogramms  
 Sie können ein benutzerdefiniertes Installationsprogramm erstellen, für die Office-Projektmappe, anstatt das Setup-Programm, das für Sie erstellt wird, wenn Sie die Projektmappe veröffentlichen. Beispielsweise können Sie die Installation mit einem Anmeldeskript starten oder mit einer Batchdatei die Projektmappe ohne Benutzerinteraktion installieren. Diese Szenarios funktionieren am besten, wenn die erforderlichen Komponenten bereits auf den Endbenutzercomputern installiert sind.  

 Rufen Sie im Rahmen des benutzerdefinierten Installationsprozesses das Installationstool für Office-Projektmappen (*VSTOInstaller.exe*), das standardmäßig an folgendem Speicherort installiert wird:  

 *%CommonProgramFiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*  

 Wenn Sie nicht das Tool an diesem Speicherort ist, können Sie die **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** oder **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4 \InstallerPath** Registrierungsschlüssel, den Pfad zu diesem Tool finden.  

 Sie können die folgenden Parameter in *VSTOinstaller.exe*.  


| Parameter | Definition |
|------------------| - |
| /Install oder /I | Installation der Projektmappe. Dieser Option muss der Pfad eines Bereitstellungsmanifests folgen. Sie können einen Pfad auf dem lokalen Computer angeben, eine Universal Naming Convention (UNC)-Dateifreigabe. Sie können einen lokalen Pfad angeben (*C:\FolderName\PublishFolder*), einen relativen Pfad (*veröffentlichen\\*), oder einen vollqualifizierten Speicherort (*\\\ServerName\ Ordnername* oder http://<em>ServerName/Ordnername</em>). |
| /Uninstall oder /U | Deinstallation der Projektmappe. Dieser Option muss der Pfad eines Bereitstellungsmanifests folgen. Sie können einen Pfad auf dem lokalen Computer, eine UNC-Dateifreigabe, angeben. Sie können einen lokalen Pfad angeben (*c:\FolderName\PublishFolder*), einen relativen Pfad (*veröffentlichen\\*), oder einen vollqualifizierten Speicherort (*\\\ServerName\ Ordnername* oder http://<em>ServerName/Ordnername</em>). |
| /Silent oder /S | Installation bzw. Deinstallation, ohne dass der Benutzer zu einer Eingabe aufgefordert wird oder Meldungen angezeigt werden. Wenn eine vertrauenswürdige Eingabeaufforderung erforderlich ist, wird die Anpassung ist nicht installiert oder aktualisiert. |
| /Help oder /? | Anzeigen der Hilfeinformationen. |

 Beim Ausführen von *VSTOinstaller.exe*, wird möglicherweise die folgenden Fehlercodes angezeigt.  

|Fehlercode|Definition|  
|----------------|----------------|  
|0|Die Projektmappe wurde erfolgreich installiert oder deinstalliert, oder die VSTOInstaller-Hilfe wurde angezeigt.|  
|-100|Eine oder mehrere Befehlszeilenoptionen sind nicht gültig oder wurden mehrmals festgelegt. Weitere Informationen geben Sie "Vstoinstaller /?" oder finden Sie unter [erstellen ein benutzerdefiniertes Installers für eine ClickOnce-Office-Projektmappe](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Eine oder mehrere Befehlszeilenoptionen sind nicht gültig. Weitere Informationen erhalten Sie, indem Sie „vstoinstaller/?“ eingeben.|  
|-200|Der Bereitstellungsmanifest-URI ist ungültig. Weitere Informationen erhalten Sie, indem Sie „vstoinstaller/?“ eingeben.|  
|-201|Die Projektmappe konnte nicht installiert werden, da das Bereitstellungsmanifest ungültig ist. Finden Sie unter [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|Die Projektmappe konnte nicht installiert werden, da Visual Studio-Tools für Office-Abschnitt im Anwendungsmanifest ungültig ist. Finden Sie unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).|  
|-203|Die Projektmappe konnte nicht installiert werden, da ein Downloadfehler aufgetreten ist. Überprüfen Sie den URI bzw. den Netzspeicherort des Bereitstellungsmanifests, und versuchen Sie es erneut.|  
|-300|Die Projektmappe konnte nicht installiert werden, da eine Sicherheitsausnahme aufgetreten ist. Finden Sie unter [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md).|  
|-400|Die Projektmappe konnte nicht installiert werden.|  
|-401|Die Projektmappe konnte nicht deinstalliert werden.|  
|-500|Der Vorgang wurde abgebrochen, da die Projektmappe nicht installiert oder deinstalliert oder das Bereitstellungsmanifest nicht heruntergeladen werden konnte.|  

##  <a name="Update"></a> Veröffentlichen eines Updates  
 Um eine Lösung zu aktualisieren, Sie erneut zu veröffentlichen mithilfe der **Projekt-Designer** oder **Veröffentlichungs-Assistenten**, und kopieren Sie dann die aktualisierte Projektmappe an den Installationsort. Wenn Sie die Dateien an den Installationsort kopieren, müssen Sie die älteren Dateien überschreiben.  

 Das nächste Mal, das die Lösung überprüft ein Update, es findet und die neue Version wird automatisch geladen.  

##  <a name="Location"></a> Ändern des Installationspfads einer Projektmappe  
 Sie können den Installationspfad hinzufügen oder ändern, nachdem eine Projektmappe veröffentlicht wurde. Eine Änderung des Installationspfads kann aus einem oder mehreren der folgenden Gründe erforderlich werden:  

- Das Setupprogramm wurde kompiliert, bevor der Installationspfad bekannt war.  

- Die Projektmappendateien wurden an einen anderen Speicherort kopiert.  

- Der Server, auf dem die Installationsdateien gehostet werden, hat einen neuen Namen oder einen neuen Speicherort.  

  Um den Installationspfad einer Projektmappe zu ändern, müssen Sie das Setupprogramm aktualisieren, das dann von den Benutzern ausgeführt werden muss. Bei Anpassungen auf Dokumentebene müssen Benutzer außerdem eine Eigenschaft in dem Dokument aktualisieren, das auf den neuen Speicherort verweist.  

> [!NOTE]  
>  Wenn Sie keine Benutzer dazu auffordern, ihre Dokumenteigenschaften zu aktualisieren möchten, lassen Sie die Benutzer das aktualisierte Dokument vom Installationspfad zu erhalten.  

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>So ändern Sie den Installationspfad im Setupprogramm  

1. Öffnen einer **Eingabeaufforderung** Fenster, und klicken Sie dann wechseln in den Installationsordner.  

2. Führen Sie das Setupprogramm aus, und geben Sie den `/url`-Parameter an, der den neuen Installationspfad als Zeichenfolge entgegennimmt.  

    Das folgende Beispiel zeigt, wie der Installationspfad auf einen Speicherort auf der Fabrikam-Website geändert wird; Sie können diese URL durch den gewünschten Pfad ersetzen:  

   ```cmd  
   setup.exe /url="http://www.fabrikam.com/newlocation"  
   ```  

   > [!NOTE]  
   >  Wenn eine Meldung angezeigt wird, dass die Signatur der ausführbaren Datei ungültig gemacht wird, ist das Zertifikat, das zum Signieren der Projektmappe verwendet wurde, nicht mehr gültig, und der Herausgeber ist unbekannt. In diesem Fall müssen Benutzer bestätigen, dass die Quelle der Projektmappe vertrauenswürdig ist, bevor sie sie installieren können.  

   > [!NOTE]  
   >  Um den aktuellen Wert der URL anzuzeigen, führen Sie `setup.exe /url` aus.  

   Bei Anpassungen auf Dokumentebene müssen Benutzer das Dokument öffnen und aktualisieren Sie dann die _AssemblyLocation-Eigenschaft. Die folgenden Schritte beschreiben, wie Benutzer diese Aufgabe ausführen können.  

#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>So aktualisieren Sie die _AssemblyLocation-Eigenschaft in einem Dokument  

1.  Auf der **Datei** Registerkarte **Informationen**, die der folgenden Abbildung dargestellt.  

     ![Registerkarte "Info" in Excel](../vsto/media/vsto-infotab.png "Registerkarte \"Info\" in Excel")  

2.  In der **Eigenschaften** wählen **erweiterte Eigenschaften**, die der folgenden Abbildung dargestellt.  

     ![Erweiterte Eigenschaften in Excel. ](../vsto/media/vsto-advanceddocumentproperties.png "Erweiterte Eigenschaften in Excel.")  

3.  Auf der **benutzerdefinierte** Registerkarte die **Eigenschaften** wählen _AssemblyLocation, wie die folgende Abbildung zeigt.  

     ![Die AssemblyLocation-Eigenschaft. ](../vsto/media/vsto-assemblylocationproperty.png "Die AssemblyLocation-Eigenschaft.")  

     Die **Wert** Feld enthält den Bezeichner für das Bereitstellungsmanifest.  

4.  Geben Sie vor dem Bezeichner den vollqualifizierten Pfad des Dokuments an, gefolgt von einem senkrechten Strich, im Format *Pfad*|*Bezeichner* (z. B. *File://ServerName/ Ordnername/Dateiname | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.  

     Weitere Informationen zum Formatieren dieses Bezeichners finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).  

5.  Wählen Sie die **OK** Schaltfläche, und speichern und schließen Sie das Dokument.  

6.  Führen Sie das Setupprogramm ohne den /url-Parameter aus, um die Projektmappe am angegebenen Speicherort zu installieren.  

##  <a name="Roll"></a> Zurücksetzen der Projektmappe auf eine frühere version  
 Wenn Sie eine Projektmappe zurücksetzen, stellen Sie die Benutzer wieder auf eine frühere Version der Projektmappe um.  

#### <a name="to-roll-back-a-solution"></a>So setzen Sie eine Projektmappe zurück  

1.  Öffnen Sie den Installationspfad der Projektmappe.  

2.  Veröffentlichungsordner der obersten Ebene, löschen Sie das Bereitstellungsmanifest (die *".VSTO"* Datei).  

3.  Suchen Sie nach dem Unterordner für die Version, auf die Sie die Datei zurücksetzen möchten.  

4.  Kopieren Sie das Bereitstellungsmanifest aus diesem Unterordner in den Veröffentlichungsordner der obersten Ebene.  

     Um beispielsweise eine Projektmappe zurücksetzen, die aufgerufen wird **OutlookAddIn1** von Version 1.0.0.1 auf Version 1.0.0.0, kopieren Sie die Datei **OutlookAddIn1.vsto** aus der **OutlookAddIn1_1_0_0_0** Ordner. Fügen Sie die Datei in der obersten Ebene veröffentlichen, Ordner und überschreiben Sie dabei das versionsspezifische Bereitstellungsmanifest für **OutlookAddIn1_1_0_0_1** das war bereits vorhanden.  

     Die folgende Abbildung zeigt die Struktur des Veröffentlichungsordners in diesem Beispiel.  

     ![Struktur des Veröffentlichungsordners](../vsto/media/publishfolderstructure.png "Struktur des Veröffentlichungsordners")  

     Wenn ein Benutzer das nächste Mal die Anwendung oder das benutzerdefinierte Dokument öffnet, wird die Änderung des Bereitstellungsmanifests erkannt. Die frühere Version der Office-Projektmappe wird vom ClickOnce-Cache ausgeführt.  

> [!NOTE]  
>  Lokale Daten werden für nur eine vorherige Version einer Projektmappe gespeichert. Wenn Sie zwei Versionen zurücksetzen, wird die lokale Daten nicht beibehalten. Weitere Informationen zu lokalen Daten finden Sie unter [Zugriff auf lokale und remote-Daten in ClickOnce-Anwendungen](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  

## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Veröffentlichen von Office-Projektmappen](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Gewusst wie: Veröffentlichen einer Office-Projektmappe mit ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Gewusst wie: Installieren einer ClickOnce-Office-Projektmappe](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)   
 [Gewusst wie: Veröffentlichen einer Office-Projektmappe auf Dokumentebene auf einem SharePoint Server mithilfe von ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Erstellen eines benutzerdefinierten Installers für eine ClickOnce-Office-Projektmappe](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)  


