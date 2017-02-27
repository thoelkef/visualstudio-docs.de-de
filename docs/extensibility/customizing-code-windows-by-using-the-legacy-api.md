---
title: "Anpassen von Code Windows mit der Legacy-API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - Code-Fenster"
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Anpassen von Code Windows mit der Legacy-API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Codefenster wird ein Dokument Window\-Objekt, das eine oder mehrere Textansichten unterstützt. Die genauen Funktionen der ein Codefenster, die die zugeordnete Sprache\-Dienst abhängig ist. Im Modus Multiple Document Interface \(MDI\) ist im Codefenster der untergeordneten MDI\-Rahmens.  
  
 Code\-Fenster von Sprachdienste gesteuert werden, und jede Sprachdienst kann einen eigenen Code\-Fenster\-Manager bereitstellen. Dadurch wird der Sprachdienst eigene Zusatzelemente Codefenster wie Wellenlinien, Farbgebung und mehr hinzu. Weitere Informationen zum Erstellen eines Fensters Core finden Sie unter [Instanziieren die Core\-Editor mithilfe der Legacy\-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Ein Codefenster ist ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> \-Objekt, das eine Textansicht und alle Details, die in dem Objekt platziert wurde. Wenn Sie das Codefenster während der Instanziierung des Kern\-Editor erstellen, kann Ihre Sprachdienst Anfügen einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> in das Codefenster wird wie in der folgenden Abbildung gezeigt.  
  
 ![CodeWindow&#45;Grafik](../extensibility/media/vscodewindow.png "vscodewindow")  
Codefenster  
  
 Der Sprachdienst den Fenster\-Manager implementiert und ist verantwortlich für die Verwaltung von Details, z. B. eine Dropdownliste angezeigt. Ruft der Code\-Fenster die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Methode während der Initialisierung der Code\-Fenster. Wenn dieser Aufruf erfolgt, kann der Sprachdienst hinzufügen, eine Dropdownliste oder einer Symbolleiste \(<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>\) in das Codefenster.  
  
## In diesem Abschnitt  
 `Customizing Code Windows by Using the Legacy API`  
 Erläutert das Code\-Fenster mit der legacy\-API anpassen.  
  
 [Gewusst wie: Hosten ein Editors in einem anderen Editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Erläutert, wie einen zweiten Redakteur in einem Editor\-Fenster zu hosten.  
  
 [Gewusst wie: Ereignisse auszulösen, wenn der Editor den Fokus verliert.](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Erläutert, wie ein Dokument Datenobjekt eine Dokumentenansicht an.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Instanziieren die Core\-Editor mithilfe der Legacy\-API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Zugreifen auf Dietext Ansicht mithilfe der Legacy\-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)