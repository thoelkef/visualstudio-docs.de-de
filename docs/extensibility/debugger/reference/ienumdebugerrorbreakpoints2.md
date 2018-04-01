---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 072068a252214fdf9a2542b88bba94a1b12bcffa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Diese Schnittstelle listet Fehler Haltepunkte ein ausstehender Haltepunkt zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , rufen Sie diese Schnittstelle stellt eine Liste von Breakpoints, die gebunden werden, oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) beim Abrufen dieser Schnittstelle, die eine Liste der Haltepunkte darstellt. wurden nicht gebunden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugErrorBreakpoints2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Ruft eine angegebene Anzahl von Fehler Haltepunkte in einem Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl von Fehler Haltepunkte in einem Enumerationsfolge an.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ruft die Anzahl der Fehler Haltepunkte in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle enthält eine Liste der [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Schnittstellen, von denen jede einen Haltepunkt beschreibt, konnte nicht gebunden werden, und warum er konnte nicht gebunden werden. Visual Studio verwendet die `IEnumDebugErrorBreakpoint2` Schnittstelle zum Aktualisieren von Breakpoints in der IDE angezeigt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)