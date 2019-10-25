---
title: 'IDiaSourceFile:: get_checksumType | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741831"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Ruft den Prüfsummen Datentyp ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Prüfsummen Datentyp zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Prüfsumme-Typ ist ein Wert, der einem Prüfsummen Algorithmus zugeordnet werden kann. Beispielsweise kann das standardmäßige PDB-Dateiformat einen der folgenden Werte aufweisen:

|Prüfsummen-Typ|Kryptoapi-Bezeichnung|Beschreibung|
|-------------------|---------------------|-----------------|
|0|\<none>|Keine Prüfsumme vorhanden.|
|1|`CALG_MD5`|mit dem MD5-Hash Algorithmus generierte Prüfsumme.|
|2|`CALG_SHA1`|mit dem SHA1-Hash Algorithmus generierte Prüfsumme.|

 Die `CryptoAPI` Bezeichnungen stammen aus der `ALG_ID`-Enumeration. Weitere Informationen zu Hash Algorithmen finden Sie im Abschnitt `CryptoAPI` von Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].

 Rufen Sie die [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) -Methode auf, um die tatsächlichen Prüfsummen Bytes für die Quelldatei abzurufen.

## <a name="see-also"></a>Siehe auch
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)