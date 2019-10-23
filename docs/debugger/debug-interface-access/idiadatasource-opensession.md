---
title: 'IDiaDataSource:: OpenSession | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7dd6ab61db3e3bafd594298aa41d32bce64d4941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744918"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Öffnet eine Sitzung zum Abfragen von Symbolen.

## <a name="syntax"></a>Syntax

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parameter
ppSession

vorgenommen Gibt ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Objekt zurück, das die geöffnete Sitzung darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.

|Wert|Beschreibung|
|-----------|-----------------|
|E_UNEXPECTED|Das [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) -Objekt wurde zuvor nicht mit einer Quelle von Symbolen initialisiert.|
|E_INVALIDARG|Ungültiger `ppSession`-Parameter.|
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher zum Öffnen der Sitzung.|

## <a name="remarks"></a>Hinweise
Diese Methode öffnet ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Objekt für eine Datenquelle.

`IDiaSession` Objekte implementieren Abfragen in der Datenquelle. Eine Sitzung verwaltet einen Adressraum für jeden Satz von Debugsymbolen. Wenn die exe-oder DLL-Datei, die von den Datenquellen Symbolen beschrieben wird, in mehreren Adressbereichen aktiv ist (z. b. weil Sie von mehreren Prozessen geladen wurde), sollte eine Sitzung für jeden Adressbereich verwendet werden.

## <a name="example"></a>Beispiel

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
