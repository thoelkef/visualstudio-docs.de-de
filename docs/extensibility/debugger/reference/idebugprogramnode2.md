---
title: IDebugProgramNode2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6f9d58ef5832b70e1f9dbac356eaa242ca2be1ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Diese Schnittstelle stellt ein Programm, das gedebuggt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugging-Modul (DE) oder einen benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um ein Programm darstellen, die gedebuggt werden kann. Diese Schnittstelle wird in der Regel implementiert, auf das gleiche Objekt, implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle. Diese Schnittstelle ist mit registrierten [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] durch Aufrufen von [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) dieser Schnittstelle zurückgegeben. Ein benutzerdefinierten Port Lieferanten empfängt diese Schnittstelle über einen Aufruf von [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Eine Deutschland empfängt diese Schnittstelle über einen Aufruf von [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramNode2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ruft den Namen eines Programms.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ruft den Namen der Hostprozess für eine Anwendung ab.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ruft die System-Prozess-ID für den Prozess, ein Programm hostet.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|ALS VERALTET MARKIERT. DARF NICHT VERWENDET WERDEN.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|ALS VERALTET MARKIERT. DARF NICHT VERWENDET WERDEN. Finden Sie unter der [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle für ein alternativer Ansatz.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ruft den Namen und Bezeichner der de dieses Programm ausführen.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|ALS VERALTET MARKIERT. DARF NICHT VERWENDET WERDEN.|  
  
## <a name="remarks"></a>Hinweise  
 Ruft die Sitzungs-Debug-Manager (SDM) in der Regel [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) beim Abrufen dieser Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)