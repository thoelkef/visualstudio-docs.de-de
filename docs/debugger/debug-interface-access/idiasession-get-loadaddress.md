---
title: 'IDiaSession:: get_loadAddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b23aff5cd5d2b94a44e3e9139ff4c97acb2225d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741926"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
Ruft die Lade Adresse für die ausführbare Datei ab, die den Symbolen in diesem Symbol Speicher entspricht.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt eine virtuelle Adresse (VA) zurück, bei der eine exe-Datei oder DLL-Datei geladen wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die zurückgegebene Lade Adresse ist immer 0 (null), es sei denn, Sie wird mit der [IDiaSession::p ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) -Methode

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)