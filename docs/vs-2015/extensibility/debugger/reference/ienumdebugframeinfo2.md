---
title: IEnumDebugFrameInfo2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc5d0fcd97de40826d4cc3815ab621728892f36b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183832"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle listet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um eine Liste von Strukturen zu bereitstellen, die die aktuelle Aufrufliste beschreibt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) um diese Schnittstelle immer einen Haltepunkt zu erhalten, Ausnahme oder ein Stillstand auftritt in einem Programm im Debugmodus befindlichen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugFrameInfo2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Ruft eine angegebene Anzahl von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in einer Enumerationsfolge.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Überspringt eine angegebene Anzahl von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in einer Enumerationsfolge.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ruft die Anzahl der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in einem Enumerator.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio ruft diese Schnittstelle als ersten Schritt zur Behandlung von einen Haltepunkt, Ausnahme oder benutzergeneriertem Pause gedebuggten Programm ab. Die Liste der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen darstellt, die aktuelle Aufrufliste, rufen Sie mit dem aktuellen Funktionsaufruf am Anfang der Liste und die älteste Funktion am Ende der Liste. Jede `FRAMEINFO` stellt einen Stapelrahmen, der ein Kontext, in dem Ausdrücke ausgewertet werden, und lokale Variablen betrachtet, dar.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)

