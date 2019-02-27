---
title: IDiaSession::findLinesByVA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29f3f714cdcbe529dac98948f6568934a6f508af
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646824"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Ruft die Zeilennummerninformationen für Zeilen in einem Bereich für die angegebene virtuelle Adresse (VA) ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT findLinesByVA (
    ULONGLONG             va,
    DWORD                 length,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
`va`

[in] Gibt die Adresse an, wie eine VA.

`length`

[in] Gibt die Anzahl der Bytes der Adressbereich aus, um mit dieser Abfrage abzudecken.

`ppResult`

[out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt, das eine Liste mit allen in der Zeile enthält Zahlen, die u. a. der angegebene Adressbereich.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt eine Funktion, die alle die zeilennummerierung innerhalb einer Funktion, die mit virtuellen Adresse der Funktion und die Länge abgerufen werden.

```C++
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)
{
    IDiaEnumLineNumbers* pEnum = NULL;
    ULONGLONG            va;
    ULONGLONG            length;

    if (pFunc->get_virtualAddress ( &va ) == S_OK)
    {
        pFunc->get_length( &length );
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );
    }
    return(pEnum);
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
