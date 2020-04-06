---
title: iPropertyProxyeeside::GetManagedViewerCreationData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714965"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Ruft Informationen über den Viewer für diesen Eigenschaftstyp ab, um diesen Viewer zu instanziieren.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parameter
`assemName`\
[out] Gibt den Namen der Assembly zurück, die dieses Objekt enthält.

`assemBytes`\
[out] Gibt ein [IEEDataStorage-Objekt](../../../extensibility/debugger/reference/ieedatastorage.md) zurück, das die Assemblybytes dieses Objekts enthält (dies ist ein NULL-Wert, wenn keine Bytes verfügbar sind).

`assemPdb`\
[out] Gibt `IEEDataStorage` ein Objekt zurück, das die Symbolspeicherinformationen für dieses Objekt enthält (dies ist ein NULL-Wert, wenn kein Symbolspeicher verfügbar ist).

`className`\
[out] Gibt den Klassennamen zurück, der dieses Objekt enthält.

`alr`\
[out] Gibt einen Wert aus der ASSEMBLYLOCRESOLUTION-Enumeration [zurück,](../../../extensibility/debugger/reference/assemblylocresolution.md) der die Position der Baugruppe angibt.

`replacementOk`\
[out] Gibt einen`TRUE`Wert ungleich Null ( ) zurück, wenn der Wert dieses Objekts geändert werden kann; Null`FALSE`( ), wenn das Objekt schreibgeschützt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird von Typvisualisierern verwendet, um einen verwalteten Viewer zu instanziieren.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
