---
title: IDebugPortEx2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: fa36bf7ae96058c4eb7c0462114af50fa08af656
ms.lasthandoff: 04/05/2017

---
# <a name="idebugportex2"></a>IDebugPortEx2
Dieser Schnittstelle können die Sitzung (SDM)-Manager-Steuerelement die Programme und Prozesse, die an einem Port zu debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ruft die SDM [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugPort2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortEx2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Startet eine ausführbare Datei an.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Setzt die Ausführung eines Prozesses.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Beendet einen Prozess an.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ruft die Prozess-ID des Ports selbst ab.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ruft ein Programm mit einem Programm Knoten verknüpft sind.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist normalerweise privat zwischen den SDM und den benutzerdefinierten Port Lieferanten.  
  
 Falls gewünscht, kann ein Debugging-Modul (DE) für diese Schnittstelle auf Suchen der [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle übergeben, um [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) und [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) , das Programm zu starten. Dies ist nicht erforderlich, allerdings kann und einer bereitgestellten Kompatibilitätsrichtlinie nach Belieben tun können, um das Programm für die Anforderung zu starten muss.  
  
## <a name="requirements"></a>Anforderungen  
 Header: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
