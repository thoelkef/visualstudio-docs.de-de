---
title: "Exemplarische Vorgehensweise: Hinzuf&#252;gen eines benutzerdefinierten Editors von Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] benutzerdefinierte - hinzufügen Funktionen."
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Exemplarische Vorgehensweise: Hinzuf&#252;gen eines benutzerdefinierten Editors von Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nach der Erstellung eines benutzerdefinierten Editors können Sie weitere Funktionen hinzufügen.  
  
### Erstellen Sie einen Editor für ein VSPackage  
  
1.  Erstellen Sie einen benutzerdefinierten Editor mithilfe der Projektvorlage Visual Studio\-Paket.  
  
     Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Editors](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Entscheiden Sie, ob Sie den Editor, um eine einzelne oder mehrere Ansichten zu unterstützen.  
  
     Ein Editor, der unterstützt die **Neues Fenster** Befehl oder Formularansicht und in der Codeansicht, erfordert separates Dokument Datenobjekte und Document\-Objekte. In einem Editor, der nur eine einzige Ansicht unterstützt, können das Dokumentobjekt für die Daten und das Dokument Ansichtsobjekt für dasselbe Objekt implementiert werden.  
  
     Ein Beispiel für mehrere Ansichten, finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementieren Sie eine Editorfactory durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.  
  
     Weitere Informationen finden Sie unter [Editor\-Factorys](../extensibility/editor-factories.md).  
  
4.  Entscheiden Sie, ob Sie den Editor für die direkte Aktivierung oder zum Vereinfachen des Einbettens um Dokumentfenster anzeigen Objekt zu verwalten.  
  
     Eine vereinfachte einbetten\-Editor\-Fenster eine standardmäßige Dokumentansicht als Host für eine direkte Aktivierung\-Editor\-Fenster ein ActiveX\-Steuerelement oder andere aktive Objekt als Dokumentansicht hostet. Weitere Informationen finden Sie unter [Vereinfachen des Einbettens](../extensibility/simplified-embedding.md) und [Direkte Aktivierung](../misc/in-place-activation.md).  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, um Befehle zu verarbeiten.  
  
6.  Geben Sie Dokument Persistenz und Änderungen der externen Datei wie folgt:  
  
    1.  Behalten Sie die Datei implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Ihres Dokuments\-Datenobjekt.  
  
    2.  Um externe Datei Änderungen zu reagieren, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> Ihres Dokuments\-Datenobjekt.  
  
        > [!NOTE]
        >  Rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> einen Zeiger auf `IVsFileChangeEx`.  
  
7.  Koordinieren von Ereignissen mit Quellcode bearbeiten. Gehen Sie dazu wie folgt vor:  
  
    1.  Abrufen eines Zeigers auf `IVsQueryEditQuerySave2` durch Aufrufen von `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Tritt das erste Ereignis bearbeiten, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methode.  
  
         Der Aufforderung, die Datei auschecken, wenn es nicht bereits ausgecheckt ist. Achten Sie darauf, dass Sie eine Bedingung "Datei nicht ausgecheckt" AVERT Fehler behandeln  
  
    3.  Rufen Sie vor dem Speichern der Datei entsprechend der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> Methode.  
  
         Diese Methode fordert den Benutzer zum Speichern der Datei, wenn es nicht gespeichert wurde oder wenn es seit der letzten Speicherung geändert hat.  
  
8.  Aktivieren der **Eigenschaften** im Fenster Eigenschaften für den ausgewählten Text in Editor angezeigt. Gehen Sie dazu wie folgt vor:  
  
    1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> jedes Mal Textauswahl geändert wird, übergeben die Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienst, um einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Aktivieren von Benutzern für Drag & drop zwischen der\-Editor und die **Toolbox**, oder zwischen externen Editoren \(z. B. Microsoft Word\) und die **Toolbox**. Gehen Sie dazu wie folgt vor:  
  
    1.  Implementieren `IDropTarget` auf Ihrem Editor der IDE informiert, dass der Editor ein Ablageziel ist.  
  
    2.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> Schnittstelle für die Sicht so Editor kann aktivieren und Deaktivieren von Elementen in der **Toolbox**.  
  
    3.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> und rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> Dienst, um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> Schnittstellen.  
  
         Dies ermöglicht das VSPackage Hinzufügen neuer Elemente zu den **Toolbox**.  
  
10. Entscheiden Sie, ob Sie andere optionale Features für den Editor.  
  
    -   Wenn den Editor unterstützt werden sollen suchen und Befehle ersetzen, implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Wenn Sie eine Dokumentgliederungsfenster in Ihrem Editor verwenden möchten, implementieren `IVsDocOutlineProvider`.  
  
    -   Wenn Sie eine Statusleiste im Editor verwenden möchten, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> und rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> einen Zeiger auf `IVsStatusBar`.  
  
         Zeigt z. B. ein Editor kann Zeile \/ Spalteninformationen, Auswahlmodus \(stream \/ Feld\), und Einfügemodus \(insert \/ Insert&#124;\).  
  
    -   Wenn den Editor unterstützt werden sollen die `Undo` Befehl die empfohlene Methode ist die Verwendung von OLE\-Modell für die rückgängig\-Manager. Als Alternative können Sie das Editor\-Handle der `Undo` Befehl direkt.  
  
11. Erstellen Sie die Registrierung Informationen, einschließlich der GUIDs für das VSPackage, die Menüs, Editor und andere Funktionen.  
  
     Im folgenden ist ein allgemeines Beispiel für Code, den Sie in Ihrem Skript des .rgs\-Datei veranschaulicht, wie Sie einen Editor ordnungsgemäß registriert einfügen würden.  
  
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
  
12. Implementieren Sie die kontextbezogene Hilfe an.  
  
     Dadurch können Sie zur Gewährleistung der Unterstützung von F1\-Hilfe und im Fenster Dynamische Hilfe für Elemente im Editor. Weitere Informationen hierzu finden Sie unter [Gewusst wie: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Verfügbar machen eines Automation\-Objektmodells von Editor durch Implementieren der `IDispatch` Schnittstelle.  
  
     Weitere Informationen finden Sie unter [Das Automatisierungsmodell beitragen.](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Stabile Programmierung  
  
-   Die Editor\-Instanz wird erstellt, wenn die IDE Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode. Wenn der Editor über mehrere Ansichten unterstützt `CreateEditorInstance` erstellt, die Daten und die Document\-Objekte anzeigen. Wenn das Datenobjekt Dokument bereits ist zu öffnen, eine Wert ungleich Null `punkDocDataExisting` Wert wird übergeben, um `IVsEditorFactory::CreateEditorInstance`. Die Implementierung der Factory\-muss bestimmen, ob ein vorhandenes Dokument Datenobjekt kompatibel ist, durch Abfragen von entsprechenden Schnittstellen auf. Weitere Informationen finden Sie unter [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
-   Wenn Sie die vereinfachten einbetten Ansatz verwenden, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle.  
  
-   Wenn Sie die direkte Aktivierung verwenden, werden implementieren Sie die folgenden Schnittstellen:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Die `IOleInPlaceComponent` Schnittstelle wird verwendet, um OLE 2 das Zusammenführen von Menüs zu vermeiden.  
  
     Die `IOleCommandTarget` Implementierung behandelt Befehle wie z. B. **Ausschneiden**, **Kopie**, und **Einfügen**. Beim Implementieren von `IOleCommandTarget`, entscheiden, ob Editor eigene VSCT\-Datei Definieren eigener Befehl Menüstruktur erfordert oder wenn es von definierten standard Befehle implementieren kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In der Regel Editoren verwenden, erweitern die IDE Menüs und definieren ihre eigenen Symbolleisten. Allerdings ist es oft erforderlich für einen Editor definieren Sie eigene Befehle zusätzlich zur Verwendung der IDE\-standard\-Befehlssatz. Zu diesem Zweck muss Editor deklarieren die Standardbefehle es verwendet, und klicken Sie dann neue Befehle, Kontextmenüs, Menüs der obersten Ebene und Symbolleisten in einer VSCT\-Datei definieren. Wenn Sie eine direkte Aktivierung\-Editor erstellen, dann implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> und definieren Sie die Menüs und Symbolleisten für den Editor in einer VSCT\-Datei anstelle von OLE 2 das Zusammenführen von Menüs.  
  
-   Um Menübefehl Versammeln in der Benutzeroberfläche zu verhindern, sollten Sie die vorhandenen Befehle vor erfinden neue Befehle in der IDE verwenden. Freigegebene Befehle werden in SharedCmdDef.vsct und ShellCmdDef.vsct definiert. Diese Dateien werden standardmäßig im Unterverzeichnis VisualStudioIntegration\\Common\\Inc installiert die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installation.  
  
-   `ISelectionContainer` einzelne und mehrere Auswahlmöglichkeiten können ausgedrückt werden. Jedes ausgewählte Objekt wird als implementiert ein `IDispatch` Objekt.  
  
-   Die IDE implementiert `IOleUndoManager` als Dienst über eine <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> oder als ein Objekt, das durch die instanziiert werden kann <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Der Editor implementiert die `IOleUndoUnit` Schnittstelle für jede `Undo` Aktion.  
  
-   Es gibt zwei Stellen ein benutzerdefinierter Editor Automatisierungsobjekte verfügbar machen:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## Siehe auch  
 [Das Automatisierungsmodell beitragen.](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Gewusst wie: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)