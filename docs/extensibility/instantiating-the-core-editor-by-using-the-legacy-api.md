---
title: Instanziieren die Kern-Editor mit der Legacy-API | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 602adf27a0a165a8919d4be928a330dc3a212cf3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500474"
---
# <a name="instantiate-the-core-editor-by-using-the-legacy-api"></a>Instanziieren Sie die Kern-Editor, indem Sie die legacy-API
Der Editor ist verantwortlich für die Textbearbeitung, die Funktionen, z. B. einfügen, löschen, kopieren und einfügen. Sie kombiniert diese Funktionen mit den Funktionen von Language-Diensten, z. B. Text, Farben, die Einzüge und IntelliSense-Anweisungsvervollständigung bereitgestellt werden.  
  
 Sie können eine Instanz von der Kern-Editor in einer von drei Methoden instanziieren:  
  
-   Erstellen Sie explizit eine Instanz des Kerns Editor in einem Fenster.  
  
-   Geben Sie eine Editorfactory, die eine Instanz der dem kerneditor zurückgibt  
  
-   Öffnen Sie eine Datei, aus der Projekthierarchie.  
  
 In den folgenden Abschnitten beschrieben, wie mithilfe der legacy-API den Editor instanziiert wird.  
  
## <a name="explicitly-open-a-core-editor-instance"></a>Öffnen Sie explizit eine Kern-Editor-Instanz  
 Wenn Sie explizit eine Instanz von der Kern-Editor zu erhalten:  
  
-   Abrufen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> zum Speichern von des dokumentendatenobjekts, das bearbeitet wird.  
  
-   Erstellen Sie eine Zeile mit-Darstellung des dokumentendatenobjekts, durch das Erstellen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> -Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Schnittstelle.  
  
-   Legen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> als das dokumentendatenobjekt für eine Instanz der Standardimplementierung von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Schnittstelle, mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> Methode.  
  
     Host der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> -Instanz in eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> -Schnittstelle mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> Methode.  
  
 An diesem Punkt anzeigen. dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle bietet ein Fenster, das eine Instanz der Kern-Editor enthält.  
  
 Dies ist jedoch keiner Instanz sehr nützlich, da es kein Tastenkombinationen, oder der Zugriff auf Erweiterte Funktionen. So erhalten Sie Zugriff auf Tastenkombinationen und erweiterte Features:  
  
-   Verwenden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode zum Zuordnen von einem Sprachdienst und das dokumentendatenobjekt, das der Editor verwendet.  
  
-   Erstellen Sie eigene Tastenkombinationen, oder verwenden Sie die Standardeinstellung des Systems durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Anzeigeeigenschaften für Objekte. Zu diesem Zweck rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> -Methode mit dem <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> Eigenschaft.  
  
     Um zu erhalten, und nicht standardmäßigen Tastenkombinationen verwenden, generieren sie mithilfe der *VSCT* Datei. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellen (VSCT) Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Wie Sie eine Editor-Factory zu verwenden, um die Kern-Editor zu erhalten.  
 Bei der Implementierung eines Kern-Editors mit einer Editor-Factory mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> -Methode, führen Sie alle Schritte im vorherigen Abschnitt, um explizit zu hosten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> mit einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Dokumentdaten-Objekt, in eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt.  
  
 Um den Text anzuzeigen, erhalten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Schnittstelle aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> Objekt, und rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Um einen Sprachdienst für dem Editor bereitzustellen, rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode innerhalb der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Standardmäßige Tastenkombinationen, im Gegensatz zum vorherigen Abschnitt abgerufen, die Sie verwenden den Befehl-Kontexts, zurückgegeben von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode, die beim Abrufen der Kern-Editor aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode.  
  
 Wenn die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode gibt den gleichen Befehl GUID als Text-Editor, zu die Instanz von der Kern-Editor automatisch erhält standardmäßig Tastenkombinationen.  
  
 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen Sie einen Kern-Editor, und registrieren Sie einen Dateityp-Editor-](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Siehe auch  
 [In der Kern-editor](../extensibility/inside-the-core-editor.md)   
 [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Kern-Editor und registrieren einen Dateityp-Editor-](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)