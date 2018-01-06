---
title: IDebugQueryEngine2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugQueryEngine2
helpviewer_keywords: IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a54b6f6ab5667993553074f1ca2511a544a0eaea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Dieser Schnittstelle können die Sitzung mit dem Debug-Manager (SDM) abzurufen, eine Schnittstelle, die Debugging-Modul (DE) darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle für die Objekte, die am häufigsten verwendeten DE-Schnittstellen implementieren (z. B. [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), und [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) in Reihenfolge Zugriff auf die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle des DE selbst.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) eine typische DE-Schnittstelle zum Abrufen dieser Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugQueryEngine2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ruft eine benutzerdefinierte Debug-Modul (DE)-Schnittstelle ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird in der Regel implementiert, in das Objekt, implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle um unterstützen Kausalität sortiert schrittweises Durchlaufen von Funktionen, d. h., wenn der Debugger aus einer Funktion stepping wird der Next-Funktion zum Ausführen der previous-Funktion auf dem Stapel jedoch eine Funktion in einem anderen Thread vollständig möglicherweise nicht. Eine Definition von "Kausalität" finden Sie in der [Visual Studio-Debugger-Glossar](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)