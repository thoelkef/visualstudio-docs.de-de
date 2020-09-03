---
title: IEnumDebugErrorBreakpoints2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95d001c0072442d07ae12f773a26290a95a2f7f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178472"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle listet die Fehler Haltepunkte auf, die einem ausstehenden Haltepunkt zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle als Teil der Unterstützung von Breakpoints.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio ruft [canbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) auf, um diese Schnittstelle abzurufen, die eine Liste von Haltepunkten darstellt, die nicht gebunden werden können, oder [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) zum Abrufen dieser Schnittstelle, die eine Liste von Haltepunkten darstellt, die nicht gebunden wurden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugErrorBreakpoints2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Ruft eine angegebene Anzahl von Fehler Breakpoints in einer Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl von Fehler Breakpoints in einer enumerationssequenz.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ruft die Anzahl der Fehler Breakpoints in einem Enumerator ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle enthält eine Liste von [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) -Schnittstellen, von denen jeder einen Haltepunkt beschreibt, der nicht gebunden werden konnte, und warum er nicht gebunden werden konnte. Visual Studio verwendet die- `IEnumDebugErrorBreakpoint2` Schnittstelle, um die Breakpoints zu aktualisieren, die in der IDE angezeigt werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Kanbind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [Enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
