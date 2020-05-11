---
title: Bereitstellen einer Office-Lösung mithilfe von ClickOnce
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416561"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Bereitstellen einer Office-Lösung mithilfe von ClickOnce
  Wenn Sie ClickOnce verwenden, können Sie die Office-Projektmappe in weniger Schritten bereitstellen. Wenn Sie Updates veröffentlichen, erkennt die Projektmappe sie automatisch und installiert sie. Für ClickOnce ist es jedoch erforderlich, die Projektmappe für jeden Benutzer eines Computers separat zu installieren. Daher sollten Sie die Verwendung von Windows Installer (*.msi*) in Betracht ziehen, wenn mehr als ein Benutzer Ihre Lösung auf demselben Computer ausführen wird.

## <a name="in-this-topic"></a>In diesem Thema

- [Veröffentlichen der Projektmappe](#Publish)

- [Festlegen, wie der Projektmappe Vertrauenswürdigkeit gewährt werden soll](#Trust)

- [Hilfe für Benutzer bei der Installation der Projektmappe](#Helping)

- [Kopieren des Dokuments einer Projektmappe auf den Computer des Endbenutzers (nur Anpassungen auf Dokumentebene)](#Put)

- [Kopieren des Dokuments einer Projektmappe auf einen Server, auf dem SharePoint ausgeführt wird (nur Anpassungen auf Dokumentebene)](#SharePoint)

- [Erstellen eines benutzerdefinierten Installationsprogramms](#Custom)

- [Veröffentlichen eines Updates](#Update)

- [Ändern des Installationspfads einer Projektmappe](#Location)

- [Zurücksetzen der Projektmappe auf eine frühere Version](#Roll)

  Weitere Informationen zum Bereitstellen einer Office-Lösung durch Erstellen einer Windows Installer-Datei finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a>Veröffentlichen der Lösung
 Sie können Ihre Projektmappe mit dem **Veröffentlichungs-Assistenten** oder dem **Projekt-Designer**veröffentlichen. In diesem Verfahren verwenden Sie den **Projekt-Designer,** da er den vollständigen Satz von Veröffentlichungsoptionen bereitstellt. Weitere Informationen finden Sie unter [Veröffentlichen des Assistenten &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>So veröffentlichen Sie die Projektmappe

1. Wählen Sie im **Projektmappen-Explorer**den Knoten aus, der für Ihr Projekt benannt ist.

2. Wählen Sie in der Menüleiste **Project**, *ProjectName* **Properties**aus.

3. Wählen Sie im **Projekt-Designer**die Registerkarte **Veröffentlichen** aus, die in der folgenden Abbildung angezeigt wird.

    ![Registerkarte "Veröffentlichen" im Projekt-Designer](../vsto/media/vsto-publishtab.png "Registerkarte "Veröffentlichen" im Projekt-Designer")

4. Geben Sie im Feld **Speicherort des Veröffentlichungsordners (FTP-Server oder Dateipfad)** den Pfad des Ordners ein, in den der **Projekt-Designer** die Projektmappendateien kopieren soll.

    Folgende Pfadtypen sind möglich:

   - Ein lokaler Pfad (z. B. *C:'FolderName'FolderName )..*

   - Ein UNC-Pfad (Uniform Naming Convention) zu einem Ordner in Ihrem Netzwerk (z. B. * \\"ServerName" und "Ordnername ").*

   - Ein relativer Pfad (z. B. *PublishFolder\\*, d. h. der Ordner, in dem das Projekt standardmäßig veröffentlicht wird).

5. Geben Sie im Feld URL des **Installationsordners** den vollqualifizierten Pfad des Speicherorts ein, an dem Endbenutzer Ihre Lösung finden.

    Wenn Sie den Standort noch nicht kennen, geben Sie nichts in dieses Feld ein. Standardmäßig sucht ClickOnce in dem Ordner, von dem aus die Benutzer die Projektmappe installieren, nach Updates.

6. Klicken Sie auf die Schaltfläche **Erforderliche Komponenten** .

7. Stellen Sie im Dialogfeld **Voraussetzungen** sicher, dass das Kontrollkästchen **Setupprogramm erstellen zum Installieren von Erforderlichenkomponenten** aktiviert ist.

8. Aktivieren Sie in der Liste **Auswählen, welche Voraussetzungen installiert werden** sollen, die Kontrollkästchen für Windows Installer **4.5** und das entsprechende .NET Framework-Paket.

    Wenn Ihre Lösung beispielsweise [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]auf die abzielt, aktivieren Sie die Kontrollkästchen für **Windows Installer 4.5** und **Microsoft .NET Framework 4.5 Full**.

9. Wenn Ihre Lösung auf .NET Framework 4.5 abzielt, aktivieren Sie auch das Kontrollkästchen **Visual Studio 2010 Tools for Office Runtime.**

    > [!NOTE]
    > Standardmäßig wird dieses Kontrollkästchen nicht angezeigt. Damit es angezeigt wird, müssen Sie ein Bootstrapperpaket erstellen. Weitere Informationen finden Sie unter [Erstellen eines Bootstrapper-Pakets für ein Office 2013 VSTO-Add-In mit Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. Wählen Sie unter **Den Installationsort für Voraussetzungen**angeben eine der angezeigten Optionen aus, und wählen Sie dann die Schaltfläche **OK** aus.

     In der folgenden Tabelle sind die einzelnen Optionen beschrieben.

    |Option|Beschreibung|
    |------------|-----------------|
    |**Erforderliche Komponenten von der Website des Komponentenherstellers herunterladen**|Der Benutzer wird aufgefordert, diese erforderlichen Komponenten vom Hersteller herunterzuladen und zu installieren.|
    |**Erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**|Die erforderliche Software wird mit der Projektmappe installiert. Wenn Sie diese Option auswählen, kopiert Visual Studio alle erforderlichen Pakete für Sie an den Veröffentlichungsort. Damit diese Option funktioniert, müssen sich die erforderlichen Pakete auf dem Entwicklungscomputer befinden.|
    |**Erforderliche Komponenten von folgendem Speicherort herunterladen**|Visual Studio kopiert alle erforderlichen Pakete an den angegebenen Speicherort und installiert sie mit der Projektmappe.|

     Siehe [Dialogfeld Voraussetzungen](../ide/reference/prerequisites-dialog-box.md).

11. Wählen Sie die Schaltfläche **Updates** aus, geben Sie an, wie oft das VSTO-Add-In oder die Anpassung jedes Endbenutzers nach Updates suchen soll, und wählen Sie dann die **Schaltfläche OK** aus.

    > [!NOTE]
    > Wenn Sie mithilfe einer CD oder eines Wechsellaufwerks bereitstellen, wählen Sie die Schaltfläche **Nie nach Updates** suchen aus.

     Informationen zum Veröffentlichen eines Updates finden Sie unter [Veröffentlichen eines Updates](#Update).

12. Wählen Sie die Schaltfläche **Optionen** aus, überprüfen Sie die Optionen im Dialogfeld **Optionen,** und wählen Sie dann die Schaltfläche **OK** aus.

13. Wählen Sie die Schaltfläche **Jetzt veröffentlichen** aus.

     Visual Studio fügt dem Veröffentlichungsordner die folgenden Ordner und Dateien hinzu, die Sie zuvor in dieser Prozedur angegeben haben.

    - Der Ordner **Anwendungsdateien.**

    - Das Setupprogramm.

    - Ein Bereitstellungsmanifest, das auf das Bereitstellungsmanifest der neuesten Version verweist.

      Der Ordner **Anwendungsdateien** enthält einen Unterordner für jede Version, die Sie veröffentlichen. Jeder versionsspezifische Unterordner enthält die folgenden Dateien.

    - Ein Anwendungsmanifest.

    - Ein Bereitstellungsmanifest.

    - Anpassungsassemblys.

      Die folgende Abbildung zeigt die Struktur des Veröffentlichungsordners für ein Outlook VSTO-Add-In.

      ![Ordnerstruktur veröffentlichen](../vsto/media/publishfolderstructure.png "Struktur des Veröffentlichungsordners")

    > [!NOTE]
    > ClickOnce fügt die *Erweiterung .deploy* an Assemblys an, sodass eine gesicherte Installation von Internetinformationsdiensten (Internet Information Services, IIS) die Dateien aufgrund einer unsicheren Erweiterung nicht blockiert. Wenn der Benutzer die Lösung installiert, entfernt ClickOnce die *Erweiterung .deploy.*

14. Kopieren Sie die Projektmappendateien an den Installationspfad, den Sie zuvor in dieser Prozedur angegeben haben.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Entscheiden Sie, wie Sie der Lösung Vertrauen gewähren möchten
 Bevor eine Projektmappe auf Benutzercomputern ausgeführt werden kann, müssen Sie entweder Vertraulichkeit gewähren, oder Benutzer müssen auf eine vertrauenswürdige Eingabeaufforderung antworten, wenn Sie die Projektmappe installieren. Um der Projektmappe Vertraulichkeit zu gewähren, signieren Sie die Manifeste, indem Sie ein Zertifikat verwenden, das einen bekannten und vertrauenswürdigen Herausgeber identifiziert. Weitere Informationen [finden Sie unter Vertrauen in die Lösung, indem Sie die Anwendungs- und Bereitstellungsmanifeste signieren.](../vsto/granting-trust-to-office-solutions.md#Signing)

 Wenn Sie eine Anpassung auf Dokumentebene bereitstellen und das Dokument in einen Ordner auf dem Computer des Benutzers einfügen oder das Dokument auf einer SharePoint-Website verfügbar machen möchten, stellen Sie sicher, dass Office dem Speicherort des Dokuments vertraut. Weitere Informationen finden Sie unter [Gewähren von Vertrauensstellungen für Dokumente](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Helfen Sie Benutzern bei der Installation der Lösung
 Benutzer können die Lösung installieren, indem sie das Setupprogramm ausführen, das Bereitstellungsmanifest öffnen oder während der Anpassung auf Dokumentebene das Dokument direkt öffnen. Als empfohlene Vorgehensweise sollten Benutzer die Projektmappe mithilfe des Setupprogramms installieren. Die beiden anderen Ansätze stellen nicht sicher, dass die erforderliche Software installiert ist. Wenn Benutzer das Dokument vom Installationspfad öffnen möchten, müssen sie ihn der Liste vertrauenswürdiger Speicherorte im Sicherheitscenter der Office-Anwendung hinzufügen.

### <a name="opening-the-document-of-a-document-level-customization"></a>Öffnen des Dokuments einer Anpassung auf Dokumentebene
 Benutzer können das Dokument einer Anpassung auf Dokumentebene direkt vom Installationspfad öffnen, oder indem Sie das Dokument auf den lokalen Computer kopieren und dann die Kopie öffnen.

 Empfohlen wird, dass Benutzer eine Kopie des Dokuments auf ihrem Computer öffnen, damit nicht mehrere Benutzer gleichzeitig versuchen, die gleiche Kopie zu öffnen. Um diese Methode zu erzwingen, können Sie das Setupprogramm so konfigurieren, dass das Dokument auf die Benutzercomputer kopiert wird. Weitere Informationen finden Sie unter [Einfügen des Dokuments einer Lösung auf dem Computer des Endbenutzers (nur Anpassungen auf Dokumentebene).](#Put)

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Installieren der Lösung durch Öffnen des Bereitstellungsmanifests von einer IIS-Website aus
 Benutzer können eine Office-Projektmappe installieren, indem sie das Bereitstellungsmanifest aus dem Web öffnen. Eine gesicherte Installation von Internetinformationsdiensten (Internet Information Services, IIS) blockiert jedoch Dateien mit der *Erweiterung .vsto.* Der MIME-Typ muss in IIS definiert werden, bevor Sie Office-Projektmappen mithilfe von IIS bereitstellen können.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>So fügen Sie den .vsto-MIME-Typ zu IIS 6.0 hinzu

1. **Wählen** > Sie auf dem Server, auf dem IIS 6.0 ausgeführt wird,**Alle Programme** > **administrative Tools** >  **Internet Information Services (IIS) Manager**starten .

2. Wählen Sie den Computernamen, den **Ordner "Websites"** oder die Website aus, die Sie konfigurieren.

3. Wählen Sie in der Menüleiste > **Aktionseigenschaften**aus. **Action**

4. Wählen Sie auf der Registerkarte **HTTP-Header** die Schaltfläche **MIME-Typen** aus.

5. Wählen Sie im Fenster **MIME-Typen** die Schaltfläche **Neu** aus.

6. Geben Sie im Fenster **MIME-Typ** **.vsto** als Erweiterung ein, geben Sie **application/x-ms-vsto** als MIME-Typ ein, und wenden Sie dann die neuen Einstellungen an.

    > [!NOTE]
    > Damit die Änderungen wirksam werden, müssen Sie den WWW-Publishingdienst neu starten oder abwarten, bis der Arbeitsprozess wiederverwendet wird. Anschließend müssen Sie den Datenträgercache des Browsers leeren und dann erneut versuchen, die *.vsto-Datei* zu öffnen.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>So fügen Sie den .vsto-MIME-Typ zu IIS 7,0 hinzu

1. **Wählen** > Sie auf dem Server, auf dem IIS 7.0 ausgeführt wird,**Alle Programme** > **zubehör**starten aus.

2. Öffnen Sie das Kontextmenü für **Die Eingabeaufforderung**, und wählen Sie dann **Ausführen als Administrator aus.**

3. Geben Sie im Feld **Öffnen** den folgenden Pfad ein, und wählen Sie dann die Schaltfläche **OK** aus.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Geben Sie den folgenden Befehl ein, und wenden Sie dann die neuen Einstellungen an.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Damit die Änderungen wirksam werden, müssen Sie den WWW-Publishingdienst neu starten oder abwarten, bis der Arbeitsprozess wiederverwendet wird. Anschließend müssen Sie den Datenträgercache des Browsers leeren und dann erneut versuchen, die *.vsto-Datei* zu öffnen.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Legen Sie das Dokument einer Lösung auf dem Computer des Endbenutzers ab (nur Anpassungen auf Dokumentebene)
 Sie können das Dokument Ihrer Lösung auf den Computer des Endbenutzers kopieren, indem Sie eine Aktion nach der Bereitstellung erstellen. Auf diese Weise muss der Benutzer das Dokument nach der Installation der Lösung nicht manuell vom Installationsort auf seinen Computer kopieren. Sie müssen eine Klasse erstellen, die die Aktion nach der Bereitstellung definiert, die Lösung erstellt und veröffentlicht, das Anwendungsmanifest ändern und das Anwendungs- und Bereitstellungsmanifest erneut signieren.

 Bei den folgenden Verfahren wird davon ausgegangen, dass ihr Projektname **ExcelWorkbook** ist und dass Sie die Projektmappe in einem erstellten Ordner mit dem Namen **C:-Publish** auf Ihrem Computer veröffentlichen.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Erstellen einer Klasse, in der die Aktion nach der Bereitstellung definiert wird

1. Wählen Sie in der Menüleiste **Datei** > **hinzufügen** > **neues Projekt**aus.

2. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** im Bereich **Installierte Vorlagen** den **Windows-Ordner** aus.

3. Wählen Sie im Bereich **Vorlagen** die **Vorlage Klassenbibliothek** aus.

4. Geben Sie im Feld **Name** **FileCopyPDA**ein, und wählen Sie dann die Schaltfläche **OK** aus.

5. Wählen Sie im **Projektmappen-Explorer**das **FileCopyPDA-Projekt** aus.

6. Wählen Sie in der Menüleiste > **Projekt-Referenz hinzufügen**aus. **Project**

7. Fügen Sie auf der Registerkarte `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument` **.NET** Verweise zu und hinzu.

8. Benennen Sie die Klasse in `FileCopyPDA` um, und ersetzen Sie den Inhalt der Datei durch den Code. Mit diesem Code werden die folgenden Aufgaben durchgeführt:

   - Kopieren des Dokuments auf den Desktop des Benutzers.

   - Ändert die _AssemblyLocation-Eigenschaft von einem relativen Pfad in einen vollqualifizierten Pfad für das Bereitstellungsmanifest.

   - Löschen der Datei, wenn der Benutzer die Projektmappe deinstalliert.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Erstellen und Veröffentlichen der Projektmappe

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **FileCopyPDA-Projekt,** und wählen Sie dann **Build**aus.

2. Öffnen Sie das Kontextmenü für das **ExcelWorkbook-Projekt,** und wählen Sie dann **Build**aus.

3. Öffnen Sie das Kontextmenü für das **ExcelWorkbook-Projekt,** und wählen Sie dann **Referenz hinzufügen**aus.

4. Wählen Sie im Dialogfeld **Referenz hinzufügen** die Registerkarte **Projekte** aus, wählen Sie **FileCopyPDA**aus, und wählen Sie dann die Schaltfläche **OK** aus.

5. Wählen Sie im **Projektmappen-Explorer**das **ExcelWorkbook-Projekt** aus.

6. Wählen Sie in der Menüleiste **Project** > **New Folder**aus.

7. Geben Sie **Daten ein,** und wählen Sie dann **den** Enter-Schlüssel aus.

8. Wählen Sie im **Projektmappen-Explorer**den **Ordner Daten** aus.

9. Wählen Sie in der Menüleiste **Projekt** > **Vorhandenes Element hinzufügen**aus.

10. Navigieren Sie im Dialogfeld **Vorhandenes Element hinzufügen** zum Ausgabeverzeichnis für das **ExcelWorkbook-Projekt,** wählen Sie die Datei **ExcelWorkbook.xlsx** aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

11. Wählen Sie im **Projektmappen-Explorer** die Datei **ExcelWorkbook.xlsx** aus.

12. Ändern Sie im **Eigenschaftenfenster** die **Build Action-Eigenschaft** in **Content** und die Copy to **Output Directory-Eigenschaft** in **Kopieren, wenn neuer**.

     Wenn Sie diese Schritte abgeschlossen haben, ähnelt das Projekt der folgenden Abbildung.

     ![Projektstruktur für die Aktion nach der Bereitstellung.](../vsto/media/vsto-postdeployment.png "Projektstruktur für die Aktion nach der Bereitstellung.")

13. Veröffentlichen Sie das **ExcelWorkbook-Projekt.**

### <a name="modify-the-application-manifest"></a>Ändern des Anwendungsmanifests

1. Öffnen Sie das Projektmappenverzeichnis **c:-publish**mithilfe des **Datei-Explorers**.

2. Öffnen Sie den Ordner **Anwendungsdateien,** und öffnen Sie dann den Ordner, der der zuletzt veröffentlichten Version der Projektmappe entspricht.

3. Öffnen Sie die Datei **ExcelWorkbook.dll.manifest** in einem Texteditor wie Notepad.

4. Fügen Sie nach dem `</vstav3:update>`-Element den folgenden Code ein. Verwenden Sie für `<vstav3:entryPoint>` das Klassenattribut des Elements die folgende Syntax: *NamespaceName.ClassName*. Im folgenden Beispiel sind der Namespace und die Klassennamen gleich, sodass der Name des resultierenden Einstiegspunkts `FileCopyPDA.FileCopyPDA` lautet.

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

1. Kopieren Sie im Ordner **%USERPROFILE%-Documents-Visual Studio 2013-Projects-ExcelWorkbook-ExcelWorkbook** die Zertifikatsdatei **ExcelWorkbook_TemporaryKey.pfx,** und fügen Sie sie dann in den Ordner *"PublishFolder" (Anwendungsdateien,* **ExcelWorkbook**\__MostRecentPublishedVersion)_ ein.

2. Öffnen Sie die Eingabeaufforderung für den Befehl Visual Studio, und ändern Sie dann die Verzeichnisse in den Ordner **c:'publish'Application Files'ExcelWorkbook**\__MostRecentPublishedVersion''ExcelWorkbook_1_0_0_4._ **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**

3. Signieren Sie das geänderte Anwendungsmanifest, indem Sie den folgenden Befehl ausführen:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Die Meldung "ExcelWorkbook.dll.manifest erfolgreich signiert" wird angezeigt.

4. Wechseln Sie in den Ordner **c:-Veröffentlichung,** und aktualisieren und signieren Sie dann das Bereitstellungsmanifest, indem Sie den folgenden Befehl ausführen:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > Ersetzen Sie im vorherigen Beispiel MostRecentVersionNumber durch die Versionsnummer der zuletzt veröffentlichten Version Ihrer Lösung (z. B. **1_0_0_4**).

     Die Meldung "ExcelWorkbook.vsto erfolgreich signiert" wird angezeigt.

5. Kopieren Sie die *ExcelWorkbook.vsto-Datei* in das Verzeichnis **c:-publish-Application Files-ExcelWorkbook**\__MostRecentVersionNumber._

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Legen Sie das Dokument einer Lösung auf einem Server ab, auf dem SharePoint ausgeführt wird (nur Anpassungen auf Dokumentebene)
 Sie können die Anpassung auf Dokumentebene für Endbenutzer mithilfe von SharePoint veröffentlichen. Wenn Benutzer die SharePoint-Site aufrufen und das Dokument öffnen, installiert die Laufzeit automatisch die Projektmappe aus dem freigegebenen Netzwerkordner auf den lokalen Computer des Benutzers. Nachdem die Projektmappe lokal installiert wurde, funktioniert die Anpassung sogar dann, wenn das Dokument an eine andere Stelle kopiert wird, z. B. auf den Desktop.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>So kopieren Sie das Dokument auf einen Server, auf dem SharePoint ausgeführt wird

1. Fügen Sie das Projektmappendokument einer Dokumentbibliothek auf einer SharePoint-Site hinzu.

2. Führen Sie die Schritte für eines der folgenden Verfahren aus:

    - Fügen Sie mit dem Office-Konfigurationstool den Server, auf dem SharePoint ausgeführt wird, auf allen Benutzercomputern dem Sicherheitscenter in Word oder Excel hinzu.

         Weitere Informationen finden Sie unter [Sicherheitsrichtlinien und -einstellungen in Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Stellen Sie sicher, dass jeder Benutzer die folgenden Schritte ausführt.

        1. Öffnen Sie auf dem lokalen Computer Word oder Excel, wählen Sie die Registerkarte **Datei** aus, und wählen Sie dann die Schaltfläche **Optionen** aus.

        2. Wählen Sie im Dialogfeld **Vertrauenscenter** die Schaltfläche **Vertrauenswürdige Standorte** aus.

        3. Aktivieren Sie das Kontrollkästchen **Vertrauenswürdige Speicherorte in meinem Netzwerk zulassen (nicht empfohlen),** und wählen Sie dann die Schaltfläche **Neuer Standort hinzufügen** aus.

        4. Geben Sie im Feld **Pfad** die URL der SharePoint-Dokumentbibliothek ein, die *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*das hochgeladene Dokument enthält (z. B. ).

             Fügen Sie den Namen der Standardwebseite nicht hinzu, z. *B. default.aspx* oder *AllItems.aspx*.

        5. Aktivieren Sie das Kontrollkästchen **Unterordner dieses Speicherorts, die ebenfalls vertrauenswürdig sind,** und aktivieren Sie dann die Schaltfläche **OK.**

             Wenn Benutzer das Dokument von der SharePoint-Site öffnen, wird das Dokument geöffnet, und die Anpassung wird installiert. Benutzer können das Dokument auf den Desktop kopieren. Die Anpassung wird nach wie vor ausgeführt, da Eigenschaften im Dokument auf den Netzwerkspeicherort des Dokuments verweisen.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Erstellen eines benutzerdefinierten Installationsprogramms
 Sie können ein benutzerdefiniertes Installationsprogramm für Ihre Office-Lösung erstellen, anstatt das Setupprogramm zu verwenden, das beim Veröffentlichen der Projektmappe für Sie erstellt wurde. Sie können z. B. ein Anmeldeskript verwenden, um die Installation zu starten, oder Sie können eine Batchdatei verwenden, um die Lösung ohne Benutzerinteraktion zu installieren. Diese Szenarios funktionieren am besten, wenn die erforderlichen Komponenten bereits auf den Endbenutzercomputern installiert sind.

 Rufen Sie im Rahmen des benutzerdefinierten Installationsvorgangs das Installationstool für*Office-Lösungen ( VSTOInstaller.exe*) auf, das standardmäßig am folgenden Speicherort installiert ist:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Wenn sich das Tool nicht an diesem Speicherort befindet, können Sie den Registrierungsschlüssel **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VSTO-Laufzeit-Setup- und** **-HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432-Knoten-Microsoft-VSTO-Laufzeit-Setup- und -v4-InstallerPath-Registrierungsschlüssel** verwenden, um den Pfad zu diesem Tool zu finden.

 Sie können die folgenden Parameter mit *VSTOinstaller.exe*verwenden.

| Parameter | Definition |
|------------------| - |
| /Install oder /I | Installation der Projektmappe. Dieser Option muss der Pfad eines Bereitstellungsmanifests folgen. Sie können einen Pfad auf dem lokalen Computer angeben, eine Universal Naming Convention (UNC)-Dateifreigabe. Sie können einen lokalen Pfad angeben (*C:'FolderName'PublishFolder*), einen relativen Pfad ( Veröffentlichen ' (*\\Veröffentlichung*' (*\\'ServerName'FolderName'* oder http://<em>ServerName/FolderName</em>). |
| /Uninstall oder /U | Deinstallation der Projektmappe. Dieser Option muss der Pfad eines Bereitstellungsmanifests folgen. Sie können einen Pfad auf dem lokalen Computer, eine UNC-Dateifreigabe, angeben. Sie können einen lokalen Pfad angeben (*c:'FolderName'PublishFolder*), einen relativen Pfad ( Veröffentlichen ' (*\\Veröffentlichung*' (*\\'ServerName'FolderName'* oder http://<em>ServerName/FolderName</em>). |
| /Silent oder /S | Installation bzw. Deinstallation, ohne dass der Benutzer zu einer Eingabe aufgefordert wird oder Meldungen angezeigt werden. Wenn eine Vertrauensaufforderung erforderlich ist, wird die Anpassung nicht installiert oder aktualisiert. |
| /Help oder /? | Anzeigen der Hilfeinformationen. |

 Wenn Sie *VSTOinstaller.exe*ausführen, werden möglicherweise die folgenden Fehlercodes angezeigt.

|Fehlercode|Definition|
|----------------|----------------|
|0|Die Projektmappe wurde erfolgreich installiert oder deinstalliert, oder die VSTOInstaller-Hilfe wurde angezeigt.|
|-100|Mindestens eine Befehlszeilenoption ist ungültig oder wurde mehr als einmal festgelegt. Weitere Informationen finden Sie unter "vstoinstaller /?" oder finden Sie unter [Erstellen eines benutzerdefinierten Installationsprogramms für eine ClickOnce Office-Lösung](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Mindestens eine Befehlszeilenoption ist ungültig. Weitere Informationen erhalten Sie, indem Sie "vstoinstaller/?" eingeben.|
|-200|Der URI des Bereitstellungsmanifests ist ungültig. Weitere Informationen erhalten Sie, indem Sie "vstoinstaller/?" eingeben.|
|-201|Die Lösung konnte nicht installiert werden, da das Bereitstellungsmanifest ungültig ist. Weitere Informationen finden Sie unter [Bereitstellungsmanifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Die Lösung konnte nicht installiert werden, da der Abschnitt Visual Studio Tools für Office des Anwendungsmanifests ungültig ist. Weitere Informationen finden Sie unter [Anwendungsmanifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md).|
|-203|Die Lösung konnte nicht installiert werden, da ein Downloadfehler aufgetreten ist. Überprüfen Sie den URI bzw. den Netzspeicherort des Bereitstellungsmanifests, und versuchen Sie es erneut.|
|-300|Die Lösung konnte nicht installiert werden, da eine Sicherheitsausnahme aufgetreten ist. Siehe [Secure Office-Lösungen](../vsto/securing-office-solutions.md).|
|-400|Die Lösung konnte nicht installiert werden.|
|-401|Die Lösung konnte nicht deinstalliert werden.|
|-500|Der Vorgang wurde abgebrochen, da die Projektmappe nicht installiert oder deinstalliert oder das Bereitstellungsmanifest nicht heruntergeladen werden konnte.|

## <a name="publish-an-update"></a><a name="Update"></a>Veröffentlichen eines Updates
 Um eine Projektmappe zu aktualisieren, veröffentlichen Sie sie erneut mithilfe des **Projekt-Designers** oder des **Veröffentlichungs-Assistenten**, und kopieren dann die aktualisierte Projektmappe an den Installationsspeicherort. Wenn Sie die Dateien an den Installationsort kopieren, müssen Sie die älteren Dateien überschreiben.

 Wenn die Lösung das nächste Mal nach einem Update sucht, wird die neue Version automatisch gefunden und geladen.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Ändern des Installationsortes einer Lösung
 Sie können den Installationspfad hinzufügen oder ändern, nachdem eine Projektmappe veröffentlicht wurde. Eine Änderung des Installationspfads kann aus einem oder mehreren der folgenden Gründe erforderlich werden:

- Das Setupprogramm wurde kompiliert, bevor der Installationspfad bekannt war.

- Die Projektmappendateien wurden an einen anderen Speicherort kopiert.

- Der Server, auf dem die Installationsdateien gehostet werden, hat einen neuen Namen oder einen neuen Speicherort.

  Um den Installationspfad einer Projektmappe zu ändern, müssen Sie das Setupprogramm aktualisieren, das dann von den Benutzern ausgeführt werden muss. Bei Anpassungen auf Dokumentebene müssen Benutzer außerdem eine Eigenschaft in dem Dokument aktualisieren, das auf den neuen Speicherort verweist.

> [!NOTE]
> Wenn Sie Benutzer nicht bitten möchten, ihre Dokumenteigenschaften zu aktualisieren, können Sie Benutzer bitten, das aktualisierte Dokument vom Installationsort abzubekommen.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>So ändern Sie den Installationspfad im Setupprogramm

1. Öffnen Sie ein **Eingabeaufforderungsfenster,** und ändern Sie dann Verzeichnisse in den Installationsordner.

2. Führen Sie das Setupprogramm aus, und geben Sie den `/url`-Parameter an, der den neuen Installationspfad als Zeichenfolge entgegennimmt.

    Das folgende Beispiel zeigt, wie der Installationspfad auf einen Speicherort auf der Fabrikam-Website geändert wird; Sie können diese URL durch den gewünschten Pfad ersetzen:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Wenn eine Meldung angezeigt wird, dass die Signatur der ausführbaren Datei ungültig gemacht wird, ist das Zertifikat, das zum Signieren der Projektmappe verwendet wurde, nicht mehr gültig, und der Herausgeber ist unbekannt. In diesem Fall müssen Benutzer bestätigen, dass die Quelle der Projektmappe vertrauenswürdig ist, bevor sie sie installieren können.

   > [!NOTE]
   > Um den aktuellen Wert der URL anzuzeigen, führen Sie `setup.exe /url` aus.

   Bei Anpassungen auf Dokumentebene müssen Benutzer das Dokument öffnen und dann die _AssemblyLocation-Eigenschaft aktualisieren. Die folgenden Schritte beschreiben, wie Benutzer diese Aufgabe ausführen können.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>So aktualisieren Sie die _AssemblyLocation-Eigenschaft in einem Dokument

1. Wählen Sie auf der Registerkarte **Datei** **Info**aus, die in der folgenden Abbildung angezeigt wird.

     ![Registerkarte "Informationen" in Excel](../vsto/media/vsto-infotab.png "Registerkarte "Informationen" in Excel")

2. Wählen Sie in der Liste **Eigenschaften** **erweiterte Eigenschaften**aus, die in der folgenden Abbildung dargestellt wird.

     !["Erweiterte Eigenschaften" in Excel.](../vsto/media/vsto-advanceddocumentproperties.png ""Erweiterte Eigenschaften" in Excel.")

3. Wählen Sie auf der Registerkarte **Benutzerdefiniert** in **der** Eigenschaftenliste _AssemblyLocation aus, wie die folgende Abbildung zeigt.

     ![Die AssemblyLocation-Eigenschaft.](../vsto/media/vsto-assemblylocationproperty.png "Die AssemblyLocation-Eigenschaft.")

     Das Feld **Wert** enthält den Bereitstellungsmanifestbezeichner.

4. Geben Sie vor dem Bezeichner den vollqualifizierten Pfad des Dokuments und gefolgt von einem Balken im Format *Path*|*Identifier* (z. B. *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*ein.

     Weitere Informationen zum Formatieren dieses Bezeichners finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).

5. Wählen Sie die **Schaltfläche OK** aus, und speichern und schließen Sie das Dokument.

6. Führen Sie das Setupprogramm ohne den /url-Parameter aus, um die Projektmappe am angegebenen Speicherort zu installieren.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Zurücksetzen einer Lösung auf eine frühere Version
 Wenn Sie eine Projektmappe zurücksetzen, stellen Sie die Benutzer wieder auf eine frühere Version der Projektmappe um.

#### <a name="to-roll-back-a-solution"></a>So setzen Sie eine Projektmappe zurück

1. Öffnen Sie den Installationspfad der Projektmappe.

2. Löschen Sie im Veröffentlichungsordner der obersten Ebene das Bereitstellungsmanifest (die *.vsto-Datei).*

3. Suchen Sie nach dem Unterordner für die Version, auf die Sie die Datei zurücksetzen möchten.

4. Kopieren Sie das Bereitstellungsmanifest aus diesem Unterordner in den Veröffentlichungsordner der obersten Ebene.

     Um beispielsweise eine Lösung mit dem Namen **OutlookAddIn1** von Version 1.0.0.1 auf Version 1.0.0.0 zurückzufahren, kopieren Sie die Datei **OutlookAddIn1.vsto** aus dem **Ordner OutlookAddIn1_1_0_0_0.** Fügen Sie die Datei in den Veröffentlichungsordner der obersten Ebene ein, und überschreiben Sie das versionsspezifische Bereitstellungsmanifest für **OutlookAddIn1_1_0_0_1,** der bereits vorhanden war.

     Die folgende Abbildung zeigt die Struktur des Veröffentlichungsordners in diesem Beispiel.

     ![Ordnerstruktur veröffentlichen](../vsto/media/publishfolderstructure.png "Struktur des Veröffentlichungsordners")

     Wenn ein Benutzer das nächste Mal die Anwendung oder das benutzerdefinierte Dokument öffnet, wird die Änderung des Bereitstellungsmanifests erkannt. Die frühere Version der Office-Projektmappe wird vom ClickOnce-Cache ausgeführt.

> [!NOTE]
> Lokale Daten werden für nur eine vorherige Version einer Projektmappe gespeichert. Wenn Sie zwei Versionen zurücksetzen, werden lokale Daten nicht beibehalten. Weitere Informationen zu lokalen Daten finden Sie [unter Zugriff auf lokale und Remotedaten in ClickOnce-Anwendungen](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Weitere Informationen

- [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)
- [Veröffentlichen von Office-Lösungen](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Gewusst wie: Veröffentlichen einer Office-Lösung mithilfe von ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Gewusst wie: Installieren einer ClickOnce Office-Lösung](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Gewusst wie: Veröffentlichen einer Office-Lösung auf Dokumentebene auf einem SharePoint-Server mithilfe von ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Erstellen eines benutzerdefinierten Installationsprogramms für eine ClickOnce Office-Lösung](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)