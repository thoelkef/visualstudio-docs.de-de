---
title: BP_CONDITION | Microsoft-Dokumentation
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
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e42bd7343100a82d88ac78890483fd095f7065b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813231"
---
# <a name="bpcondition"></a>BP_CONDITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt die Bedingungen, unter denen ein Haltepunkt ausgelöst wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```csharp  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## <a name="members"></a>Member  
 `pThread`  
 Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den aktiven Thread für die Anwendung darstellt, die den Haltepunkt enthält.  
  
 `styleCondition`  
 Ein Wert aus der [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) Enumeration, der dieser Bedingung für Haltepunkt beschreibt.  
  
 `bstrContext`  
 Die Position des Haltepunkts.  
  
 `bstrCondition`  
 Die Bedingung der Auslösung des Haltepunkts.  
  
 `nRadix`  
 Die Basis zum Auswerten von numerische Informationen verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.  
  
 Diese Struktur wird ebenfalls übergeben, als Parameter an die [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) und [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)

