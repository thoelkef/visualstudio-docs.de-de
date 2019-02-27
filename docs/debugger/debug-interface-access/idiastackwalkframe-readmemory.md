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
ms.openlocfilehash: 82ef0d25e796f9e04ecdcfd0c54a7312b9c9edad
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628597"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Liest Arbeitsspeicher aus Image an.

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

[in] Eines der [MemoryTypeEnum-Enumeration](../../debugger/debug-interface-access/memorytypeenum.md) Enumerationswerte, der angibt, die Art des Arbeitsspeichers auf.

 `va`

[in] Speicherort der virtuellen Adresse in Abbildung gelesen werden soll.

 `cbData`

[in] Größe des Datenpuffers in Byte.

 `pcbData`

[out] Gibt die Anzahl der zurückgegebenen Bytes. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes der Daten zur Verfügung.

 `data`

[out] Ein Puffer, der mit Daten aus der angegebenen Position gefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)