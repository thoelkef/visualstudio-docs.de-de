---
title: iPropertyProxyeeside::CreateReplacementObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715041"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Erstellt eine Kopie eines Datenobjekts, das für den Ausdrucksevaluator (EE) spezifisch ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataIn`\
[in] Ein [IEEDataStorage-Objekt,](../../../extensibility/debugger/reference/ieedatastorage.md) das die zu kopierenden Daten enthält.

`dataOut`\
[out] Gibt ein neues `IEEDataStorage`-Objekt zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode erhält ein [IEEDataStorage-Objekt,](../../../extensibility/debugger/reference/ieedatastorage.md) das ein Array von Bytes darstellt. Dieses eingehende Datenobjekt wird in der Regel nicht von der EE implementiert. Das von dieser Methode zurückgegebene Objekt wird jedoch immer vom EE `IEEDataStorage` implementiert, wodurch der EE die Schnittstelle auf jeder gewünschten Klasse implementieren kann.

 Beachten Sie, dass die `IEEDataStorage` vom eingehenden Objekt bereitgestellten `IEEDataStorage` Daten dieselben Daten im ausgehenden Objekt sein müssen.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
