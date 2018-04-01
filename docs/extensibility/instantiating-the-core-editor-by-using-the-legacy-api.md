---
title: Instanziieren den Core-Editor mithilfe der Legacy-API | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 29
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e508bda0b22c798246b0f6abf4dfb03c41a92d6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Instanziieren den Core-Editor mithilfe der Legacy-API
Der Editor ist verantwortlich für die Textbearbeitung Funktionen, z. B. einfügen, löschen, kopieren und einfügen. Sie kombiniert diese Funktionen, mit denen von Sprache-Diensten, z. B. Farben für Text, Einzug und IntelliSense-Anweisungsvervollständigung bereitgestellt werden.  
  
 Sie können eine Instanz des Editors Core in einer von drei Methoden instanziieren:  
  
-   Erstellen Sie explizit eine Instanz des Kerns Editor in einem Fenster.  
  
-   Geben Sie eine Editorfactory die eine Instanz des Editors Core zurückgibt  
  
-   Öffnen Sie eine Datei aus der Projekthierarchie.  
  
 In den folgenden Abschnitten wird erläutert, wie auf die legacy-API verwenden, um den Editor zu instanziieren.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Öffnen explizit eine Core-Editor-Instanz  
 Wenn Sie eine Instanz des Editors Core explizit abrufen zu können:  
  
-   Abrufen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zum Speichern der dokumentdatenobjekt bearbeitet wird.  
  
-   Erstellen Sie eine Zeile mit Repräsentation der dokumentdatenobjekt durch das Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> -Schnittstelle aus dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle.  
  
-   Legen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> als das dokumentdatenobjekt für eine Instanz der Standardimplementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Schnittstelle, mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> Methode.  
  
     Host der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> -Instanz in eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> -Schnittstelle mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> Methode.  
  
 An diesem Punkt Anzeigen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle stellt ein Fenster mit einer Instanz des Editors Core.  
  
 Allerdings ist dies keine Instanz sehr nützlich, da es nicht Tastenkombinationen haben, oder der Zugriff auf Erweiterte Funktionen. So erhalten Sie Zugriff auf Tastenkombinationen und erweiterten Funktionen:  
  
-   Verwenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode, um einen Sprachdienst und das Dokumentobjekt für Daten, die der Editor verwendet zuzuordnen.  
  
-   Erstellen Sie eine eigene Tastenkombinationen, oder verwenden Sie den System-Standardwert durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Anzeigeeigenschaften für Objekte. Rufen Sie hierzu die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> Methode mit der <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> Eigenschaft.  
  
     Zum Abrufen und nicht standardmäßigen Tastenkombinationen verwenden, generieren Sie mithilfe der VSCT-Datei. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Gewusst wie: eine Editorfactory zu verwenden, um die Core-Editor zu erhalten.  
 Bei der Implementierung eines Core-Editors mit einer Factory-Editor mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> -Methode, befolgen Sie alle Schritte im vorherigen Abschnitt zum Hosten explizit ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> mit eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Dokumentdaten-Objekt, in ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt.  
  
 Um den Text anzuzeigen, erhalten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Schnittstelle aus dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Objekt, und rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Rufen Sie einen Sprachdienst, um den Editor bereitzustellen, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode innerhalb der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Um Tastenkombinationen im Gegensatz zum vorherigen Abschnitt zu ermitteln, die Sie verwenden des Befehlskontext zurückgegebenes der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode beim Abrufen des Core-Editors aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methodenrückgabe denselben Befehl GUID als Text-Editor, die Instanz des Editors Core automatisch erhält standardmäßig Tastenkombinationen.  
  
 Allgemeine Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Core-Editor, und registrieren einen Dateityp-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Siehe auch  
 [In der Core-Editor](../extensibility/inside-the-core-editor.md)   
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Kern-Editors, und registrieren einen Dateityp-Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)