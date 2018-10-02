---
title: DEBUG_ADDRESS | Microsoft-Dokumentation
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
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05c6e00591271fc0a8c074e8018bd780c75d1857
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510719"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DEBUG_ADDRESS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-address).  
  
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
 Die Prozess-ID.  
  
 guidModule  
 Die GUID des Moduls, das diese Adresse enthält.  
  
 tokClass  
 Das Token identifiziert die Klasse oder eines Typs dieser Adresse.  
  
> [!NOTE]
>  Dieser Wert richtet sich nach einem symbolanbieter und hat daher keine allgemein Bedeutung außer als Bezeichner für einen Klassentyp.  
  
 Addr  
 Ein [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Struktur, die eine Vereinigung von Strukturen enthält, in denen einzelne Adresse beschrieben. Der Wert `addr`.`dwKind` stammt aus dem [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) -Enumeration, die erläutert, wie die Union zu interpretieren.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Methode gefüllt werden soll.  
  
 **Warnung [nur für C++]**  
  
 Wenn `addr.dwKind` ist `ADDRESS_KIND_METADATA_LOCAL` und, wenn `addr.addr.addrLocal.pLocal` nicht ist ein null-Wert, wird Sie aufrufen müssen `Release` für den token auf:  
  
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

