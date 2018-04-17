---
title: IEnumDebugThreads2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3405a8ab52591e79f5a865016b68c69c61e6cf8b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Diese interfac genannt Listet die Threads in der aktuellen Debugsitzung ausgeführt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle, um eine Liste der Threads in einem Programm darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) beim Abrufen dieser Schnittstelle, die eine Liste aller Threads in alle Programme, die in einem Prozess darstellt. Rufen Sie [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) beim Abrufen dieser Schnittstelle, die eine Liste der Threads, die in einem Programm darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugThreads2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Ruft eine angegebene Anzahl von Threads in die Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Überspringt eine angegebene Anzahl von Threads in einer Enumerationsfolge an.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Setzt ein Enumerationsfolge auf den Anfang zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumeration Status als aktueller Planer enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ruft die Anzahl der Threads in einen Enumerator ab.|  
  
## <a name="remarks"></a>Hinweise  
 Visual Studio in der Regel ruft diese Schnittstelle zum Aktualisieren der **Threads** Fenster auch hinsichtlich den ersten Thread, der die Liste zu erhalten, für den Aufruf [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Fortfahren](../../../extensibility/debugger/reference/idebugprocess3-continue.md), und [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Fortsetzen](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Führen Sie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)