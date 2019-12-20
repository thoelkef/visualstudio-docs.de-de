---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fa926b21171c3e09b5a0f4d74e9415da090bf2f
ms.sourcegitcommit: 97623fd6190c43fed0d2ee7af92b01c375282622
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73569075"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor
Nachdem Sie einen benutzerdefinierten Editor erstellt haben, können Sie ihm weitere Funktionen hinzufügen.

## <a name="to-create-an-editor-for-a-vspackage"></a>So erstellen Sie einen Editor für ein VSPackage

1. Erstellen Sie mithilfe der Projektvorlage für Visual Studio-Pakete einen benutzerdefinierten Editor.

     Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Entscheiden Sie, ob Sie möchten, dass Ihr Editor eine einzelne Ansicht oder mehrere Ansichten unterstützt.

     Ein Editor, der den **neuen Fenster** Befehl oder die Formularansicht und die Code Ansicht unterstützt, erfordert separate Dokument Datenobjekte und Dokument Ansichts Objekte. In einem Editor, der nur eine einzelne Ansicht unterstützt, können das Dokument Datenobjekt und das Dokument Ansichts Objekt für dasselbe Objekt implementiert werden.

     Ein Beispiel für mehrere Ansichten finden Sie [unter Unterstützung mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md).

3. Implementieren Sie eine Editorfactory, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>-Schnittstelle einrichten.

     Weitere Informationen finden Sie unter [editorfactorys](../extensibility/editor-factories.md).

