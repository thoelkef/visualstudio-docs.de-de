---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123917"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Diese Schnittstelle listet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um eine Liste von Strukturen zu bieten, die die aktuelle Aufrufliste beschreibt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio-Aufrufe [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) zum Abrufen dieser Schnittstelle, sobald ein Haltepunkt Ausnahme oder ein Stillstand auftritt in einem Programm, das gerade gedebuggt wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugFrameInfo2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Ruft eine angegebene Anzahl von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in eine Enumerationsfolge.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Überspringt die angegebene Anzahl von [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in eine Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ruft die Anzahl der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in einen Enumerator.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio ruft diese Schnittstelle ab, als der erste Schritt zur Behandlung von ein Haltepunkt, eine Ausnahme oder ein vom Benutzer generierte anhalten, auf das derzeit debuggte Programm. Die Liste der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen darstellt, die aktuelle Aufrufliste, rufen Sie mit der aktuellen Funktionsaufruf am Anfang der Liste und die älteste Funktion am Ende der Liste. Jede `FRAMEINFO` stellt einen Stapelrahmen, der einen Kontext, in dem Ausdrücke ausgewertet werden können, und erläutert, lokale Variablen, dar.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)