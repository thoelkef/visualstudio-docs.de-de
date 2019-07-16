---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 725ac07c85dd31edaf97200a7a8668ff3efd9ab9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329523"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Initialisiert die Quelldaten für dieses Objekt und gibt ein Objekt, das die ursprünglichen Daten enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataOut`\
[out] Gibt eine [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Objekt

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode führt, was ist erforderlich, ein Objekt zu initialisieren, damit es zurückgeben kann ein [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle für die Daten des Objekts. Dadurch können Daten anzeigen und, wenn zulässig, geändert werden, indem eine typschnellansicht des Objekts.

## <a name="see-also"></a>Siehe auch
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)