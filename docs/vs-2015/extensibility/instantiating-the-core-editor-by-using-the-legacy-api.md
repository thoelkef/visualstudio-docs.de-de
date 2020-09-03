---
title: Instanziieren des Kern Editors mit der Legacy-API | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203913"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Instanziieren des Core-Editors mithilfe der Legacy-API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Editor ist für Text Bearbeitungsfunktionen wie das Einfügen, löschen, kopieren und Einfügen verantwortlich. Diese Funktionen werden mit den von Sprachdiensten bereitgestellten Funktionen kombiniert, z. b. Text Färbung, Einzüge und IntelliSense-Anweisungs Vervollständigung.  
  
 Es gibt drei Möglichkeiten, eine Instanz des Core-Editors zu instanziieren:  
  
- Erstellen Sie explizit eine Instanz des Core-Editors in einem-Fenster.  
  
- Bereitstellen einer Editorfactory, die eine Instanz des Kern-Editors zurückgibt  
  
- Öffnen Sie eine Datei aus der Projekt Hierarchie.  
  
  In den folgenden Abschnitten wird erläutert, wie Sie die Legacy-API verwenden, um den Editor zu instanziieren.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Explizites Öffnen einer Core-Editor-Instanz  
 Beim expliziten Abrufen einer Instanz des Kern-Editors:  
  
- Abrufen eines- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Objekts, das das zu bearbeitende Dokument Datenobjekt enthält.  
  
- Erstellen Sie eine Zeilen orientierte Darstellung des Dokument Datenobjekts, indem Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Schnittstelle aus der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle erstellen.  
  
- Legen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> Sie als Dokument Datenobjekt für eine Instanz der Standard Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Schnittstelle mithilfe der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> Methode fest.  
  
   Hosten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Sie die Instanz <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> mithilfe der-Methode in einer-Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> .  
  
  An dieser Stelle stellt die Anzeige der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle ein Fenster bereit, das eine Instanz des Kern Editors enthält.  
  
  Dies ist jedoch keine sehr nützliche Instanz, da Sie keine Tastenkombinationen oder Zugriff auf Erweiterte Funktionen hat. So erhalten Sie Zugriff auf Tastenkombinationen und erweiterte Features:  
  
- Verwenden <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Sie die-Methode, um einen Sprachdienst und das Dokument Datenobjekt, das der Editor verwendet, zuzuordnen.  
  
- Erstellen Sie entweder Ihre eigenen Tastenkombinationen, oder verwenden Sie den Standardwert des Systems, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Eigenschaften der Objekt Anzeige festlegen. Um dies zu erreichen, müssen Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> Methode mit der- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> Eigenschaft abrufen.  
  
   Zum Abrufen und verwenden nicht standardmäßiger Tastenkombinationen generieren Sie diese mithilfe der vsct-Datei. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Verwenden einer Editorfactory zum Abrufen des Kern-Editors  
 Wenn Sie mit der-Methode einen Kern Editor mit einer Editorfactory implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , führen Sie alle im vorherigen Abschnitt beschriebenen Schritte aus, um einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> mithilfe eines <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Dokument Datenobjekts in einem-Objekt explizit zu hosten <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> .  
  
 Um den Text anzuzeigen, rufen Sie eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Schnittstelle aus dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> -Objekt ab und rufen die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode auf.  
  
 Um dem Editor einen Sprachdienst bereitzustellen, müssen Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode innerhalb der-Methode aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  
  
 Zum Abrufen von Standardtasten Kombinationen verwenden Sie im Gegensatz zum vorherigen Abschnitt den Befehls Kontext, der von der-Methode zurückgegeben wird, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Wenn Sie den Kern-Editor aus der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode abrufen.  
  
 Wenn die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode dieselbe Befehls-GUID wie der Text-Editor zurückgibt, ruft die Instanz des Core-Editors automatisch die Standardtasten Kombinationen ab.  
  
 Allgemeine Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Kern Editors und Registrieren eines Editor Dateityps](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Im Kern-Editor](../extensibility/inside-the-core-editor.md)   
 [Öffnen und Speichern von Projekt Elementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Core-Editors und Registrieren eines Editordateityps](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
