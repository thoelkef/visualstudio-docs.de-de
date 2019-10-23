---
title: 'IDiaSourceFile:: get_checksum | Microsoft-Dokumentation'
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
ms.openlocfilehash: 8f4367a7862dabe248dfbe08e64c45598abe3679
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741844"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Ruft die Prüfsumme Bytes ab.

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

in Größe des Daten Puffers in Bytes.

 `pcbData`

vorgenommen Gibt die Anzahl der Prüfsummen Bytes zurück. Dieser Parameter kann nicht `NULL` werden.

 `data`

[in, out] Ein Puffer, der mit der Prüfsumme Bytes gefüllt ist. Wenn dieser Parameter `NULL` ist, gibt `pcbData` die erforderliche Anzahl von Bytes zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie die [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) -Methode auf, um den Typ des Prüfsummen Algorithmus zu ermitteln, der zum Generieren der Prüfsummen Bytes verwendet wurde.

 Die Prüfsumme wird in der Regel aus dem Image der Quelldatei generiert, sodass sich Änderungen in der Quelldatei in Änderungen der Prüfsummen Bytes widerspiegeln. Wenn die Prüfsummen Bytes nicht mit einer Prüfsumme identisch sind, die aus dem geladenen Bild der Datei generiert wurde, sollte die Datei als beschädigt oder manipuliert angesehen werden.

 Typische Prüfsummen sind nie mehr als 32 Bytes groß, gehen jedoch nicht davon aus, dass es sich um die maximale Größe einer Prüfsumme handelt. Legen Sie den `data`-Parameter auf `NULL` fest, um die Anzahl der Bytes abzurufen, die zum Abrufen der Prüfsumme benötigt werden. Weisen Sie dann einen Puffer mit der entsprechenden Größe zu, und nennen Sie diese Methode mit dem neuen Puffer.

## <a name="see-also"></a>Siehe auch
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)