---
title: IDebugStackFrame2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d534c5616bd32011fb4e84367911b9a8c1b29ab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986942"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Diese Schnittstelle stellt einen einzelnen Stapelrahmen in einer Aufrufliste, in einem bestimmten Thread dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um einen Stapelrahmen darstellt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) zum Abrufen einer [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Schnittstelle. Rufen Sie [Weiter](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) zum Abrufen einer [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) -Struktur, enthält die `IDebugStackFrame2` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugStackFrame2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Codekontext für diesen Stapelrahmen ab.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentenkontext für diesen Stapelrahmen ab.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ruft den Namen des Stapelrahmens.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ruft eine Beschreibung des Stapelrahmens ab.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ruft eine Darstellung abhängig vom Computer des Bereichs von physischen Adressen, die einen Stapelrahmen zugeordnet.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ruft ein Evaluierungskontext für die ausdrucksauswertung im aktuellen Kontext des einen Stapelrahmen und der Thread ab.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ruft die Sprache, die einen Stapelrahmen zugeordnet.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ruft eine Beschreibung der Eigenschaften einer Stapelrahmen zugeordnet.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Erstellt einen Enumerator für die Stack-Frame-Eigenschaften.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ruft den Thread, der einen Stapelrahmen zugeordnet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird abgerufen, nur, wenn die zu debuggende Programm wird an einem Haltepunkt beendet wurde (entweder durch einen Benutzer festgelegten Haltepunkt oder verursacht eine Ausnahme). Von dieser Schnittstelle Context Ausdruck zum Auswerten von Ausdrücken abgerufen werden kann, eine Liste mit Registrierungen zurückgegeben werden kann, oder die Aufrufliste abgerufen und überprüft werden kann.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)