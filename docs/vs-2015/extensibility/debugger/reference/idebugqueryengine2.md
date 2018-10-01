---
title: IDebugQueryEngine2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f80e8b44326cb082c8f6428365bad2575c317da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511959"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugQueryEngine2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugqueryengine2).  
  
Diese Schnittstelle kann die Sitzung mit dem Debug-Manager (SDM) rufen Sie eine Schnittstelle, die die Debug-Engine (DE) darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle für die Objekte, die die am häufigsten verwendeten DE-Schnittstellen zu implementieren (z. B. [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), und [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) in Auftrag Zugriff auf die [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle des DE selbst.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) an einer typischen DE-Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugQueryEngine2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ruft einen benutzerdefinierten Debug-Engine (DE)-Schnittstelle ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird in der Regel implementiert, in das Objekt, implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle zur Unterstützung von Kausalität geordnete Durchlaufen von Funktionen, d. h., wenn der Debugger aus einer Funktion, schrittweise Ausführung ist die die Next-Funktion zum Ausführen der previous-Funktion auf dem Stapel jedoch eine Funktion in einem anderen Thread vollständig möglicherweise nicht. Eine Definition von "Kausalität" finden Sie in der [Visual Studio-Debugger-Glossar](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

