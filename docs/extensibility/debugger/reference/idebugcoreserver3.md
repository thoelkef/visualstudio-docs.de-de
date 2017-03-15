---
title: "IDebugCoreServer3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "IDebugCoreServer3-Schnittstelle"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle weist den Zugriff auf Informationen über den Server, auf dem der Prozess ausgeführt wird.  
  
## Syntax  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus einer [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)\-Schnittstelle zu erhalten.  Ein Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) kann diese Schnittstelle auch zurückgeben.  Diese Schnittstelle wird am häufigsten für ein benutzerdefiniertes Anschlusslieferanten verwendet, um Programme auf einem Server zu starten \(entweder lokal oder remote\).  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden der [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Ruft den Namen des Servers ab.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Ruft eine benutzerfreundliche Version des Servernamens ab|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Teilt gesagt, das auf Module ermöglichen, Debugsymbolinformationen auf Prozesse automatisch beim Start dieser Prozesse anhängen.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Ruft einen bestimmten Fehlercode ab, wenn das automatische Anhängen fehlschlägt.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Erstellt eine Instanz eines Debugmoduls auf dem Server.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Ruft ein Flag ab, das angibt, ob der Server auf dem gleichen Computer wie der Aufrufer ist.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Ruft einen Wert ab, der das Protokoll angibt, das verwendet wird, um mit dem Server zu kommunizieren.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deaktiviert alle selbstklebenden Einstellungen für alle Debuginformationen Module, die ungefähr Server kennt.|  
  
## Hinweise  
 Ein benutzerdefinierter Port lieferant empfängt die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)\-Schnittstelle für einen Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md).  Die `IDebugCoreServer3`\-Schnittstelle kann von dieser Schnittstelle abgerufen werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)