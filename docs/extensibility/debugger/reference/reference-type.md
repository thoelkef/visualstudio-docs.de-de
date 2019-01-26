---
title: REFERENCE_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af30f7092c36edfa706664e97bf988255bcfa44c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951507"
---
# <a name="referencetype"></a>REFERENCE_TYPE
Gibt den Verweistyp.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```csharp  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## <a name="members"></a>Member  
 REF_TYPE_WEAK  
 Gibt einen schwachen Verweis an. Können nicht kombiniert werden, mit `REF_TYPE_STRONG`.  
  
 REF_TYPE_STRONG  
 Gibt einen starken Verweis an. Können nicht kombiniert werden, mit `REF_TYPE_WEAK`.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet als die `dwRefType` Mitglied der [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Struktur.  
  
 Übergeben als Parameter an die [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)