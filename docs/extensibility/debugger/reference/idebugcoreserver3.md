---
title: IDebugCoreServer3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9456ddbe7588217e4864f6f8c8b994bc9323ab76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Diese Schnittstelle ermöglicht Zugriff auf Informationen über den Server, den der Prozess ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) beim Abrufen dieser Schnittstelle aus einem [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle. Ein Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) kann diese Schnittstelle auch zurückgeben. Diese Schnittstelle wird durch einen benutzerdefinierten Port Lieferanten am häufigsten verwendet, um Programme auf einem Server (lokal oder remote) zu starten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Ruft den Namen des Servers ab.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Ruft eine benutzerfreundliche Version des Servernamens.|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Weist bestimmten Debugmodule für Prozesse, die automatisch angefügt wird, wenn diese Prozesse starten.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Ruft einen bestimmten Fehlercode ab, wenn automatische anfügen erzeugt einen Fehler.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Erstellt eine Instanz von Debugging-Modul auf dem Server.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Ruft ein Flag, der angibt, ob der Server auf demselben Computer wie der Aufrufer ab.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Ruft einen Wert, der angibt, des Protokolls für die Kommunikation mit dem Server verwendet wird.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deaktiviert alle Anhängen Einstellungen für alle Debugmodule, denen diesem Server kennt automatische.|  
  
## <a name="remarks"></a>Hinweise  
 Ein benutzerdefinierten Port Lieferanten empfängt die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle bei einem Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md). Die `IDebugCoreServer3` Schnittstelle kann von dieser Schnittstelle abgerufen werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)