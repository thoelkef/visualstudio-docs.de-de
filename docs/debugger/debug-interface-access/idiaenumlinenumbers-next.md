---
title: 'Idiaenumlinenumbers:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66abd987e3da4fadaac9d5b2de6664c4ae9e24ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599089"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Ruft eine angegebene Anzahl von Zeilennummern, in der Enumerationsfolge ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

[in] Die Anzahl von Zeilennummern im Enumerator abgerufen werden sollen.

 rgelt

[out] Gibt ein Array von [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) Objekte, die die gewünschten Zeilennummern darstellen.

 pceltFetched

[out] Gibt die Anzahl von Zeilennummern im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn keine weitere Zeilennummern vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)