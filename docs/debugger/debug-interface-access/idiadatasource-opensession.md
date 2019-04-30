---
title: 'Idiadatasource:: OpenSession | Microsoft-Dokumentation'
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
ms.openlocfilehash: 393abb3b1e1872a416865cbfee5c142bef98ce78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838453"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Wird eine Sitzung für das Abfragen von Symbolen geöffnet.

## <a name="syntax"></a>Syntax

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parameter
ppSession

[out] Gibt eine [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt, das die geöffnete Sitzung darstellt.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.

|Wert|Beschreibung|
|-----------|-----------------|
|E_UNEXPECTED|Die [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) Objekt zuvor nicht mit der Quelle von Symbolen initialisiert wurde.|
|E_INVALIDARG|Ungültiger `ppSession`-Parameter.|
|E_OUTOFMEMORY|Nicht genügend Arbeitsspeicher, um die Sitzung zu öffnen.|

## <a name="remarks"></a>Hinweise
Diese Methode öffnet ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Objekt für eine Datenquelle.

`IDiaSession` Objekte werden Abfragen in der Datenquelle implementieren. Eine Sitzung verwaltet einen Adressraum für jeden Satz von Debugsymbolen. Wenn die .exe oder .dll-Datei, die von der Quelle Datensymbole beschrieben ist in mehrere Adressen aktiv Bereichen (z. B., weil mehrere Prozesse geladen haben), und dann eine Sitzung für jeden Adressbereich verwendet werden soll.

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
