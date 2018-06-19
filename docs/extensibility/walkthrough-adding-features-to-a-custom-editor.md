---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Funktionen eines benutzerdefinierten Editors | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14642a13553f3c4a09b86daa2d7638183fe7d8d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146022"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Exemplarische Vorgehensweise: Hinzufügen eines benutzerdefinierten Editors von Funktionen
Nach der Erstellung eines benutzerdefinierten Editors können Sie weitere Funktionen hinzufügen.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Beim Erstellen eines Editors für ein VSPackage  
  
1.  Erstellen Sie einen benutzerdefinierten Editor, indem Sie mit der Visual Studio-Paket-Projektvorlage.  
  
     Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Entscheiden Sie, ob den Editor eine einzelne oder mehrere Ansichten unterstützt werden sollen.  
  
     Einen Editor, den unterstützt die **neues Fenster** -Befehls oder Formularansicht und in der Codeansicht, Datenobjekte separates Dokument und Ansicht-Dokumentobjekte erfordert. In einem Editor, der nur eine einzige Ansicht unterstützt, kann das dokumentdatenobjekt und des dokumentansichtsobjekts für dasselbe Objekt implementiert werden.  
  
     Ein Beispiel für mehrere Ansichten, finden Sie unter [unterstützen mehrere Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementieren Sie eine Editorfactory durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.  
  
     Weitere Informationen finden Sie unter [Editorfactorys](../extensibility/editor-factories.md).  
  
4.  Entscheiden Sie, ob den Editor die direkte Aktivierung verwendet werden soll oder einbetten vereinfacht, um das Dokument Objekt Ansichtsfenster verwalten.  
  
     Ein vereinfachtes Einbetten von Editor-Fenster hostet eine standardmäßige Dokumentenansicht, während eine direkte Aktivierung-Editor-Fenster ein ActiveX-Steuerelement oder andere aktive Objekt als Dokumentansicht hostet. Weitere Informationen finden Sie unter [vereinfacht einbetten](../extensibility/simplified-embedding.md) und [direkte Aktivierung](../extensibility/in-place-activation.md).  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, um Befehle zu behandeln.  
  
6.  Geben Sie Dokument Persistenz und als Reaktion auf Änderungen der externen Datei wie folgt an:  
  
    1.  Um die Datei beizubehalten, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> auf dokumentdatenobjekt des Editors.  
  
    2.  Um auf Änderungen der externen Datei zu reagieren, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> auf dokumentdatenobjekt des Editors.  
  
        > [!NOTE]
        >  Rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> um einen Zeiger auf `IVsFileChangeEx`.  
  
7.  Bearbeiten der Dokumentereignisse mit quellcodeverwaltung zu koordinieren. Gehen Sie dazu wie folgt vor:  
  
    1.  Abrufen eines Zeigers auf `IVsQueryEditQuerySave2` durch Aufrufen von `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Tritt das erste Ereignis bearbeiten, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methode.  
  
         Dadurch wird der Benutzer die Datei auschecken, wenn es nicht bereits ausgecheckt ist aufgefordert. Achten Sie darauf, dass Sie eine "Datei nicht ausgecheckt" Bedingung AVERT Fehler behandeln  
  
    3.  Rufen Sie vor dem Speichern der Datei auf ähnliche Weise die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> Methode.  
  
         Diese Methode fordert den Benutzer zum Speichern der Datei, wenn sie nicht gespeichert wurde oder wenn es seit der letzten Speicherung geändert hat.  
  
8.  Aktivieren der **Eigenschaften** im Fenster Eigenschaften für Text im Editor angezeigt. Gehen Sie dazu wie folgt vor:  
  
    1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> jedes Mal Textauswahl ändert das Übergeben von in der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienst um einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Benutzern das Ziehen und Ablegen von Elementen zwischen den Editor zu aktivieren und die **Toolbox**, oder zwischen externen Editoren (z. B. Microsoft Word) und die **Toolbox**. Gehen Sie dazu wie folgt vor:  
  
    1.  Implementieren `IDropTarget` auf Ihrem-Editor der IDE benachrichtigt, dass der Editor Ablageziel ist.  
  
    2.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> Schnittstelle für die Sicht, damit der Editor kann aktivieren und Deaktivieren von Elementen in der **Toolbox**.  
  
    3.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> , und rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> Dienst um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> Schnittstellen.  
  
         Dadurch können Ihre VSPackage, um neue Elemente hinzufügen das **Toolbox**.  
  
10. Entscheiden Sie, ob andere optionale Features für den Editor verwendet werden soll.  
  
    -   Wenn den Editor unterstützt werden sollen suchen und Ersetzen Sie Befehle, implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Wenn Sie eine Dokumentgliederungsfenster im Editor verwenden möchten, implementieren `IVsDocOutlineProvider`.  
  
    -   Wenn Sie eine Statusleiste im Editor verwenden möchten, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> , und rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> um einen Zeiger auf `IVsStatusBar`.  
  
         Z. B. ein Editor Zeile anzeigen kann / Informationen in der Spalte, die Mehrfachauswahlmodus aufweist (stream / Feld), und der Einfügemodus (einfügen / Insert|).  
  
    -   Wenn den Editor unterstützt werden sollen die `Undo` Befehl, wird empfohlen, das OLE-rückgängig-Manager-Modell verwenden. Als Alternative können Sie die Editor-Handle lassen die `Undo` Befehl direkt.  
  
11. Erstellen Sie die Registrierung Informationen, z. B. die GUIDs für das VSPackage, die Menüs, Editor und andere Funktionen.  
  
     Im folgenden ist ein allgemeines Beispiel des Codes, die Sie in Ihrem RGS-Datei-Skript veranschaulicht, wie Sie einen Editor ordnungsgemäß registrieren einfügen würden.  
  
    ```  
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
  
12. Implementieren Sie kontextbezogene Hilfe und Unterstützung.  
  
     Dadurch können Sie angeben, dass die Unterstützung von F1-Hilfe und dynamische Hilfefenster für Elemente im Editor. Weitere Informationen dazu finden Sie unter [Vorgehensweise: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Verfügbar machen eine Automatisierungsobjektmodell aus dem Editor durch Implementieren der `IDispatch` Schnittstelle.  
  
     Weitere Informationen finden Sie unter [zum Automatisierungsmodell beitragen](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Stabile Programmierung  
  
-   Die Editorinstanz wird erstellt, wenn die IDE Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode. Wenn der Editor über mehrere Ansichten unterstützt `CreateEditorInstance` erstellt die Dokumentdaten und der Document-Objekte anzeigen. Ist das dokumentdatenobjekt bereits geöffnet, eine Wert ungleich Null `punkDocDataExisting` an übergebene Wert `IVsEditorFactory::CreateEditorInstance`. Die Editor-Factory-Implementierung muss bestimmen, ob ein vorhandenes dokumentdatenobjekt kompatibel durch Abfragen der entsprechenden Schnittstellen auf. Weitere Informationen finden Sie unter [unterstützen mehrere Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
-   Wenn Sie das Einbetten von vereinfachten Ansatz verwenden, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle.  
  
-   Wenn Sie die direkte Aktivierung verwenden möchten, werden implementieren Sie die folgenden Schnittstellen:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Die `IOleInPlaceComponent` Schnittstelle wird verwendet, um OLE 2 das Zusammenführen von Menüs zu vermeiden.  
  
     Ihre `IOleCommandTarget` Implementierung behandelt Befehle wie z. B. **Ausschneiden**, **Kopie**, und **einfügen**. Bei der Implementierung `IOleCommandTarget`, entscheiden, ob der Editor eine eigene VSCT-Datei, um einen eigenen Menüstruktur Befehl definieren erforderlich ist oder wenn er durch definierten Standardbefehle implementieren kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In der Regel Editoren verwenden und Erweitern der IDE-Menüs und definieren ihre eigenen Symbolleisten haben. Allerdings ist es oft erforderlich, für einen Editor so definieren Sie einen eigenen bestimmten Befehle zusätzlich zur Verwendung der IDE-standard-Befehlssatz. Zu diesem Zweck muss der Editor die standard-Befehle verwendet werden können, und definieren Sie neuen Befehle, die Kontextmenüs, die Menüs der obersten Ebene und die Symbolleisten in einer VSCT-Datei deklarieren. Wenn Sie eine direkte Aktivierung-Editor erstellen, dann implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> und definieren Sie die Menüs und Symbolleisten für den Editor in einer VSCT-Datei anstelle von OLE 2 das Zusammenführen von Menüs.  
  
-   Um in der Benutzeroberfläche Versammeln Menübefehl zu verhindern, sollten Sie die vorhandene Befehle in der IDE verwenden, bevor Sie neue Befehle gleichzeitig. Freigegebene Befehle werden in SharedCmdDef.vsct und ShellCmdDef.vsct definiert. Diese Dateien werden standardmäßig installiert, in das Unterverzeichnis VisualStudioIntegration\Common\Inc Ihrer [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installation.  
  
-   `ISelectionContainer` können einzelne und mehrere Auswahlmöglichkeiten Ausdrücken. Jedes ausgewählte Objekt wird als implementiert ein `IDispatch` Objekt.  
  
-   Die IDE implementiert die `IOleUndoManager` als Dienst zugegriffen werden kann, aus einer <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> oder als ein Objekt, das über instanziiert werden kann <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Der Editor implementiert die `IOleUndoUnit` Schnittstelle für die einzelnen `Undo` Aktion.  
  
-   Es gibt zwei Bereiche kann in ein benutzerdefinierter Editor Automatisierungsobjekte verfügbar machen:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Siehe auch  
 [Das Automatisierungsmodell beitragen.](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Vorgehensweise: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)