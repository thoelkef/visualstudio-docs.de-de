---
title: iPropertyProxyeeside::InplaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714895"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualisiert die Daten des Objekts mit dem angegebenen Datenobjekt und gibt ein neues Datenobjekt zurück, das die neuen Daten des Objekts darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parameter
`dataIn`\
[in] Ein [IEEDataStorage-Objekt,](../../../extensibility/debugger/reference/ieedatastorage.md) das die neuen Daten enthält.

`dataOut`\
[out] Gibt ein `IEEDataStorage` neues Objekt zurück, das die ersetzten Daten enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode aktualisiert tatsächlich die Daten des Objekts. Die Daten im zurückgegebenen [IEEDataStorage-Objekt](../../../extensibility/debugger/reference/ieedatastorage.md) müssen nicht mit den `IEEDataStorage` Daten im eingehenden Objekt identisch sein, aber das zurückgegebene Objekt muss den aktuellen Wert der Eigenschaft widerspiegeln.

 Das eingehende Datenobjekt wird in der Regel nicht von der EE implementiert. Das von dieser Methode zurückgegebene Objekt wird jedoch immer vom EE `IEEDataStorage` implementiert, wodurch der EE die Schnittstelle auf jeder gewünschten Klasse implementieren kann.

 Die [CreateReplacementObject-Methode](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) erstellt ein Datenobjekt basierend auf dem eingehenden Datenobjekt, wirkt sich jedoch nicht auf die ursprünglichen Daten der Eigenschaft aus.

## <a name="see-also"></a>Weitere Informationen
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
