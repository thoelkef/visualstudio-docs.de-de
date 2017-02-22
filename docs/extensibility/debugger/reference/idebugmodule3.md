---
title: "IDebugModule3 | Microsoft Docs"
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
  - "IDebugModule3"
helpviewer_keywords: 
  - "IDebugModule3-Schnittstelle"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Modul dar, der alternative Speicherorte von Symbolen und JustMyCode\-Zuständen unterstützt.  
  
## Syntax  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um alternative Speicherorte von Symbolen zu unterstützen und mit JustMyCode\-Zuständen arbeiten \(siehe [Glossar für Visual Studio\-Debugger](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) für eine Definition von „JustMyCode“\).  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) gibt diese Schnittstelle zurück.  DE sendet die [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)\-Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\) mithilfe der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)\-Methode.  Außerdem wird ein Aufruf [QueryInterface](/visual-cpp/atl/queryinterface) auf einer [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)\-Schnittstelle wird von dieser Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden der [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|["Getsymbolinfo"](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Gibt eine Liste von Pfaden zurück, die nach Symbolen und die Ergebnisse eines Pfads gegesucht gefunden werden.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Lädt und initialisiert Symbole für das aktuelle Modul.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Gibt das Flag zurück, die angibt, ob das Modul Benutzercode darstellt.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Gibt an, ob das Modul als Benutzercode betrachtet werden soll oder nicht.|  
  
## Hinweise  
 Visual Studio stellt der typische Nutzer dieser Schnittstelle.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)