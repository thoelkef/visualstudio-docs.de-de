---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 720f150be1b7cf992f0949750dd52218939c7d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
Diese Struktur stellt die Adresse einer lokalen Variablen in einem Bereich (in der Regel eine Funktion oder Methode) dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 tokMethod  
 Die ID der Methode oder Funktion die lokale Variable enthalten ist.  
  
 [C++] `_mdToken` ist ein `typedef` für 32-Bit- `int`.  
  
 pLocal  
 Das Token, dessen Adresse, die diese Struktur darstellt.  
  
 dwIndex ab  
 Der Index dieser lokalen Variablen in der Methode oder Funktion oder ein anderer Wert (sprachspezifischen) kann sein.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist Teil der Union der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn die `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur auf festgelegt ist `ADDRESS_KIND_LOCAL` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) die Enumeration).  
  
 `Warning:` [Nur C++]  Wenn `pLocal` nicht null ist, dann rufen Sie müssen `Release` auf dem token Zeiger (`addr` ist ein Feld in der [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)