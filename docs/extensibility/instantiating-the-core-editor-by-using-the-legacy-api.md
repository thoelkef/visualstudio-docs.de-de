---
title: "Instanziieren die Core-Editor mithilfe der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "legacy - Editor instanziieren Editoren [Visual Studio SDK]"
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Instanziieren die Core-Editor mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Editor ist verantwortlich für die Textbearbeitung Funktionen, z. B. einfügen, löschen, kopieren und einfügen. Es kombiniert diese Funktionen, mit denen von Sprachdienste wie Text Färbung, Einzug und IntelliSense\-Anweisungsabschluss bereitgestellt.  
  
 Sie können eine Instanz des Editors Core in eine von drei Arten instanziieren:  
  
-   Erstellen Sie explizit eine Instanz des Kerns Editor in einem Fenster.  
  
-   Geben Sie eine Editorfactory die eine Instanz des Editors Core zurückgibt  
  
-   Öffnen Sie eine Datei aus der Projekthierarchie.  
  
 In den folgenden Abschnitten erläutern die legacy\-API verwenden, um den Editor zu instanziieren.  
  
## Öffnen explizit eine Core\-Editor\-Instanz  
 Wenn eine Instanz des Editors Core explizit zu erhalten:  
  
-   Abrufen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Aufnahme das Datenobjekt Dokument bearbeitet wird.  
  
-   Erstellen Sie eine Zeile mit Darstellung des Dokument\-Objekts, durch das Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> \-Schnittstelle aus dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle.  
  
-   Legen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> als Datenobjekt Dokument für eine Instanz der Standardimplementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Schnittstelle, mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> Methode.  
  
     Host der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> \-Instanz in eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> \-Schnittstelle mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> Methode.  
  
 An diesem Punkt Anzeigen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle stellt ein Fenster, das eine Instanz des Editors Core enthält.  
  
 Dies ist jedoch keine Instanz sehr nützlich, da keine Tastenkombinationen verfügen, oder der Zugriff auf Erweiterte Funktionen. So erhalten Sie Zugriff auf die Tastenkombinationen und erweiterte Funktionen:  
  
-   Verwenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode zum Zuweisen eines Sprachdiensts und das Dokumentobjekt für Daten, die der Editor verwendet.  
  
-   Erstellen Sie eigene Tastenkombinationen, oder verwenden Sie die Standardeinstellung des Systems durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekte Eigenschaften anzeigen. Rufen Sie hierzu die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> \-Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> Eigenschaft.  
  
     Um zu erhalten, und nicht standardmäßigen Tastenkombinationen verwenden, generieren sie mithilfe der VSCT\-Datei. Weitere Informationen finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Wie Sie eine Editorfactory die Core\-Editor abrufen  
 Beim Implementieren eines Core\-Editors mit einer Factory\-Editor mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \-Methode, führen Sie alle Schritte im vorherigen Abschnitt explizit hosten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> verwenden ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Dokumentdaten\-Objekt, in ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt.  
  
 Um den Text anzuzeigen, erhalten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> \-Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Objekt, und rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Um eine Sprache in dem Editor bereitzustellen, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode innerhalb der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Um Tastenkombinationen, im Gegensatz zum vorherigen Abschnitt zu ermitteln, verwenden Sie den Befehlskontext zurückgegebene die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode beim Abrufen des Core\-Editors aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \-Methode gibt den gleichen Befehl GUID als Text\-Editor, die Instanz des Editors Core automatisch erhält standardmäßig Tastenkombinationen.  
  
 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Kern\-Editors, und registrieren einen Dateityp\-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## Siehe auch  
 [In der Core\-Editor](../extensibility/inside-the-core-editor.md)   
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Kern\-Editors, und registrieren einen Dateityp\-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)