---
title: 'Vorgehensweise: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af0a07abe1cbb380acde91067e3e6252d0cd8596
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830053"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Gewusst wie: veröffentlichen eine WPF-Anwendung mit aktivierten visuellen Stilen
Durch visuelle Stile kann die Darstellung von allgemeinen Steuerelementen auf Grundlage des vom Benutzer ausgewählten Designs geändert werden. Standardmäßig werden keine visuellen Stile für WPF-Anwendungen (Windows Presentation Foundation) aktiviert. Daher müssen Sie sie manuell aktivieren. Allerdings tritt bei der Veröffentlichung der Projektmappe ein Fehler auf, wenn visuelle Stile für eine WPF-Anwendung aktiviert sind. In diesem Thema wird beschrieben, wie dieser Fehler zu beheben ist und wie eine WPF-Anwendung mit aktivierten visuellen Stilen veröffentlicht werden kann. Weitere Informationen zu visuellen Stilen finden Sie unter [Übersicht über die visuelle Stile](/windows/desktop/Controls/visual-styles-overview). Weitere Informationen zur Fehlermeldung finden Sie unter [Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Um den Fehler zu beheben und die Projektmappe zu veröffentlichen, müssen Sie die folgenden Aufgaben ausführen:  
  
- [Veröffentlichen Sie die Projektmappe ohne aktivierte visuelle Stile](#publish-the-solution-without-visual-styles-enabled).  
  
- [Erstellen Sie eine Manifestdatei](#create-a-manifest-file).  
  
- [Fügen Sie der Manifestdatei in die ausführbare Datei der veröffentlichten Projektmappe](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).  
  
- [Die Anwendungs- und Bereitstellungsmanifeste zu signieren](#sign-the-application-and-deployment-manifests).  
  
  Anschließend können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem Endbenutzer die Anwendung installieren sollen.  
  
##  <a name="publish-the-solution-without-visual-styles-enabled"></a>So veröffentlichen Sie die Projektmappe ohne aktivierte visuelle Stile  
  
1.  Stellen Sie sicher, dass visuelle Stile für das Projekt nicht aktiviert sind. Überprüfen Sie zunächst die manifest-Datei des Projekts für die folgenden XML-Code. Wenn der XML-Code vorhanden ist, schließen Sie ihn in ein Kommentartag ein.  
  
     Visuelle Stile sind standardmäßig nicht aktiviert.  
  
    ```xml  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Die folgenden Prozeduren zeigen, wie die Manifestdatei geöffnet wird, die Ihrem Projekt zugeordnet ist.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>So öffnen Sie die Manifestdatei in einem Visual Basic-Projekt  
  
    1.  Wählen Sie auf der Menüleiste **Projekt**, *ProjectName* **Eigenschaften**, wobei *ProjectName* ist der Name des WPF-Projekts.  
  
         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.  
  
    2.  Auf der **Anwendung** Registerkarte **Windows-Anzeigeeinstellungen**.  
  
         Die Datei "app.manifest" wird geöffnet, der **Code-Editor**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>So öffnen Sie die Manifestdatei in einem C#-Projekt  
  
    1.  Wählen Sie auf der Menüleiste **Projekt**, *ProjectName* **Eigenschaften**, wobei *ProjectName* ist der Name des WPF-Projekts.  
  
         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.  
  
    2.  Auf der **Anwendung** Registerkarte, notieren Sie sich mit dem Namen, der im manifestfeld angezeigt wird. Dies ist der Name des Manifests, das dem Projekt zugeordnet ist.  
  
        > [!NOTE]
        >  Wenn **Manifest mit Standardeinstellungen einbetten** oder **Anwendung ohne Manifest erstellen** angezeigt im manifestfeld, visuelle Stile nicht aktiviert sind. Wenn der Name einer Manifestdatei im Manifestfeld angezeigt wird, wechseln Sie zum nächsten Schritt in diesem Verfahren.  
  
    3.  In **Projektmappen-Explorer**, wählen Sie **alle Dateien anzeigen**.  
  
         Mit dieser Schaltfläche werden alle Projektelemente angezeigt, einschließlich der ausgeschlossen und derjenigen, die normalerweise ausgeblendet werden. Die Manifestdatei erscheint als Projektelement.  
  
2.  Erstellen und veröffentlichen Sie die Projektmappe. Weitere Informationen zum Veröffentlichen der Projektmappe finden Sie unter [Vorgehensweise: veröffentlichen eine ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="create-a-manifest-file"></a>So erstellen Sie eine Manifestdatei  
  
1.  Fügen Sie folgendes XML in eine Editor-Datei ein.  
  
     Dieser XML-Code beschreibt die Assembly, die Steuerelemente enthält, die visuelle Stile unterstützen.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Klicken Sie im Editor, **Datei**, und klicken Sie dann auf **speichern**.  
  
3.  In der **speichern** Dialogfeld die **Dateityp** Dropdown-Liste **alle Dateien**.  
  
4.  In der **Dateiname** Feld, nennen Sie die Datei aus, und fügen Sie *". manifest"* bis zum Ende des Dateinamens. Zum Beispiel: *"Themes.manifest"*.  
  
5.  Wählen Sie die **Ordner durchsuchen** , wählen Sie einen Ordner, und klicken Sie dann auf **speichern**.  
  
    > [!NOTE]
    >  Die verbleibenden Verfahren wird davon ausgegangen, dass der Name dieser Datei *"Themes.manifest"* und, die die Datei wird gespeichert, um die *C:\temp* Verzeichnis auf Ihrem Computer.  
  
## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>So fügen Sie die Manifestdatei in die ausführbare Datei der veröffentlichten Projektmappe ein  
  
1. Öffnen der **Visual Studio-Eingabeaufforderung**.  
  
    Weitere Informationen zum Öffnen der **Visual Studio-Eingabeaufforderung**, finden Sie unter [eingabeaufforderungen](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
   > [!NOTE]
   >  In den verbleibenden Schritten werden die folgenden Annahmen über die Projektmappe gemacht:  
   > 
   > - Der Name der Lösung ist **"mywpfproject"**.  
   >   -   Die Projektmappe befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
   > 
   >   Die Lösung wird im folgenden Verzeichnis veröffentlicht: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
   >   -   Die neueste Version der veröffentlichten Anwendungsdateien befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
   > 
   >   Sie müssen die oben genannten Namen und Verzeichnisspeicherorte nicht verwenden. Die oben genannten Namen und Speicherorte dienen nur als Beispiele bei der Veranschaulichung der Schritte, die für die Veröffentlichung der Projektmappe erforderlich sind.  
  
2. Ändern Sie an der Eingabeaufforderung den Pfad zu dem Verzeichnis, das die neueste Version der veröffentlichten Anwendungsdateien enthält. Das folgende Beispiel veranschaulicht diesen Schritt.  
  
   ```cmd  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Manifestdatei in die ausführbare Datei der Anwendung einzubetten:  
  
   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
   ```  
  
## <a name="sign-the-application-and-deployment-manifests"></a>So signieren Sie die Anwendungs- und Bereitstellungsmanifeste  
  
1. Führen Sie an der Eingabeaufforderung den folgenden Befehl zum Entfernen der *".deploy"* Erweiterung aus der ausführbaren Datei im aktuellen Verzeichnis.  
  
   ```cmd  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  In diesem Beispiel wird davon ausgegangen, dass nur eine Datei hat die *".deploy"* Dateierweiterung. Stellen Sie sicher, dass Sie alle Dateien in diesem Verzeichnis umbenennen, die die *".deploy"* Dateierweiterung.  
  
2. Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Anwendungsmanifests ein:  
  
   ```cmd  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  In diesem Beispiel wird davon ausgegangen, dass Sie mit das Manifest signiert die *PFX* -Datei des Projekts. Wenn Sie das Manifest nicht signieren, können Sie weglassen der `-cf` Parameter, die in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat, das ein Kennwort erforderlich ist signieren, geben Sie die `-password` Option (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3. Führen Sie an der Eingabeaufforderung den folgenden Befehl zum Hinzufügen der *".deploy"* Erweiterung auf den Namen der Datei, die Sie in einem vorherigen Schritt dieses Verfahrens umbenannt.  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  In diesem Beispiel wird davon ausgegangen, dass nur eine Datei hatte eine *".deploy"* Dateierweiterung. Stellen Sie sicher, dass Sie alle Dateien in diesem Verzeichnis umbenennen, die bisher die *".deploy"* Dateinamenerweiterung.  
  
4. Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Verteilungsmanifests ein:  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  In diesem Beispiel wird davon ausgegangen, dass Sie mit das Manifest signiert die *PFX* -Datei des Projekts. Wenn Sie das Manifest nicht signieren, können Sie weglassen der `-cf` Parameter, die in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat, das ein Kennwort erforderlich ist signieren, geben Sie die `-password` auswählen, wie im folgenden Beispiel:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
   Nachdem Sie diese Schritte ausgeführt haben, können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem aus Endbenutzer die Anwendung installieren sollen. Wenn Sie beabsichtigen, die Projektmappe häufig zu aktualisieren, können Sie diese Befehle in ein Skript übernehmen und das Skript jedes Mal ausführen, wenn Sie eine neue Version veröffentlichen.  
  
## <a name="see-also"></a>Siehe auch

-[Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Übersicht über die visuelle Stile](/windows/desktop/Controls/visual-styles-overview)
- [Aktivieren von visuellen Stilen](/windows/desktop/Controls/cookbook-overview)
- [Eingabeaufforderungen](/dotnet/framework/tools/developer-command-prompt-for-vs)
