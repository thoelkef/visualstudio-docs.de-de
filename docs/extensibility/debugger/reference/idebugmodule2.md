---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "IDebugModule2-Schnittstelle"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt, Modul\-dass ist ein ausführbares Einheit von Programm\-solchen als DLL dar.  
  
## Syntax  
  
```  
IDebugModule2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um ein Modul darzustellen und den Zugriff auf Informationen über dieses Modul bereitzustellen.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) gibt diese Schnittstelle zurück.  DE sendet die [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)\-Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\) mithilfe der [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)\-Methode.  
  
 Diese Schnittstelle kann in einer [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur \(die ebenfalls durch den Aufruf zurückgegebenen [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)zurückgegeben wurde\).  
  
 [Weiter](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) gibt auch diese Schnittstelle zurück \([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) gibt die [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)\-Schnittstelle zurück.\)  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugModule2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ruft [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) ab, das dieses Modul beschreibt.|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|VERALTET.  NOT TUN USE.  Lädt die Symbole für dieses Modul.|  
  
## Hinweise  
 Modul **Module** Informationen können im Fenster der IDE angezeigt werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)