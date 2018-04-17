---
title: VSCodeWindow Objekt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2b1d85eea974e67ae37f8d4d5bfd7aa0069e92b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="vscodewindow-object"></a>VSCodeWindow-Objekt
Codefenster ist eine spezielle Dokumentfenster, die eine oder mehrere Textansichten, in der Regel enthalten kann die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 Architektonisch, ist das Codefenster einem Dokumentfenster angezeigt, die innerhalb eines Fensterrahmens. Das Codefenster ist funktionell einfach in einem Dokumentfenster mit zusätzlichen Funktionen. Im Modus Multiple Document Interface (MDI) ist das Codefenster der untergeordneten MDI-Rahmens an. Weitere Informationen finden Sie unter [Codefenster über die Legacy-API anpassen](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Die folgende Tabelle enthält die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Mechanismus suchen einen Dienst, den ein global eindeutiger Bezeichner (GUID) identifiziert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt mehrere Document Interface (MDI) untergeordnetes Element mit einer oder mehreren Ansichten von Code dar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen an.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Bearbeiten von Zahlen](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)