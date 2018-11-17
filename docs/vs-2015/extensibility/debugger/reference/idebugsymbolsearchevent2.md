---
title: IDebugSymbolSearchEvent2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14c1272aee4197a37ba03c62028afcbb222fa5df
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778630"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird von der Debug-Engine (DE) gesendet, um anzugeben, dass die Debugsymbole für ein Modul, das im Debugmodus befindlichen geladen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um zu melden, dass es sich bei einem Modul die Symbole geladen wurden. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet dieses Ereignisobjekt zum Berichten des Moduls Symbole geladen wurden. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn diese an die zu debuggende Programm wird angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die `IDebugSymbolSearchEvent2` Schnittstelle verfügbar macht, die folgende Methode.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Ruft Informationen zu den Ergebnissen einer Suche Symbol ab.|  
  
## <a name="remarks"></a>Hinweise  
 Dieses Ereignis wird gesendet werden, auch wenn die Symbole konnte nicht geladen werden. Aufrufen von `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` , kann der Handler, der dieses Ereignis, um zu bestimmen, ob das Modul tatsächlich keine Symbole.  
  
 Visual Studio verwendet dieses Ereignis in der Regel beim Aktualisieren des Status der geladenen Symbole in der **Module** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

