---
title: iPropertyProxyeeside::ResolveAssemblyRef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c54945b0c89fb9608fab6aa70dcc63a7c6ae42df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714887"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Bestimmt den Speicherort der angegebenen verwalteten Assemblyreferenz.

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

## <a name="parameters"></a>Parameter
`assemName`\
[in] Name der aufgelösten Assembly.

`assemBytes`\
[out] Gibt ein [IEEDataStorage-Objekt](../../../extensibility/debugger/reference/ieedatastorage.md) zurück, das die Assemblybytes enthält, die dem Verweis zugeordnet sind.

`assemPdb`\
[out] Gibt `IEEDataStorage` ein Objekt zurück, das die Symbolspeicherdaten enthält, die diesem Verweis zugeordnet sind.

`assemLocation`\
[out] Gibt die Pfadposition dieses Verweises zurück.

`alr`\
[out] Gibt einen Wert aus der ASSEMBLYLOCRESOLUTION-Enumeration [zurück,](../../../extensibility/debugger/reference/assemblylocresolution.md) der die Position der Assembly dieses Verweises angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird in der Regel nicht von einem benutzerdefinierten Ausdrucksevaluator implementiert.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
