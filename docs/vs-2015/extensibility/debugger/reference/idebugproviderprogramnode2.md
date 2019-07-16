---
title: IDebugProviderProgramNode2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a81668d5c45dd4b3363821972914e3f9dc10266a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692214"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle marshallt Programm sammlungsbezogene Schnittstellen über Prozessgrenzen hinweg.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Marshalling Schnittstellen über Prozessgrenzen hinweg zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine `IDebugProgramNode2` Schnittstelle, um diese Schnittstelle zu erhalten. Wenn diese Schnittstelle kann nicht abgerufen werden, unterstützt die DE kein Marshalling von Schnittstellen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird implementiert, wenn die DE aus der zu debuggende Programm wird in einem separaten Prozessbereich ausgeführt wird: z. B. wenn die DE in den Prozessbereich der Visual Studio anstelle von den Prozessbereich der gedebuggten Programm ausgeführt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
