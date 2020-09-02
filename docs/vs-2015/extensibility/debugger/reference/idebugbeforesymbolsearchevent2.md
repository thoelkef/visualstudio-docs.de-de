---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 26a8d7b28528a79a925207e1ee3794fcbb4ca1d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423516"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die Debug-Engine (de) sendet diese Schnittstelle an den Sitzungs-Debug-Manager (SDM), um die Status leisten Nachricht während der Symbol Auslastung festzulegen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBeforeSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die de implementiert diese Schnittstelle, wenn Sie die Status leisten Nachricht bei Symbol Ladevorgängen festlegen muss. Diese Schnittstelle wird nur von Debug-engines implementiert, die mit oder einem Teil von Skript Interpretern funktionieren. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet **QueryInterface** für den Zugriff auf die **IDebugEvent2** -Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, wenn es die Status leisten Nachricht während der Symbol Auslastung festlegen muss. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBeforeSymbolSearchEvent2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Ruft den Namen des Moduls ab, das gerade deentschlgt wird.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
