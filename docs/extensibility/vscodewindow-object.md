---
title: "VSCodeWindow-Objekt | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSCodeWindow"
helpviewer_keywords: 
  - "Ansichten [Visual Studio SDK] VSCodeWindow-Objekt"
  - "VsCodeWindow-Objekt"
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# VSCodeWindow-Objekt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein Codefenster ist ein spezieller Dokumentfenster, das eine oder mehrere Textansichten, in der Regel enthalten kann die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 Das Codefenster ist aufseiten ein Dokumentfenster, die in einem Frame Fenster befindet. Die Funktion ist das Codefenster einfach ein Dokumentfenster mit zusätzlichen Funktionen. Im Modus Multiple Document Interface \(MDI\) ist im Codefenster der untergeordneten MDI\-Rahmens. Weitere Informationen finden Sie unter [Anpassen von Code Windows mit der Legacy\-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Die folgende Tabelle enthält die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Zugriff\-Mechanismus, um einen Dienst zu suchen, den ein global eindeutiger Bezeichner \(GUID\) identifiziert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt mehrere Document Interface \(MDI\) untergeordnetes Element mit einer oder mehreren Codeansichten dar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Figures Edit](http://msdn.microsoft.com/de-de/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)