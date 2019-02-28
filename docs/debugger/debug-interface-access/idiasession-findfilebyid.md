---
title: 'Idiasession:: Findfilebyid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3454ff5ef087b67dda5d48849d4a6c4eceb7e52
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621824"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Ruft eine Quelldatei von Datei-ID ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `uniqueId`

[in] Gibt den Bezeichner der Datei an.

 `ppResult`

[out] Gibt eine [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) abgerufene Objekt, das die Quelldatei darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 Bezeichner der Datei ist ein eindeutiger Wert, der intern verwendet, um die DIA-SDK damit alle Quelldateien eindeutig ist. Diese Methode wird in der Regel intern die DIA-SDK verwendet.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)