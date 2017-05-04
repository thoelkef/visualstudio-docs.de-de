---
title: "IApplicationDebuggerUI-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IApplicationDebuggerUI-Schnittstelle"
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI-Schnittstelle
Wird von der Debuggerintegrierte Entwicklungsumgebung \(IDE\) \(zusätzlich zu `IApplicationDebugger`\) von einer externen Komponente mehr Kontrolle über die Benutzeroberfläche des Debuggers zu geben.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IApplicationDebuggerUI`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Setzt das Fenster, das das angegebene enthält, debuggen Dokument zur oben in der Debuggerbenutzeroberfläche.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Setzt das Fenster, das den Kontext des bestimmten Dokuments zur oben in der Debuggerbenutzeroberfläche enthält und führt das Fenster den Kontext aus.|