---
title: IDebugPendingBreakpoint2::Bind | Microsoft-Dokumentation
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
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd8ab4846796e872cc7de97e82efa719405d99c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520816"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPendingBreakpoint2::Bind](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpendingbreakpoint2-bind).  
  
Wird dieser ausstehenden Haltepunkt an einem oder mehreren Code-Speicherorten gebunden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```csharp  
int Bind();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Haltepunkt gelöscht wurde.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Methode aufgerufen wird, sollten eine Debug-Engine (DE) versuchen, diese ausstehenden Haltepunkt auf alle Speicherorte von Code zu binden, die mit übereinstimmen.  
  
 Nach der Rückgabe dieser Methode benötigt der Aufrufer Ereignisse, die angibt, dass der ausstehenden Haltepunkt gebunden wurde oder fehlerhaft. bevor die Annahme getroffen ist, die Aufrufe zu warten, bis die [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)-Methoden aller Haltepunkte gebunden oder Fehler, bzw. Listet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)

