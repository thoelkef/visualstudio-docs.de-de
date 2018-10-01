---
title: IDebugCoreServer3 | Microsoft-Dokumentation
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
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1c039ccb08f7143112939f9d7880d508bd079a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524893"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugCoreServer3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3).  
  
Diese Schnittstelle bietet Zugriff auf Informationen über den Server, die, den der Prozess ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) dieser Schnittstelle vom Abrufen einer [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle. Ein Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) können diese Schnittstelle auch zurückgeben. Diese Schnittstelle wird meist ein Lieferant benutzerdefinierten Port verwendet, um Programme auf einem Server (lokal oder remote) zu starten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Ruft den Namen des Servers.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Ruft eine benutzerfreundliche Version des Servernamens.|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Teilt bestimmte Debug-Engines automatisch an Prozesse anfügen, wenn die Prozesse starten.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Ruft einen bestimmten Fehlercode ab, wenn automatische anfügen erzeugt einen Fehler.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Erstellt eine Instanz von einer Debug-Engine auf dem Server.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Ruft ein Flag, der angibt, ob der Server auf dem gleichen Computer wie der Aufrufer ist ab.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Ruft einen Wert, der angibt, des Protokolls für die Kommunikation mit dem Server verwendet wird.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deaktiviert alle Anhängen Einstellungen für alle Debug-Engines, die, denen diesem Server bekannt sind, automatische.|  
  
## <a name="remarks"></a>Hinweise  
 Ein benutzerdefinierter Port Lieferant empfängt die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle, die bei einem Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md). Die `IDebugCoreServer3` Schnittstelle kann von dieser Schnittstelle abgerufen werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)

