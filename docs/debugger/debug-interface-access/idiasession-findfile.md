---
title: 'IDiaSession:: FindFile | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9751127007b4e7823cf6d2ae35ed2fe80cb83b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742278"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Ruft Quelldateien nach dem Kompilieren und dem Namen ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT findFile ( 
   IDiaSymbol*           pCompiland,
   LPCOLESTR             name,
   DWORD                 option,
   IDiaEnumSourceFiles** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `pCompiland`

in Ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das das kompiand darstellt, das als Kontext für die Suche verwendet werden soll. Legen Sie diesen Parameter auf `NULL`, um Quelldateien in allen Kompilierungen zu suchen.

 `name`

in Gibt den Namen der Quelldatei an, die abgerufen werden soll. Legen Sie diesen Parameter auf `NULL` fest, damit alle Quelldateien abgerufen werden.

 `option`

in Gibt die Vergleichs Optionen an, die auf die Namenssuche angewendet werden. Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.

 `ppResult`

vorgenommen Gibt ein [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) -Objekt zurück, das eine Liste der abgerufenen Quelldateien enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel

```C++
IDiaEnumSourceFiles* pEnum;
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );
```

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)