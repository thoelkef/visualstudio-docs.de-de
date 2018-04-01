---
title: IEnumDebugThreads2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b03d9adbec92986ea8a1cf0f589bd451107a611f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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