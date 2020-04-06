---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Features zu einem benutzerdefinierten Editor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697791"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Exemplarische Vorgehensweise: Hinzufügen von Features zu einem benutzerdefinierten Editor
Nachdem Sie einen benutzerdefinierten Editor erstellt haben, können Sie ihm weitere Features hinzufügen.

## <a name="to-create-an-editor-for-a-vspackage"></a>So erstellen Sie einen Editor für ein VSPackage

1. Erstellen Sie einen benutzerdefinierten Editor mithilfe der Visual Studio Package-Projektvorlage.

     Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Entscheiden Sie, ob der Editor eine einzelne Ansicht oder mehrere Ansichten unterstützen soll.

     Ein Editor, der den Befehl **"Neues Fenster"** unterstützt oder über Formular- und Codeansicht verfügt, erfordert separate Dokumentdatenobjekte und Dokumentansichtsobjekte. In einem Editor, der nur eine einzelne Ansicht unterstützt, können das Dokumentdatenobjekt und das Dokumentansichtsobjekt für dasselbe Objekt implementiert werden.

     Ein Beispiel für mehrere Ansichten finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).

3. Implementieren Sie eine Editorfactory, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle einrichten.

     Weitere Informationen finden Sie unter [Editor-Fabriken](../extensibility/editor-factories.md).

