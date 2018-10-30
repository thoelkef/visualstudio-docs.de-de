---
title: 'Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einem benutzerdefinierten Editor | Microsoft-Dokumentation'
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
ms.openlocfilehash: 7062f44fe119858e579a53325deca0ea04b46475
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873018"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Exemplarische Vorgehensweise: Hinzufügen von Funktionen zu einer benutzerdefinierten editor
Nachdem Sie einen benutzerdefinierten Editor erstellt haben, können Sie weitere Features, hinzufügen.  
  
## <a name="to-create-an-editor-for-a-vspackage"></a>Beim Erstellen eines Editors für ein VSPackage  
  
1.  Erstellen Sie einen benutzerdefinierten Editor, indem Sie mithilfe der Visual Studio-Paket-Projektvorlage.  
  
     Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefiniertes Editors](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Entscheiden Sie, ob Sie Ihren-Editor, um eine einzelne oder mehrere Ansichten zu unterstützen.  
  
     Einen Editor, unterstützt die **neues Fenster** Befehl oder Formularansicht und Codeansicht, sind separate dokumentdatenobjekten und dokumentenansichtsobjekten erforderlich. In einem Editor, der nur eine einzige Ansicht unterstützt, kann auf demselben Objekt das dokumentendatenobjekt und dem dokumentenansichtsobjekt implementiert werden.  
  
     Ein Beispiel für mehrere Ansichten, finden Sie unter [unterstützen mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementieren eine Editor-Factory durch das Einrichten der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> Schnittstelle.  
  
     Weitere Informationen finden Sie unter [editorfactorys](../extensibility/editor-factories.md).  
  
4.  Entscheiden Sie, ob Sie Ihre-Editor, um die direkte Aktivierung verwendet werden soll, oder zum Vereinfachen des Einbettens, um das Dokumentfenster des Ansicht-Objekt zu verwalten.  
  
     Ein vereinfachtes einbetten Editor-Fenster hostet eine standardmäßige Dokumentenansicht, während ein Editor-Fenster für die direkte Aktivierung ein ActiveX-Steuerelement oder andere aktive Objekt als Dokumentansicht hostet. Weitere Informationen finden Sie unter [vereinfachtes einbetten](../extensibility/simplified-embedding.md) und [direkte Aktivierung](../extensibility/in-place-activation.md).  
  
5.  Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle, um Befehle zu verarbeiten.  
  
6.  Geben Sie Dokument Persistenz und Reaktion auf Änderungen der externen Datei:  
  
    1.  Behalten Sie die Datei implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> auf dokumentendatenobjekt des Editors.  
  
    2.  Um externe Änderungen zu reagieren, implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> auf dokumentendatenobjekt des Editors.  
  
        > [!NOTE]
        >  Rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> um einen Zeiger auf `IVsFileChangeEx`.  
  
7.  Bearbeiten der Dokumentereignisse mit quellcodeverwaltung zu koordinieren. Führen Sie folgende Schritte aus:  
  
    1.  Erhalten Sie einen Zeiger auf `IVsQueryEditQuerySave2` durch Aufrufen von `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Wenn das erste bearbeiten-Ereignis auftritt, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Methode.  
  
         Diese Methode der Benutzer aufgefordert, die Datei auschecken, wenn sie nicht bereits ausgecheckt wird. Achten Sie darauf, behandeln eine Bedingung "Datei nicht ausgecheckt", um diese Fehler zu vermeiden.  
  
    3.  Rufen Sie vor dem Speichern der Datei an, auf ähnliche Weise die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> Methode.  
  
         Diese Methode fordert den Benutzer zum Speichern der Datei, wenn sie noch nicht gespeichert wurde oder wenn es sich seit der letzten Speicherung geändert.  
  
8.  Aktivieren der **Eigenschaften** Fenster aus, um die Eigenschaften im Editor ausgewählten Text anzuzeigen. Führen Sie folgende Schritte aus:  
  
    1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> jedes Mal Textauswahl geändert wird, übergibt in der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Dienst um einen Zeiger auf abrufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Aktivieren von Benutzern für Drag & drop Elemente zwischen dem-Editor und die **Toolbox**, oder zwischen externen Editors (z. B. Microsoft Word) und die **Toolbox**. Führen Sie folgende Schritte aus:  
  
    1.  Implementieren `IDropTarget` in Ihrem Editor, um der Editor ein Ablageziel ist der IDE zu informieren.  
  
    2.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> Schnittstelle für die Sicht, damit der Editor kann aktivieren und Deaktivieren von Elementen in der **Toolbox**.  
  
    3.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> , und rufen Sie `QueryService` auf <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> Dienst erhalten einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> Schnittstellen.  
  
         Die folgenden Schritte ermöglichen das VSPackage, neue Elemente hinzufügen das **Toolbox**.  
  
10. Entscheiden Sie, ob Sie alle anderen optionalen Features für den Editor.  
  
    -   Wenn Sie Ihre-Editor unterstützt werden sollen, suchen und Befehle ersetzen, implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Wenn Sie ein dokumentgliederung-Toolfenster in Ihrem Editor verwenden möchten, implementieren Sie `IVsDocOutlineProvider`.  
  
    -   Wenn Sie eine Statusleiste im Editor verwenden möchten, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> , und rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> um einen Zeiger auf `IVsStatusBar`.  
  
         Ein Editor kann z. B. Zeile anzeigen / Spalteninformationen, Auswahlmodus (streamen / Feld), und Einfügemodus (eingefügt / Insert|).  
  
    -   Wenn Sie Ihre-Editor unterstützt werden sollen die `Undo` Befehl, die empfohlene Methode ist die Verwendung von OLE rückgängig-Manager-Modell. Als Alternative können Sie das Handle des Editors haben die `Undo` direkt den Befehl.  
  
11. Erstellen Sie die Registrierung Informationen, einschließlich die GUIDs für das VSPackage, die Menüs, Editor und andere Funktionen.  
  
     Folgendes ist ein allgemeines Beispiel für Code, den Sie in eingegeben würden Ihrem *RGS* Datei Skript veranschaulicht, wie Sie einen Editor ordnungsgemäß zu registrieren.  
  
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
  
12. Implementieren Sie die kontextbezogene Hilfe an.  
  
     Dadurch können Sie angeben, dass F1-Hilfe und dynamische Hilfefenster für Elemente in einem Editor unterstützen. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Machen Sie ein Automation-Objektmodell aus Ihrem Editor durch die Implementierung der `IDispatch` Schnittstelle.  
  
     Weitere Informationen finden Sie unter [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Stabile Programmierung  
  
- Die Editor-Instanz wird erstellt, wenn es sich bei die IDE Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode. Wenn der Editor über mehrere Ansichten unterstützt `CreateEditorInstance` wird sowohl die Dokumentdaten als auch die dokumentenansichtsobjekten erstellt. Wenn das dokumentendatenobjekt bereits ist zu öffnen, eine Wert ungleich Null `punkDocDataExisting` Wert wird übergeben, um `IVsEditorFactory::CreateEditorInstance`. Die Implementierung der Factory-Editors muss bestimmen, ob ein vorhandenes dokumentendatenobjekt kompatibel ist, indem entsprechende Schnittstellen darauf abgefragt. Weitere Informationen finden Sie unter [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
- Wenn Sie die vereinfachte einbettungsansatz verwenden, implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle.  
  
- Wenn Sie die direkte Aktivierung verwenden möchten, werden implementieren Sie die folgenden Schnittstellen:  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
  > [!NOTE]
  >  Die `IOleInPlaceComponent` Schnittstelle wird verwendet, um OLE 2 das Zusammenführen von Menüs zu vermeiden.  
  
   Ihre `IOleCommandTarget` Implementierung behandelt Befehle wie z. B. **Ausschneiden**, **Kopie**, und **einfügen**. Bei der Implementierung `IOleCommandTarget`, entscheiden Sie, ob Ihre-Editor eine eigene erfordert *VSCT* Datei, um eine eigene Menüstruktur Befehl definieren, oder wenn es von definierten standard-Befehle implementieren kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In der Regel Editoren verwenden und erweitern die IDE Menüs und definieren ihre eigenen Symbolleisten haben. Allerdings ist es häufig erforderlich, für einen Editor, um eine eigene bestimmte Befehle zusätzlich zur Verwendung der IDE-standard-Befehlssatz zu definieren. Als Editor muss deklarieren Sie die standard-Befehle verwendet, wobei Sie neuen Befehle, Kontextmenüs, Menüs der obersten Ebene und Symbolleisten in einem *VSCT* Datei. Wenn Sie eine direkte Aktivierung-Editor erstellen, implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> und definieren Sie die Menüs und Symbolleisten für den Editor in einem *VSCT* Datei anstelle von OLE 2 das Zusammenführen von Menüs.  
  
- Um Menübefehl Versammeln in der Benutzeroberfläche zu verhindern, sollten Sie die vorhandene Befehle vor dem entwickeln neue Befehle in der IDE verwenden. Freigegebenen Befehle in definiert *SharedCmdDef.vsct* und *ShellCmdDef.vsct*. Diese Dateien werden standardmäßig installiert, in das Unterverzeichnis VisualStudioIntegration\Common\Inc Ihre [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Installation.  
  
- `ISelectionContainer` können einzelne und mehrere Auswahl Ausdrücken. Jedes ausgewählte Objekt wird als implementiert eine `IDispatch` Objekt.  
  
- Die IDE implementiert die `IOleUndoManager` als Dienst über eine <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> oder als ein Objekt, das durch instanziiert werden kann <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Die Editor-implementiert die `IOleUndoUnit` Schnittstelle für die einzelnen `Undo` Aktion.  
  
- Es gibt zwei Stellen ein benutzerdefinierter Editor kann Automatisierungsobjekte verfügbar zu machen:  
  
  -   `Document.Object`  
  
  -   `Window.Object`  
  
## <a name="see-also"></a>Siehe auch  
 [Mitwirken Sie am Automatisierungsmodell](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Gewusst wie: Bereitstellen von Kontext für Editoren](../extensibility/how-to-provide-context-for-editors.md)