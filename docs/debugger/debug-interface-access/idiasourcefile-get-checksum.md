---
title: 'Idiasourcefile:: Get_checksum | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dc866cf392d2464756fc4e5cb19bfd02fcdea58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838066"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Ruft die Bytes der Prüfsumme ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parameter
 `cbData`

[in] Größe des Datenpuffers in Byte.

 `pcbData`

[out] Gibt die Anzahl der Bytes der Prüfsumme zurück. Dieser Parameter darf nicht sein `NULL`.

 `data`

[in, out] Ein Puffer, der mit der Prüfsumme Bytes gefüllt ist. Wenn dieser Parameter ist `NULL`, klicken Sie dann `pcbData` gibt die Anzahl der Bytes, die erforderlich sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Um den Typ des Prüfsummenalgorithmus zu ermitteln, die verwendet wurde, um die Bytes der Prüfsumme zu generieren, rufen die [idiasourcefile:: Get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) Methode.

 Die Prüfsumme wird in der Regel aus dem Image der Quelldatei generiert, damit die Änderungen in der Quelldatei in die Änderungen in den Bytes der Prüfsumme berücksichtigt werden. Die Bytes der Prüfsumme stimmen nicht überein. wird eine Prüfsumme aus geladenen Bild der Datei generiert wird, und klicken Sie dann die Datei, die berücksichtigt werden sollten beschädigt oder manipuliert.

 Typische Prüfsummen werden nie mehr als 32 Bytes, aber nicht davon ausgehen, dass die maximale Größe einer Prüfsumme ist. Legen Sie die `data` Parameter `NULL` beim Abrufen der Anzahl von Bytes, die zum Abrufen der Prüfsumme erforderlich sind. Klicken Sie dann ein Puffer von geeigneter Größe, und rufen Sie diese Methode einmal mit dem neuen Puffer.

## <a name="see-also"></a>Siehe auch
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)