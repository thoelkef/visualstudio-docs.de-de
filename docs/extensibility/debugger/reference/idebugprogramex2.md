---
title: IDebugProgramEx2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8e26a21e00ff9f0fff664130171a302667ee414
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120961"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Dieser Schnittstelle können die Sitzung Debug-Manager (SDM) Anfügen an ein Programm, und erhalten die Programm-Knoten mit einem Programm verknüpft sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle auf das gleiche Objekt wie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle, um die SDM an ein Programm angefügt werden, während gleichzeitig ermöglicht den Port Lieferanten zum Nachverfolgen von allen Sitzungen angefügt können die Programm. Der benutzerdefinierten Port Lieferanten kann diese Schnittstelle implementieren, wenn er entscheidet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ruft die SDM [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProgram2` Schnittstelle zum Abrufen diese Schnittstelle, um Sitzungen zu verfolgen, die auf Programme angefügt haben.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramEx2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm zu einer Sitzung an.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft die einem Programm zugeordneten Programm Knoten ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist privat zwischen den SDM und das Programm.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)