---
title: IEEVisualizerDataProvider::CanSetObjectForVisualizer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71fe6ed16bd1e80a13cfe97fe5ebcf84bc140da4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335609"
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