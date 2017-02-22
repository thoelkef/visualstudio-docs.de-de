---
title: "IDebugProgramNode2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2"
helpviewer_keywords: 
  - "IDebugProgramNode2-Schnittstelle"
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Programm, das gedebuggt werden kann.  
  
## Syntax  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Modul \(Debug\) DE oder einen benutzerdefinierten Port lieferant implementiert diese Schnittstelle, um ein Programm, das gedebuggt werden kann.  Diese Schnittstelle wird normalerweise im selben Objekt implementiert, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle implementiert.  Diese Schnittstelle ist mit [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] registriert, indem [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)aufruft.  
  
## Hinweise für Aufrufer  
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) Aufruf, um diese Schnittstelle zurückzugeben.  Ein benutzerdefinierter Port lieferant empfängt diese Schnittstelle durch einen Aufruf von [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md).  DE empfängt diese Schnittstelle durch einen Aufruf von [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProgramNode2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Ruft den Namen eines Programms ab.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Ruft den Namen des Prozesses hostings ein Programm ab.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Ruft die prozess\-id Prozess für das Hosten eines Programms ab.|  
|[GetHostMachineName\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|VERALTET.  NOT TUN USE.|  
|[Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|VERALTET.  NOT TUN USE.  Zeigen Sie die [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)\-Schnittstelle für einen alternativen Ansatz.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Ruft den Namen und Bezeichner DEs running dieses Programm ab.|  
|[DetachDebugger\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|VERALTET.  NOT TUN USE.|  
  
## Hinweise  
 Der Debuginformationen Manager der Sitzung \(SDM\) ruft in der Regel [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) an, die zum Abrufen dieser Schnittstelle.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)