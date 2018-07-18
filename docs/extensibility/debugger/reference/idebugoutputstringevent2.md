---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac8a2072d801936d8035d5479c7d234082639818
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117120"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) auf dem Sitzungs-Manager (SDM) Ausgabe eine Zeichenfolge gesendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um eine Zeichenfolge zum Senden der **Ausgabe** Fenster der IDE. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt, senden eine Zeichenfolge, die die **Ausgabe** Fenster. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn es an das derzeit debuggte Programm angefügt ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugOutputStringEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ruft die anzeigbare Meldung ab.|  
  
## <a name="remarks"></a>Hinweise  
 In nicht verwaltetem Code kann beispielsweise die Zeichenfolge, die ausgegeben werden stammen, das derzeit debuggte Programm sendet eine Zeichenfolge an die Win32 `OutputDebugString` Funktion. Diese Zeichenfolge ist durch die DE abgefangen und an die SDM als gesendet die `IDebugOutputStringEvent2` Ereignis.  
  
 Verwendung [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) zum Senden einer Nachricht, die eine Antwort des Benutzers erfordert.  
  
 Verwendung [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) eine Fehlermeldung gesendet, die keine Antwort erforderlich ist.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)