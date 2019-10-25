---
title: IDiaStackWalkHelper::p dataforva | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d51736a80021847881db164c9e176a010124638
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741402"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Gibt den pData-Datenblock zurück, der der virtuellen Adresse zugeordnet ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT pdataForVA( 
   ULONGLONG  va,
   DWORD      cbData,
   DWORD*     pcbData,
   BYTE*      pbData
);
```

#### <a name="parameters"></a>Parameter
 `va`

in Gibt die virtuelle Adresse der abzurufenden Daten an.

 `cbData`

in Die Größe der abzurufenden Daten in Bytes.

 `pcbData`

vorgenommen Gibt die tatsächliche Größe der Daten in Bytes zurück, die abgerufen wurden.

 `pbData`

[in, out] Ein Puffer, der mit den angeforderten Daten gefüllt wird. Darf nicht `NULL` sein.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine pData für die angegebene Adresse vorhanden ist. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 PData (der-Abschnitt mit dem Namen ". pdata") eines Kompilierungen enthält Informationen zur Ausnahmebehandlung für Funktionen.

 Der Aufrufer weiß, wie viele Daten zurückgegeben werden sollen, sodass der Aufrufer nicht mehr gefragt werden muss, wie viele Daten verfügbar sind. Daher ist es zulässig, dass eine Implementierung dieser Methode einen Fehler zurückgibt, wenn der `pbData` Parameter `NULL` ist.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)