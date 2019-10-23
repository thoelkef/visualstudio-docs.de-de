---
title: 'IDiaStackWalkHelper:: Read Memory | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741359"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Liest einen Datenblock aus dem Image der ausführbaren Datei im Arbeitsspeicher.

## <a name="syntax"></a>Syntax

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parameter
 `type`

in Ein Wert aus der [MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) -enumerationsenumeration, der den Typ des zu lesenden Speichers angibt.

 va

in Die virtuelle Adresse im Abbild, ab der der Lesevorgang begonnen werden soll.

 `cbData`

in Die Größe des Daten Puffers in Bytes.

 `pcbData`

vorgenommen Gibt die Anzahl der tatsächlich gelesenen Bytes zurück. Wenn `pbData` `NULL` ist, ist dies die Gesamtanzahl der verfügbaren Daten bytes.

 `pbData`

[in, out] Ein Puffer, der mit dem gelesenen Speicher gefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md)