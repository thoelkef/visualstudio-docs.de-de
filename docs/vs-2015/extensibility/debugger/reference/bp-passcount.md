---
title: BP_PASSCOUNT | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT
helpviewer_keywords:
- BP_PASSCOUNT structure
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b99cbd777755a9a48869299b5cea523ecacbb4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153376"
---
# <a name="bp_passcount"></a>BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt die Anzahl und die Bedingungen, auf die ein bedingter Breakpoint ausgelöst wird.  
  
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
 Gibt an, wie oft über den Haltepunkt übergeben werden soll, bevor es ausgelöst wird.  
  
 `stylePassCount`  
 Ein Wert aus der [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) Enumeration, der den Stil der Breakpoint-Durchlauf Anzahl angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur ist ein Member der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -Struktur.  
  
 Diese Struktur wird auch als Parameter an die[setpasscount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) -Methode und die[setpasscount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) -Methode übergeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [Setpasscount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [Setpasscount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)
