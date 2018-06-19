---
title: IDebugStackFrame2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efa6c917e5a59c291d07757b52fab4fe8aa7b0ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122092"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Diese Schnittstelle stellt einen einzelnen Stapelrahmen in einer Aufrufliste in einem bestimmten Thread dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um einen Stapelrahmen darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) zum Abrufen einer [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) Schnittstelle. Rufen Sie [Weiter](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) zum Abrufen einer [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) -Struktur, enthält die `IDebugStackFrame2` Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugStackFrame2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Codekontext für diesen Stapelrahmen ab.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentenkontext für diesen Stapelrahmen ab.|  
|[getName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ruft den Namen des Stapelrahmens ab.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ruft eine Beschreibung des Stapelrahmens ab.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ruft eine rechnerabhängige Darstellung des Bereichs von physischen Adressen, die einen Stapelrahmen zugeordnet.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ruft einen Evaluierungskontext für die Auswertung von Ausdrücken im aktuellen Kontext einer Stapelrahmen und die Threads ausführt.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ruft die Sprache, die einen Stapelrahmen zugeordnet.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ruft eine Beschreibung der Eigenschaften, die einen Stapelrahmen zugeordnet.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Erstellt einen Enumerator für die Stack-Frame-Eigenschaften.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ruft den Thread, der einen Stapelrahmen zugeordnet.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird abgerufen, nur, wenn das Programm, das gerade gedebuggt wird an einem Haltepunkt angehalten wurde (entweder durch einen Benutzer festgelegten Haltepunkt oder verursacht eine Ausnahme). Von dieser Schnittstelle eine Ausdruckskontext abgerufen werden kann, um Ausdrücke ausgewertet werden, eine Liste mit Registrierungen zurückgegeben werden kann oder die Aufrufliste abgerufen und untersucht werden kann.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)