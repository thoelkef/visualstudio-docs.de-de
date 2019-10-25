---
title: 'IDiaSession:: findFileById | Microsoft-Dokumentation'
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
ms.openlocfilehash: aafdd2270606ba6e56713e9166dbae2b8c635b41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742276"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Ruft eine Quelldatei nach dem Quelldatei Bezeichner ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `uniqueId`

in Gibt den Quelldatei Bezeichner an.

 `ppResult`

vorgenommen Gibt ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekt zurück, das die abgerufene Quelldatei darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Quelldatei Bezeichner ist ein eindeutiger Wert, der intern für die Dia SDK verwendet wird, um alle Quelldateien eindeutig zu machen. Diese Methode wird in der Regel intern für die Dia SDK verwendet.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)