4. Entscheiden Sie, ob der Editor die direkte Aktivierung oder die vereinfachte Einbettung verwenden soll, um das Objektfenster für die Dokumentansicht zu verwalten.

     Ein vereinfachtes Einbettungs-Editorfenster hostet eine Standarddokumentansicht, während ein ortsspezifisches Aktivierungseditorfenster ein ActiveX-Steuerelement oder ein anderes aktives Objekt als Dokumentansicht hostet. Weitere Informationen finden Sie unter [Vereinfachtes Einbetten](../extensibility/simplified-embedding.md) und [Direkteaktivierung](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Sie die Schnittstelle zum Behandeln von Befehlen.

6. Bereitstellen der Dokumentpersistenz und Antwort auf externe Dateiänderungen:

    1. Um die Datei <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> beizubehalten, implementieren Sie und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> auf dem Dokumentdatenobjekt des Editors.

    2. Um auf externe Dateiänderungen <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> zu reagieren, implementieren Sie und auf das Dokumentdatenobjekt Ihres Editors.

        > [!NOTE]
        > Rufen `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> Sie an, um `IVsFileChangeEx`einen Zeiger auf zu erhalten.

7. Koordinieren Sie Dokumentbearbeitungsereignisse mit der Quellcodeverwaltung. Folgen Sie diesen Schritten:

    1. Erhalten Sie einen `IVsQueryEditQuerySave2` Zeiger, indem Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>aufrufen.

    2. Wenn das erste Bearbeitungsereignis <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> auftritt, rufen Sie die Methode auf.

         Diese Methode fordert den Benutzer auf, die Datei auszuchecken, wenn sie noch nicht ausgecheckt ist. Achten Sie darauf, eine "Datei nicht ausgecheckt" Bedingung zu behandeln, um Fehler zu vermeiden.

    3. Auf ähnliche Weise rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> vor dem Speichern der Datei die Methode auf.

         Diese Methode fordert den Benutzer auf, die Datei zu speichern, wenn sie nicht gespeichert wurde oder sich seit dem letzten Speichern geändert hat.

8. Aktivieren Sie das **Eigenschaftenfenster,** um Eigenschaften für im Editor ausgewählten Text anzuzeigen. Folgen Sie diesen Schritten:

    1. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Sie jedes Mal auf, wenn <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>sich die Textauswahl ändert, und übergeben Sie die Implementierung von .

    2. Rufen `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Sie den Dienst an, um einen Zeiger auf zu <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>erhalten.

9. Ermöglichen Sie Benutzern das Ziehen und Ablegen von Elementen zwischen dem Editor und der **Toolbox**oder zwischen externen Editoren (z. B. Microsoft Word) und der **Toolbox**. Folgen Sie diesen Schritten:

    1. Implementieren `IDropTarget` Sie auf Ihrem Editor, um die IDE darauf aufmerksam zu machen, dass Ihr Editor ein Drop-Ziel ist.

    2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> Sie die Schnittstelle in der Ansicht, damit Ihr Editor Elemente in der **Toolbox**aktivieren und deaktivieren kann.

    3. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> und `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> aufrufen Sie den Dienst, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> um einen Zeiger auf die und Schnittstellen zu erhalten.

         Mit diesen Schritten können Sie mit Ihrem VSPackage neue Elemente zur **Toolbox**hinzufügen.

10. Entscheiden Sie, ob Sie weitere optionale Funktionen für Ihren Editor benötigen.

    - Wenn Ihr Editor die Suche und den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>Austausch von Befehlen unterstützen soll, implementieren Sie .

    - Wenn Sie ein Dokumentgliederungstoolfenster in `IVsDocOutlineProvider`Ihrem Editor verwenden möchten, implementieren Sie .

    - Wenn Sie eine Statusleiste in Ihrem <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Editor `QueryService` verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> möchten, implementieren `IVsStatusBar`und rufen Sie an, um einen Zeiger auf zu erhalten.

         Beispielsweise kann ein Editor Zeilen-/Spalteninformationen, Auswahlmodus (Stream / Box) und Einfügemodus (Einfügen / Überschlagen) anzeigen.

    - Wenn der Editor den `Undo` Befehl unterstützen soll, wird empfohlen, das OLE-Rückgängig-Manager-Modell zu verwenden. Alternativ können Sie den Editor direkt `Undo` über den Befehl verwenden lassen.

11. Erstellen Sie Registrierungsinformationen, einschließlich der GUIDs für das VSPackage, die Menüs, den Editor und andere Funktionen.

     Im Folgenden finden Sie ein allgemeines Beispiel für Code, den Sie in Ihr *.rgs-Dateiskript* setzen würden, um zu veranschaulichen, wie ein Editor ordnungsgemäß registriert wird.

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

12. Implementieren Sie kontextsensitive Hilfeunterstützung.

     In diesem Schritt können Sie F1-Hilfe und dynamische Hilfeunterstützung für Elemente in Ihrem Editor bereitstellen. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen von Kontext für Editoren](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Stellen Sie ein Automatisierungsobjektmodell `IDispatch` aus dem Editor bereit, indem Sie die Schnittstelle implementieren.

     Weitere Informationen finden Sie unter [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Stabile Programmierung

- Die Editorinstanz wird erstellt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> wenn die IDE die Methode aufruft. Wenn der Editor mehrere `CreateEditorInstance` Ansichten unterstützt, werden sowohl die Dokumentdaten als auch die Dokumentansichtsobjekte erstellt. Wenn das Dokumentdatenobjekt bereits geöffnet ist, wird ein Wert ungleich NULL `punkDocDataExisting` an `IVsEditorFactory::CreateEditorInstance`übergeben. Die Editor factory-Implementierung muss bestimmen, ob ein vorhandenes Dokumentdatenobjekt kompatibel ist, indem Sie nach geeigneten Schnittstellen für dieses Objekt abfragen. Weitere Informationen finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).

- Wenn Sie den vereinfachten Einbettungsansatz verwenden, implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle.

- Wenn Sie sich für die in-Place-Aktivierung entscheiden, implementieren Sie die folgenden Schnittstellen:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Die `IOleInPlaceComponent` Schnittstelle wird verwendet, um eine Zusammenführung des OLE 2-Menüs zu vermeiden.

   Ihre `IOleCommandTarget` Implementierung verarbeitet Befehle wie **Ausschneiden**, **Kopieren**und **Einfügen**. Entscheiden `IOleCommandTarget`Sie beim Implementieren, ob der Editor eine eigene *.vsct-Datei* benötigt, um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]seine eigene Befehlsmenüstruktur zu definieren, oder ob er Standardbefehle implementieren kann, die durch definiert sind. In der Regel verwenden und erweitern Editoren die Menüs der IDE und definieren ihre eigenen Symbolleisten. Es ist jedoch häufig erforderlich, dass ein Editor zusätzlich zur Verwendung des Standardbefehlssatzes der IDE eigene spezifische Befehle definiert. Der Editor muss die von ihm verwendeten Standardbefehle deklarieren und dann alle neuen Befehle, Kontextmenüs, Menüs der obersten Ebene und Symbolleisten in einer *.vsct-Datei* definieren. Wenn Sie einen ortseinen Aktivierungseditor erstellen, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> und definieren Sie die Menüs und Symbolleisten für den Editor in einer *.vsct-Datei,* anstatt ole 2-Menüzusammenführen zu verwenden.

- Um das Überfüllung des Menübefehls in der Benutzeroberfläche zu verhindern, sollten Sie die vorhandenen Befehle in der IDE verwenden, bevor Sie neue Befehle erfinden. Freigegebene Befehle werden in *SharedCmdDef.vsct* und *ShellCmdDef.vsct*definiert. Diese Dateien werden standardmäßig im Unterverzeichnis VisualStudioIntegration-Common-Inc Ihrer [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installation installiert.

- `ISelectionContainer`kann sowohl Einzel- als auch Mehrfachauswahlen ausdrücken. Jedes ausgewählte Objekt wird `IDispatch` als Objekt implementiert.

- Die IDE `IOleUndoManager` implementiert als Dienst, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> auf den von einem oder als <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>Objekt zugegriffen werden kann, das über instanziiert werden kann. Ihr Editor implementiert `IOleUndoUnit` die `Undo` Schnittstelle für jede Aktion.

- Es gibt zwei Stellen, an denen ein benutzerdefinierter Editor Automatisierungsobjekte verfügbar machen kann:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Weitere Informationen

- [Beitrag zum Automatisierungsmodell](../extensibility/internals/contributing-to-the-automation-model.md)
