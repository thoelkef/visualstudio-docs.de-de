---
title: 'Gewusst wie: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3691f782f317667b56f6bf3641c0f4c6a703eda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697574"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Gewusst wie: Veröffentlichen einer WPF-Anwendung mit aktivierten visuellen Stilen

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Durch visuelle Stile kann die Darstellung von allgemeinen Steuerelementen auf Grundlage des vom Benutzer ausgewählten Designs geändert werden. Standardmäßig werden keine visuellen Stile für WPF-Anwendungen (Windows Presentation Foundation) aktiviert. Daher müssen Sie sie manuell aktivieren. Allerdings tritt bei der Veröffentlichung der Projektmappe ein Fehler auf, wenn visuelle Stile für eine WPF-Anwendung aktiviert sind. In diesem Thema wird beschrieben, wie dieser Fehler zu beheben ist und wie eine WPF-Anwendung mit aktivierten visuellen Stilen veröffentlicht werden kann. Weitere Informationen zu visuellen Stilen finden Sie unter [Übersicht über visuelle Stile](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Weitere Informationen zur Fehlermeldung finden Sie unter [Problembehandlung bei bestimmten Fehlern in ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)-bereit Stellungen.

 Um den Fehler zu beheben und die Projektmappe zu veröffentlichen, müssen Sie die folgenden Schritte ausführen:

- [Veröffentlichen Sie die Projekt Mappe ohne aktivierte visuelle Stile](#BKMK_publishsolwovs).

- [Erstellen Sie eine Manifest-Datei](#BKMK_CreateManifest).

- [Betten Sie die Manifest-Datei in die ausführbare Datei der veröffentlichten](#BKMK_embedmanifest)Projekt Mappe ein.

- [Signieren Sie die Anwendungs-und Bereitstellungs Manifeste](#BKMK_signappdeplyman).

  Anschließend können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem Endbenutzer die Anwendung installieren sollen.

## <a name="publish-the-solution-without-visual-styles-enabled"></a><a name="BKMK_publishsolwovs"></a> Veröffentlichen der Projekt Mappe ohne aktivierte visuelle Stile

1. Stellen Sie sicher, dass visuelle Stile für das Projekt nicht aktiviert sind. Zuerst überprüfen Sie die Manifestdatei des Projekts auf folgende XML. Wenn der XML-Code vorhanden ist, schließen Sie ihn in ein Kommentartag ein.

     Visuelle Stile sind standardmäßig nicht aktiviert.

    ```xml
    <dependency>
        <dependentAssembly>
          <assemblyIdentity
              type="win32"
              name="Microsoft.Windows.Common-Controls"
              version="6.0.0.0"
              processorArchitecture="*"
              publicKeyToken="6595b64144ccf1df"
              language="*" />
        </dependentAssembly>
      </dependency>
    ```

     Die folgenden Prozeduren zeigen, wie die Manifestdatei geöffnet wird, die Ihrem Projekt zugeordnet ist.

    **So öffnen Sie die Manifestdatei in einem Visual Basic-Projekt**

    1. Wählen Sie in der Menüleiste **Projekt, Projekt** _Name_**Eigenschaften**aus, wobei *ProjectName* der Name des WPF-Projekts ist.

         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.

    2. Klicken Sie in der Registerkarte **Anwendung** auf **Windows-Einstellungen anzeigen**.

         Die Datei „app.manifest“ wird im **Code-Editor** geöffnet.

    **So öffnen Sie die Manifestdatei in einem C#-Projekt**

    1. Wählen Sie in der Menüleiste **Projekt, Projekt** _Name_**Eigenschaften**aus, wobei *ProjectName* der Name des WPF-Projekts ist.

         Die Eigenschaftenseiten für das WPF-Projekt werden angezeigt.

    2. Beachten Sie auf der Registerkarte **Anwendung** den Namen, der im Manifestfeld angezeigt wird. Dies ist der Name des Manifests, das dem Projekt zugeordnet ist.

        > [!NOTE]
        > Wenn **Manifest mit Standardeinstellungen einbetten** oder **Anwendung ohne Manifest erstellen** im Manifestfeld angezeigt wird, werden visuelle Designs nicht aktiviert. Wenn der Name einer Manifestdatei im Manifestfeld angezeigt wird, wechseln Sie zum nächsten Schritt in diesem Verfahren.

    3. Wählen Sie in **Projektmappen-Explorer**die Option **alle Dateien anzeigen** () aus.

         Mit dieser Schaltfläche werden alle Projektelemente angezeigt, einschließlich der ausgeschlossen und derjenigen, die normalerweise ausgeblendet werden. Die Manifestdatei erscheint als Projektelement.

2. Erstellen und veröffentlichen Sie die Projektmappe. Weitere Informationen zum Veröffentlichen der Lösung finden Sie unter Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem Webpublishing-Assistenten](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a><a name="BKMK_CreateManifest"></a> Manifest-Datei erstellen

1. Fügen Sie folgendes XML in eine Editor-Datei ein.

     Dieser XML-Code beschreibt die Assembly, die Steuerelemente enthält, die visuelle Stile unterstützen.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
     <asmv1:assembly manifestVersion="1.0"
         xmlns="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <dependency>
        <dependentAssembly>
          <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="*"
            publicKeyToken="6595b64144ccf1df"
            language="*" />
        </dependentAssembly>
      </dependency>
    </asmv1:assembly>
    ```

2. Klicken Sie im Editor auf **Datei** und dann auf **Speichern unter**.

3. Klicken Sie im Dialogfeld **Speichern unter** auf die Dropdownliste **Dateityp**, und wählen Sie **Alle Dateien** aus.

4. Geben Sie im Feld **Dateiname** einen Namen für die Datei ein, und fügen Sie dem Ende des Namens **.manifest** an. Beispiel: **themes.manifest**.

5. Klicken Sie auf die Schaltfläche **Ordner durchsuchen**, wählen Sie einen beliebigen Ordner aus, und klicken Sie dann auf **Speichern**.

    > [!NOTE]
    > Im verbleibenden Verfahren wird davon ausgegangen, dass der Name dieser Datei **themes.manifest** ist und auf dem Computer im Verzeichnis C:\temp gespeichert wird.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a><a name="BKMK_embedmanifest"></a> Einbetten der Manifest-Datei in die ausführbare Datei der veröffentlichten Projekt Mappe

1. Öffnen Sie die **Visual Studio-Eingabeaufforderung**.

    Weitere Informationen zum Öffnen der **Visual Studio-Eingabeaufforderung**finden Sie unter [Eingabe Aufforderungen](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).

   > [!NOTE]
   > In den verbleibenden Schritten werden die folgenden Annahmen über die Projektmappe gemacht:
   >
   > - Der Name der Projektmappe ist **MyWPFProject**.
   > - Die Lösung befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Die Projekt Mappe wird im folgenden Verzeichnis veröffentlicht: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Die neueste Version der veröffentlichten Anwendungs Dateien befindet sich im folgenden Verzeichnis: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Sie müssen die oben genannten Namen und Verzeichnisspeicherorte nicht verwenden. Die oben genannten Namen und Speicherorte dienen nur als Beispiele bei der Veranschaulichung der Schritte, die für die Veröffentlichung der Projektmappe erforderlich sind.

2. Ändern Sie an der Eingabeaufforderung den Pfad zu dem Verzeichnis, das die neueste Version der veröffentlichten Anwendungsdateien enthält. Das folgende Beispiel veranschaulicht diesen Schritt.

   ```
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Manifestdatei in die ausführbare Datei der Anwendung einzubetten:

   ```
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a><a name="BKMK_signappdeplyman"></a> Signieren der Anwendungs-und Bereitstellungs Manifeste

1. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die `.deploy`-Erweiterung aus der ausführbaren Datei im aktuellen Verzeichnis zu entfernen:

   ```
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass nur eine Datei die Dateierweiterung `.deploy` aufweist. Stellen Sie sicher, dass Sie alle Dateien in diesem Verzeichnis umbenennen, die die Dateierweiterung `.deploy` aufweisen.

2. Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Anwendungsmanifests ein:

   ```
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass Sie das Manifest mit der `.pfx`-Datei des Projekts signieren. Wenn Sie das Manifest nicht signieren, können Sie den-Parameter weglassen, der `–cf` in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat signieren, das ein Kennwort erfordert, geben Sie die `–password` Option ( `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` ) an.

3. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die `.deploy`-Erweiterung dem Namen der Datei hinzuzufügen, die Sie in einem vorherigen Schritt dieses Verfahrens umbenannt haben:

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass nur eine Datei die Dateierweiterung `.deploy` aufweist. Stellen Sie sicher, dass alle Dateien in diesem Verzeichnis umbenannt werden, die zuvor die Dateinamenerweiterung `.deploy` hatten.

4. Geben Sie an der Eingabeaufforderung den folgenden Befehl zum Signieren des Verteilungsmanifests ein:

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > In diesem Beispiel wird davon ausgegangen, dass Sie das Manifest mit der `.pfx`-Datei des Projekts signieren. Wenn Sie das Manifest nicht signieren, können Sie den-Parameter weglassen, der `–cf` in diesem Beispiel verwendet wird. Wenn Sie das Manifest mit einem Zertifikat signieren, das ein Kennwort erfordert, geben Sie die `–password` Option an, wie in diesem Beispiel: `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` .

   Nachdem Sie diese Schritte ausgeführt haben, können Sie die veröffentlichten Dateien an den Speicherort verschieben, von dem aus Endbenutzer die Anwendung installieren sollen. Wenn Sie beabsichtigen, die Projektmappe häufig zu aktualisieren, können Sie diese Befehle in ein Skript übernehmen und das Skript jedes Mal ausführen, wenn Sie eine neue Version veröffentlichen.

## <a name="see-also"></a>Weitere Informationen

[Problembehandlung bei bestimmten Fehlern in ClickOnce-bereit Stellungen](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md) 
 [Übersicht über](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e) 
 visuelle Stile [Eingabe Aufforderungen](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)
