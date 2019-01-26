---
title: IPropertyProxyEESide::ResolveAssemblyRef | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d161e5e66d60b3967dcdd0e9e6f67e5699c4444c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949778"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Bestimmt die Position des angegebenen verwalteten Assemblyverweises.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ResolveAssemblyRef(  
   BSTR*                  assemName,  
   IEEDataStorage**       assemBytes,  
   IEEDataStorage**       assemPdb,  
   BSTR*                  assemLocation,  
   ASSEMBLYLOCRESOLUTION* alr  
);  
```  
  
```csharp  
int ResolveAssemblyRef(  
   ref string                     assemName,  
   out IEEDataStorage             assemBytes,  
   out IEEDataStorage             assemPdb,  
   out string                     assemLocation,  
   out enum_ASSEMBLYLOCRESOLUTION alr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `assemName`  
 [in] Der Name der Assembly auflösen.  
  
 `assemBytes`  
 [out] Gibt eine [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Objekt, enthält die Assemblybytes, die dem Verweis zugeordnet.  
  
 `assemPdb`  
 [out] Gibt eine `IEEDataStorage` -Objekt, das das Symbol enthält Daten, die mit dieser Anforderung verknüpfte speichern.  
  
 `assemLocation`  
 [out] Gibt den Speicherort des dieses Verweises zurück.  
  
 `alr`  
 [out] Gibt einen Wert aus der [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) Enumeration, der angibt, der des Speicherortes der Assembly des Verweises.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht in der Regel von einem benutzerdefinierten ausdrucksauswertung implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)