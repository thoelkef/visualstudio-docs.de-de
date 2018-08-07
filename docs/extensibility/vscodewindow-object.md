---
title: VSCodeWindow-Objekt | Microsoft-Dokumentation
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
ms.openlocfilehash: b9ef7d4b190a9b2c1a487fb70df33726ca9b3ed4
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586273"
---
# <a name="vscodewindow-object"></a>VSCodeWindow-Objekt
Ein Code-Fenster ist eine spezielle Dokumentfenster, der eine oder mehrere Textansichten, in der Regel enthalten kann die <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
 Aus Sicht der Systemarchitektur wird im Code-Fenster ein Dokumentfenster, das innerhalb eines Fensterrahmens. Konkret wird im Code-Fenster einfach ein Dokumentfenster mit zusätzlichen Funktionen. Im Modus Multiple Document Interface (MDI) ist im Code-Fenster den MDI-Child-Rahmen. Weitere Informationen finden Sie unter [Anpassen von Fenstern des Code mit der legacy-API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Die folgende Tabelle enthält die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> Objekt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Stellt einen generischen Mechanismus suchen einen Dienst, den ein global eindeutiger Bezeichner (GUID) identifiziert.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Stellt mehrere Document Interface (MDI) untergeordnetes Element, das eine oder mehrere Codeansichten enthält.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Füllt einen Fensterrahmen.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Abbildungen bearbeiten](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)