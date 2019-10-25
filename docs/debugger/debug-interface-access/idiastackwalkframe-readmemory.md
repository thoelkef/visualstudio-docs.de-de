---
title: IDiaStackWalkFrame::readMemory | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741477"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Liest Speicher aus dem Image.

## <a name="syntax"></a>Syntax

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parameter
 `type`

in Einer der [MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) -Enumerationswerte, der die Art des Arbeitsspeichers angibt, auf den zugegriffen werden soll.

 `va`

in Der Speicherort der virtuellen Adresse in Image zum beginnen des Lesens.

 `cbData`

in Größe des Daten Puffers in Bytes.

 `pcbData`

vorgenommen Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` `NULL` ist, enthält `pcbData` die Gesamtzahl der verfügbaren Daten bytes.

 `data`

vorgenommen Ein Puffer, der mit Daten aus der angegebenen Position ausgefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)