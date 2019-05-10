---
title: IEEVisualizerDataProvider::CanSetObjectForVisualizer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e66f14ca1191a164236b78837297f20881ff0178
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65224079"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
Diese Methode bestimmt, ob die Schnellansicht das Datenobjekt, den es darstellt aktualisiert werden kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanSetObjectForVisualizer(
   BOOL* b
);
```

```csharp
int CanSetObjectForVisualizer(
   out int b
);
```

## <a name="parameters"></a>Parameter
 `b`\

 [out] Ungleich Null (`TRUE`), wenn das Objekt, für die Schnellansicht aktualisiert werden kann, NULL (`FALSE`), wenn dies nicht möglich ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein Objekt möglicherweise nicht geändert werden, wenn sie auf den nur-Lese Speicher, z. B. gebunden ist.

## <a name="see-also"></a>Siehe auch
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)