---
title: "DEBUG_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "DEBUG_ADDRESS-Struktur"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur stellt eine Adresse dar.  
  
## Syntax  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## Ausdrücke  
 ulAppDomainID  
 Die Prozessnummer  
  
 guidModule  
 Die GUID des Moduls, das diese Adresse enthält.  
  
 tokClass  
 Das Token, das die Klasse oder den Typ dieser Adresse bezeichnet.  
  
> [!NOTE]
>  Dieser Wert ist für ein Symbol für bestimmt und enthält daher keine allgemeine Bedeutung anders als Bezeichner für einen Klassentyp.  
  
 Adr  
 Eine [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, die eine Union von Strukturen enthält, die die einzelnen Adresstypen beschreiben.  Der Wert `addr`.`dwKind` stammt aus der [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)\-Enumeration, der erklärt, wie die Gesamtmenge interpretiert.  
  
## Hinweise  
 Diese Struktur wird auf die gefüllt werden soll [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)\-Methode übergeben.  
  
 **Warnung nur \[C\+\+\]**  
  
 Wenn `addr.dwKind``ADDRESS_KIND_METADATA_LOCAL` ist und `addr.addr.addrLocal.pLocal` kein NULL\-Wert ist, müssen Sie auf dem `Release` Zeiger auf das Token aufrufen:  
  
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
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)