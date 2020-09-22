---
title: DEBUG_ADDRESS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d001d29433573fedde3b4310f989667538b4b69c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841203"
---
# <a name="debug_address"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 ulappdomainid  
 Die Prozess-ID.  
  
 guidmodule  
 Die GUID des Moduls, das diese Adresse enthält.  
  
 "dekclass"  
 Das Token, das die Klasse oder den Typ dieser Adresse identifiziert.  
  
> [!NOTE]
> Dieser Wert ist für einen Symbol Anbieter spezifisch und hat daher keine allgemeine Bedeutung, außer als Bezeichner für einen Klassentyp.  
  
 addr  
 Eine [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) -Struktur, die eine Union von-Strukturen enthält, die die einzelnen Adresstypen beschreiben. Der-Wert `addr` .`dwKind` stammt aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) -Enumeration, in der die Interpretation der Union erläutert wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird an die [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) -Methode, die ausgefüllt werden soll, übermittelt.  
  
 **Warnung [nur C++]**  
  
 Wenn `addr.dwKind` ist `ADDRESS_KIND_METADATA_LOCAL` und wenn `addr.addr.addrLocal.pLocal` kein NULL-Wert ist, müssen Sie `Release` für den tokenzeiger aufzurufen:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
