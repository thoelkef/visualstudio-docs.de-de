---
title: IDebugCanStopEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696673"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um den Sitzungs-Debug-Manager (SDM) zu Fragen, ob er am aktuellen Code Speicherort angehalten werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle, um das Durchlaufen des Quellcodes zu unterstützen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden (SDM verwendet [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die- `IDebugEvent2` Schnittstelle).  
  
 Die Implementierung dieser Schnittstelle muss den SDM-Befehl [canstoppt](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) an die Debug-Engine übermitteln. Dies kann z. b. mit einer Nachricht erfolgen, die an den Meldungs Behandlungs Thread der Debug-Engine gesendet wurde, oder das Objekt, das diese Schnittstelle implementiert, kann einen Verweis auf die Debug-Engine enthalten und einen Rückruf in die Debug-Engine mit dem an übergeben `IDebugCanStopEvent2::CanStop` .  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die de kann diese Methode jedes Mal senden, wenn die de aufgefordert wird, die Ausführung fortzusetzen, und die de den Code schrittweise durchläuft. Dieses Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von SDM beim Anfügen an das gedestete Programm bereitgestellt wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugCanStopEvent2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Ruft den Grund für dieses Ereignis ab.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Gibt an, ob das Programm, das gedebuggt wird, an der Position dieses Ereignisses angehalten werden soll (und ein Ereignis senden soll, das den Grund für das Beenden beschreibt), oder die Ausführung einfach|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Ruft den Dokument Kontext ab, der den Speicherort dieses Ereignisses beschreibt.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Ruft den Code Kontext ab, der den Speicherort dieses Ereignisses beschreibt.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird von der de gesendet, wenn der Benutzer eine Funktion durchführt und die Datei keine Debuginformationen findet oder wenn die Debuginformationen vorhanden sind, aber der de-Code nicht weiß, ob der Quellcode für diese Position angezeigt werden kann.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
