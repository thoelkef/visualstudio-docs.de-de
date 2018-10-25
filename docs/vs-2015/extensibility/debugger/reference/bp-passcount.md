---
title: BP_PASSCOUNT | Microsoft-Dokumentation
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
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: febd0cdb942302332b761d02eca85737a8c7632b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877958"
---
# <a name="bppasscount"></a>BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt die Anzahl und die Bedingungen aus, auf denen ein bedingter Haltepunkt ausgelöst wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```csharp  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## <a name="members"></a>Member  
 `dwPassCount`  
 Die Anzahl der Male auf, um vor dem Auslösen, es auf den Haltepunkt zu übergeben.  
  
 `stylePassCount`  
 Ein Wert aus der [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) -Enumeration, der den Stil der der Haltepunkt gibt an, übergeben Sie die Anzahl.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur.  
  
 Diese Struktur wird ebenfalls übergeben, als Parameter an die[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) und[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)

