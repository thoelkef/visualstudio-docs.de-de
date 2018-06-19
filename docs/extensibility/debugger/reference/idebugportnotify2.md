---
title: IDebugPortNotify2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1874b46e702af49bf8f0a738b9e764f2fa11014
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115176"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Diese Schnittstelle registriert oder hebt die Registrierung ein Programm, das mit dem Port gedebuggt werden kann, ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle zum Hinzufügen und Entfernen von Programmen vom Port unterstützt. Er ist in der Regel implementiert, auf das gleiche Objekt, implementiert die [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugPort2` Schnittstelle gibt diese Schnittstelle. Darüber hinaus einen Aufruf von [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) gibt diese Schnittstelle. Ein Debugmodul sehen diese Schnittstelle als Parameter an [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortNotify2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das gedebuggt werden kann mit dem Port, den es ausgeführt wird.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Hebt die Registrierung eines Programms, das vom Port gedebuggt werden kann, ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Es sei denn, ein Debugport feststellen können, wenn Sie Programme geladen oder entladen wird, muss ein benutzerdefinierten Port Lieferanten diese Schnittstelle implementieren. Alle Programme, die geladen werden, für das Debuggen über einen bestimmten Port werden die Verwendung dieser Schnittstelle nachverfolgt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)