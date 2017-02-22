---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "METADATA_ADDRESS_LOCAL-Struktur"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur enthält die Adresse einer lokalen Variable innerhalb eines Bereichs dar \(normalerweise eine Funktion oder Methode\).  
  
## Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## Ausdrücke  
 tokMethod  
 Die ID der Methode oder Funktion die lokale Variable ist ein Part aus.  
  
 \[C\+\+\] `_mdToken``typedef` für 32\-Bit\- `int`.  
  
 pLocal  
 Das Token, dessen Adresse dieser Struktur darstellt.  
  
 dwIndex  
 Kann der Index dieser lokalen Variablen in der Methode oder der Funktion oder ein anderer Wert \(sprachspezifisch\).  
  
## Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, wenn das `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur in `ADDRESS_KIND_LOCAL` festgelegt wird \(ein Wert aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration\).  
  
 \[C\+\+\] `Warning:`nur bei `pLocal` nicht NULL ist, müssen Sie auf dem `Release` Zeiger aufrufen \(`addr` Token ist ein Feld in der [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur\):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)