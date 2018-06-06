---
title: 'Vorgehensweise: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen | Microsoft Docs'
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
ms.openlocfilehash: 0111226fdd3de300265f69930b7e9e56f90876c8
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816015"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Gewusst wie: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen
Durch visuelle Stile kann die Darstellung von allgemeinen Steuerelementen auf Grundlage des vom Benutzer ausgewählten Designs geändert werden. Standardmäßig werden keine visuellen Stile für WPF-Anwendungen (Windows Presentation Foundation) aktiviert. Daher müssen Sie sie manuell aktivieren. Allerdings tritt bei der Veröffentlichung der Projektmappe ein Fehler auf, wenn visuelle Stile für eine WPF-Anwendung aktiviert sind. In diesem Thema wird beschrieben, wie dieser Fehler zu beheben ist und wie eine WPF-Anwendung mit aktivierten visuellen Stilen veröffentlicht werden kann. Weitere Informationen zu visuellen Stilen finden Sie unter [visuelle Stile Übersicht](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Weitere Informationen zu der Fehlermeldung finden Sie unter [Problembehandlung bei bestimmten Fehlern in ClickOnce-Bereitstellungen](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Um den Fehler zu beheben und die Projektmappe zu veröffentlichen, müssen Sie die folgenden Aufgaben ausführen:  
  
-   [Veröffentlichen Sie die Projektmappe ohne aktivierte visuelle Stile](#BKMK_publishsolwovs).  
  
-   [Erstellen Sie eine Manifestdatei](#BKMK_CreateManifest).  
  
-   [Fügen Sie der Manifestdatei in die ausführbare Datei der veröffentlichten Projektmappe](#BKMK_embedmanifest).  
  
-   [Melden Sie sich die Anwendungs- und Bereitstellungsmanifeste](#BKMK_signappdeplyman).  
  
 Anschließend können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem Endbenutzer die Anwendung installieren sollen.  
  
##  <a name="BKMK_publishsolwovs"></a> Veröffentlichen Sie die Projektmappe ohne aktivierte visuelle Stile  
  
1.  Stellen Sie sicher, dass visuelle Stile für das Projekt nicht aktiviert sind. Überprüfen Sie zunächst die Manifestdatei des Projekts für die folgenden XML-Code. Wenn der XML-Code vorhanden ist, schließen Sie ihn in ein Kommentartag ein.  
  
     Visuelle Stile sind standardmäßig nicht aktiviert.  
  
    ```xml  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Die folgenden Prozeduren zeigen, wie die Manifestdatei geöffnet wird, die Ihrem Projekt zugeordnet ist.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>So öffnen Sie die Manifestdatei in einem Visual Basic-Projekt  
  
    1.  Wählen Sie in der Menüleiste **Projekt**, * Projektname ***Eigenschaften**, wobei *Projektname* ist der Name des WPF-Projekts.  
  
         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.  
  
    2.  Auf der **Anwendung** Registerkarte **Windows-Einstellungen anzeigen**.  
  
         Die Datei "app.manifest" wird geöffnet, der **Code-Editor**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>So öffnen Sie die Manifestdatei in einem C#-Projekt  
  
    1.  Wählen Sie in der Menüleiste **Projekt**, * Projektname ***Eigenschaften**, wobei *Projektname* ist der Name des WPF-Projekts.  
  
         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.  
  
    2.  Auf der **Anwendung** Registerkarte, notieren Sie sich den Namen, der im manifestfeld angezeigt wird. Dies ist der Name des Manifests, das dem Projekt zugeordnet ist.  
  
        > [!NOTE]
        >  Wenn **Manifest mit Standardeinstellungen einbetten** oder **Anwendung ohne Manifest erstellen** erscheinen im manifestfeld, visuelle Stile nicht aktiviert sind. Wenn der Name einer Manifestdatei im Manifestfeld angezeigt wird, wechseln Sie zum nächsten Schritt in diesem Verfahren.  
  
    3.  In **Projektmappen-Explorer**, wählen Sie **alle Dateien anzeigen** ().  
  
         Mit dieser Schaltfläche werden alle Projektelemente angezeigt, einschließlich der ausgeschlossen und derjenigen, die normalerweise ausgeblendet werden. Die Manifestdatei erscheint als Projektelement.  
  
2.  Erstellen und veröffentlichen Sie die Projektmappe. Weitere Informationen dazu, wie Sie die Projektmappe zu veröffentlichen, finden Sie unter [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a> Erstellen Sie eine Manifestdatei  
  
1.  Fügen Sie folgendes XML in eine Editor-Datei ein.  
  
     Dieser XML-Code beschreibt die Assembly, die Steuerelemente enthält, die visuelle Stile unterstützen.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  Klicken Sie in Notepad auf **Datei**, und klicken Sie dann auf **speichern unter**.  
  
3.  In der **speichern unter** Dialogfeld die **Dateityp** Dropdown-Liste **alle Dateien**.  
  
4.  In der **Dateiname** Feld, nennen Sie die Datei aus, und fügen **.manifest** bis zum Ende des Dateinamens. Zum Beispiel: **"Themes.manifest"**.  
  
5.  Wählen Sie die **Ordner durchsuchen** Schaltfläche, wählen Sie einen beliebigen Ordner, und klicken Sie dann auf **speichern**.  
  
    > [!NOTE]
    >  Die verbleibenden Verfahren wird davon ausgegangen, dass der Name dieser Datei **"Themes.manifest"** und die Datei in das Verzeichnis C:\temp auf Ihrem Computer gespeichert ist.  
  
##  <a name="BKMK_embedmanifest"></a> Fügen Sie der Manifestdatei in die ausführbare Datei der veröffentlichten Projektmappe  
  
1.  Öffnen der **Visual Studio-Eingabeaufforderung**.  
  
     Weitere Informationen zum Öffnen der **Visual Studio-Eingabeaufforderung**, finden Sie unter [Eingabeaufforderungen](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
    > [!NOTE]
    >  In den verbleibenden Schritten werden die folgenden Annahmen über die Projektmappe gemacht:  
    >   
    >  -   Der Name der Lösung ist **"mywpfproject"**.  
    > -   Die Projektmappe befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      Die Lösung wird veröffentlicht, auf das folgende Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   Die neueste Version der veröffentlichten Anwendungsdateien befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Sie müssen die oben genannten Namen und Verzeichnisspeicherorte nicht verwenden. Die oben genannten Namen und Speicherorte dienen nur als Beispiele bei der Veranschaulichung der Schritte, die für die Veröffentlichung der Projektmappe erforderlich sind.  
  
2.  Ändern Sie an der Eingabeaufforderung den Pfad zu dem Verzeichnis, das die neueste Version der veröffentlichten Anwendungsdateien enthält. Das folgende Beispiel veranschaulicht diesen Schritt.  
  
    ```  
cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Manifestdatei in die ausführbare Datei der Anwendung einzubetten:  
  
    ```
    mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a> Melden Sie sich die Anwendungs- und Bereitstellungsmanifeste  
  
1.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die `.deploy`-Erweiterung aus der ausführbaren Datei im aktuellen Verzeichnis zu entfernen:  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  In diesem Beispiel wird davon ausgegangen, dass nur eine Datei die Dateierweiterung `.deploy` aufweist. Stellen Sie sicher, dass Sie alle Dateien in diesem Verzeichnis umbenennen, die die Dateierweiterung `.deploy` aufweisen.  
  
2.  Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Anwendungsmanifests ein:  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  In diesem Beispiel wird davon ausgegangen, dass Sie das Manifest mit der `.pfx`-Datei des Projekts signieren. Wenn Sie das Manifest nicht anmelden, können Sie weglassen der `-cf` Parameter, die in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat, die ein Kennwort erforderlich ist signieren, geben Sie die `-password` Option (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3.  Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die `.deploy`-Erweiterung dem Namen der Datei hinzuzufügen, die Sie in einem vorherigen Schritt dieses Verfahrens umbenannt haben:  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  In diesem Beispiel wird davon ausgegangen, dass nur eine Datei die Dateierweiterung `.deploy` aufweist. Stellen Sie sicher, dass alle Dateien in diesem Verzeichnis umbenannt werden, die zuvor die Dateinamenerweiterung `.deploy` hatten.  
  
4.  Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Verteilungsmanifests ein:  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  In diesem Beispiel wird davon ausgegangen, dass Sie das Manifest mit der `.pfx`-Datei des Projekts signieren. Wenn Sie das Manifest nicht anmelden, können Sie weglassen der `-cf` Parameter, die in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat, die ein Kennwort erforderlich ist signieren, geben Sie die `-password` Option, wie in diesem Beispiel:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
 Nachdem Sie diese Schritte ausgeführt haben, können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem aus Endbenutzer die Anwendung installieren sollen. Wenn Sie beabsichtigen, die Projektmappe häufig zu aktualisieren, können Sie diese Befehle in ein Skript übernehmen und das Skript jedes Mal ausführen, wenn Sie eine neue Version veröffentlichen.  
  
## <a name="see-also"></a>Siehe auch  
 [Beheben von spezifischen Fehlern in ClickOnce-Bereitstellungen](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Übersicht über die visuelle Stile](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Aktivieren von visuellen Stilen](https://msdn.microsoft.com/library/bb773175.aspx)   
 [Eingabeaufforderungen](/dotnet/framework/tools/developer-command-prompt-for-vs)