4. Entscheiden Sie, ob Sie möchten, dass der Editor die direkte Aktivierung oder die vereinfachte Einbettung verwendet, um das Dokument Ansichts Objekt Fenster zu verwalten.

     Ein vereinfachtes Fenster zum Einbetten eines Editors hostet eine Standarddokument Ansicht, während ein direktes Aktivierungs-Editor-Fenster ein ActiveX-Steuerelement oder ein anderes aktives Objekt als Dokument Ansicht hostet. Weitere Informationen finden Sie unter [vereinfachte Einbettung](../extensibility/simplified-embedding.md) und direkte [Aktivierung](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Schnittstelle zum Verarbeiten von Befehlen.

6. Dokument Persistenz und Antwort auf externe Dateiänderungen bereitstellen:

    1. Um die Datei beizubehalten, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> für das Dokument Datenobjekt des Editors.

    2. Um auf Änderungen externer Dateien zu reagieren, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> für das Dokument Datenobjekt des Editors.

        > [!NOTE]
        > `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> abrufen, um einen Zeiger auf `IVsFileChangeEx`zu erhalten.

7. Koordinieren Sie Dokument Bearbeitungs Ereignisse mit der Quell Code Verwaltung. Führen Sie folgende Schritte aus:

    1. Rufen Sie einen Zeiger auf `IVsQueryEditQuerySave2` auf, indem Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>aufrufen.

    2. Wenn das erste Bearbeitungs Ereignis auftritt, wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>-Methode aufgerufen.

         Diese Methode fordert den Benutzer auf, die Datei auszuchecken, wenn Sie nicht bereits ausgecheckt ist. Stellen Sie sicher, dass die Bedingung "Datei nicht ausgecheckt" behandelt wird, um Fehler zu verhindern.

    3. Gleichermaßen können Sie vor dem Speichern der Datei die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>-Methode aufzurufen.

         Diese Methode fordert den Benutzer auf, die Datei zu speichern, wenn Sie nicht gespeichert wurde, oder wenn Sie sich seit der letzten Speicherung geändert hat.

8. Aktivieren Sie das Fenster **Eigenschaften** , um Eigenschaften für Text anzuzeigen, der im Editor ausgewählt ist. Führen Sie folgende Schritte aus:

    1. Wenn Sie die Textauswahl ändern und die Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>übergeben, wird <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> aufgerufen.

    2. Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienst auf, um einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>zu erhalten.

9. Ermöglicht Benutzern das ziehen und Ablegen von Elementen zwischen dem Editor und der **Toolbox**oder zwischen externen Editoren (z. b. Microsoft Word) und der **Toolbox**. Führen Sie folgende Schritte aus:

    1. Implementieren Sie `IDropTarget` im Editor, um die IDE zu warnen, dass der Editor ein Ablage Ziel ist.

    2. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>-Schnittstelle in der Sicht, damit der Editor Elemente in der **Toolbox**aktivieren und deaktivieren kann.

    3. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A>, und rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> Dienst auf, um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>-und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> Schnittstellen zu erhalten.

         Mit diesen Schritten kann Ihr VSPackage neue Elemente zur **Toolbox**hinzufügen.

10. Entscheiden Sie, ob Sie weitere optionale Features für den Editor benötigen.

    - Wenn Sie möchten, dass der Editor Befehle zum Suchen und ersetzen unterstützt, implementieren Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.

    - Wenn Sie ein Dokument Gliederungs Tool Fenster in Ihrem Editor verwenden möchten, implementieren Sie `IVsDocOutlineProvider`.

    - Wenn Sie eine Statusleiste im Editor verwenden möchten, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> und `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>, um einen Zeiger auf `IVsStatusBar`abzurufen.

         Beispielsweise kann ein Editor Zeilen-/Spalteninformationen, den Auswahlmodus (Stream/Box) und den Einfügemodus (INSERT/OVERSTRIKE) anzeigen.

    - Wenn Sie möchten, dass der Editor den `Undo`-Befehl unterstützt, wird empfohlen, das OLE rückgängig-Manager-Modell zu verwenden. Als Alternative können Sie den Editor direkt mit dem `Undo` Befehl behandeln lassen.

11. Erstellen Sie Registrierungsinformationen, einschließlich der GUIDs für das VSPackage, die Menüs, den Editor und andere Funktionen.

     Im folgenden finden Sie ein allgemeines Beispiel für Code, den Sie in das *RGS* -Datei Skript einfügen, um zu veranschaulichen, wie ein Editor ordnungsgemäß registriert wird.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Implementieren der kontextbezogenen Hilfe Unterstützung.

     Dieser Schritt ermöglicht es Ihnen, F1-Hilfe und dynamische Hilfefenster Unterstützung für Elemente in Ihrem Editor bereitzustellen. Weitere Informationen finden Sie unter Gewusst [wie: Bereitstellen von Kontext für Editoren](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Machen Sie ein Automatisierungs Objektmodell aus dem Editor verfügbar, indem Sie die `IDispatch`-Schnittstelle implementieren.

     Weitere Informationen finden Sie unter [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Stabile Programmierung

- Die Editor-Instanz wird erstellt, wenn die IDE die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>-Methode aufruft. Wenn der Editor mehrere Ansichten unterstützt, erstellt `CreateEditorInstance` sowohl die Dokument Daten als auch die Dokument Ansichts Objekte. Wenn das Dokument Datenobjekt bereits geöffnet ist, wird ein `punkDocDataExisting` Wert ungleich NULL an `IVsEditorFactory::CreateEditorInstance`übermittelt. Die Editorfactory-Implementierung muss bestimmen, ob ein vorhandenes Dokument Datenobjekt kompatibel ist, indem entsprechende Schnittstellen abgefragt werden. Weitere Informationen finden Sie [unter unterstützen mehrerer Dokument Ansichten](../extensibility/supporting-multiple-document-views.md).

- Wenn Sie den vereinfachten Einbettungs Ansatz verwenden, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>-Schnittstelle.

- Wenn Sie die direkte Aktivierung verwenden möchten, implementieren Sie die folgenden Schnittstellen:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Die `IOleInPlaceComponent`-Schnittstelle wird verwendet, um die Zusammenführung von OLE 2-Menüs zu

   Die `IOleCommandTarget`-Implementierung verarbeitet Befehle wie **Ausschneiden**, **Kopieren**und **Einfügen**. Wenn Sie `IOleCommandTarget`implementieren, entscheiden Sie, ob Ihr Editor eine eigene *vsct* -Datei erfordert, um eine eigene Befehlsmenü Struktur zu definieren, oder ob Sie von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]definierte Standard Befehle implementieren kann. In der Regel verwenden Editoren die Menüs der IDE und definieren ihre eigenen Symbolleisten. Es ist jedoch häufig notwendig, dass ein Editor zusätzlich zur Verwendung des Standard Befehlssatzes der IDE seine eigenen spezifischen Befehle definiert. Der Editor muss die verwendeten Standard Befehle deklarieren und dann alle neuen Befehle, Kontextmenüs, Menüs der obersten Ebene und Symbolleisten in einer *vsct* -Datei definieren. Wenn Sie einen direkten Aktivierungs-Editor erstellen, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>, und definieren Sie die Menüs und Symbolleisten für den Editor in einer *vsct* -Datei anstelle der OLE 2-Menü Zusammenführung.

- Um die Überfüllung des Menübefehls in der Benutzeroberfläche zu verhindern, sollten Sie die vorhandenen Befehle in der IDE verwenden, bevor Sie neue Befehle erfinden. Freigegebene Befehle sind in " *sharedcmddef. vsct* " und " *shellcmddef. vsct*" definiert. Diese Dateien werden standardmäßig im Unterverzeichnis visualstudiointegration\common\inc der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]-Installation installiert.

- `ISelectionContainer` kann sowohl eine einfache als auch eine Mehrfachauswahl Ausdrücken. Jedes ausgewählte Objekt wird als `IDispatch` Objekt implementiert.

- Die IDE implementiert `IOleUndoManager` als Dienst, der von einem <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> oder als Objekt zugänglich ist, das über <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>instanziiert werden kann. Der Editor implementiert die `IOleUndoUnit`-Schnittstelle für jede `Undo` Aktion.

- Es gibt zwei Stellen, in denen ein benutzerdefinierter Editor Automatisierungs Objekte verfügbar machen kann:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Siehe auch

- [Zum Automatisierungs Modell beitragen](../extensibility/internals/contributing-to-the-automation-model.md)