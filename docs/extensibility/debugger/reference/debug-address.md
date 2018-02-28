---
title: DEBUG_ADDRESS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1985fcf51e6d5ce02cf582257f5a3a142334faf1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
Diese Struktur stellt eine Adresse dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 ulAppDomainID  
 Die Prozess-ID  
  
 guidModule  
 Die GUID des Moduls, das diese Adresse enthält.  
  
 tokClass  
 Das Token, die Klasse oder der Typ dieser Adresse identifizieren.  
  
> [!NOTE]
>  Dieser Wert gilt nur für ein Symbol-Anbieter und hat daher keine allgemeine Bedeutung außer als Bezeichner für einen Klassentyp.  
  
 addr  
 Ein [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, die eine Union von Strukturen enthält, die den einzelnen Adresstypen beschreiben. Der Wert `addr`.`dwKind` ergibt sich aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) -Enumeration, die erläutert, wie die Union zu interpretieren.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Methode ausgefüllt werden.  
  
 **Warnung [nur C++]**  
  
 Wenn `addr.dwKind` ist `ADDRESS_KIND_METADATA_LOCAL` und `addr.addr.addrLocal.pLocal` ist keine null-Wert, und dann Sie aufrufen müssen `Release` für den token auf:  
  
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
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)