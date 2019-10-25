---
title: 'Idiapropertystorage:: Read Multiple | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742882"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Liest angegebene Eigenschaften aus dem aktuellen Eigenschaften Satz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Parameter
 `cpspec`

in Anzahl der Eigenschaften, die im `rgpspec` Array angegeben sind. Wenn 0 (null), gibt die Methode keine Eigenschaften zurück, sondern gibt `S_OK` als Erfolgs Code zurück.

 `rgpspec`

in Ein Array von zu lesenden Eigenschaften. Eigenschaften können entweder durch eine eigen schafts-ID oder durch einen optionalen Zeichen folgen Namen angegeben werden. Es ist nicht erforderlich, Eigenschaften in einer bestimmten Reihenfolge im Array anzugeben. Das Array kann doppelte Eigenschaften enthalten, sodass bei der Rückgabe für einfache Eigenschaften doppelte Eigenschaftswerte entstehen. Nicht einfache Eigenschaften sollten beim Versuch, Sie ein zweites Mal zu öffnen, den Zugriff verweigert zurückgeben. Das Array kann eine Mischung aus Eigenschaften-IDs und Zeichen folgen-IDs enthalten. Dieses Array muss mindestens `cpspec` Anzahl von Eigenschafts Werten aufweisen.

 `rgvar`

[in, out] Ein Array von `PROPVARIANT` Strukturen (im Microsoft. VisualStudio. OLE. Interop-Namespace), das mit Werten für jede Eigenschaft ausgefüllt werden soll. Das Array muss mindestens `cpspec` Elemente in der Größe aufweisen. Der Aufrufer muss die Werte im Array nicht initialisieren.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn eine oder mehrere Eigenschaften nicht gefunden wurden. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn eine Eigenschaft nicht gefunden wurde, enthält der entsprechende Eintrag im `rgvar` Array eine `VARIANT` mit dem Typ `VT_EMPTY`.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)