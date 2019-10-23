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
ms.openlocfilehash: 2513825fd2b6f4e6035f9f23295f0c9f00385d0a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742077"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
Ruft die Zeilennummern Informationen für Zeilen ab, die in einem angegebenen Bereich virtueller Adressen (VA) enthalten sind.

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

in Gibt die Adresse als VA an.

`length`

in Gibt die Anzahl der Bytes für den Adressbereich an, die mit dieser Abfrage abgedeckt werden.

`ppResult`

vorgenommen Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt zurück, das eine Liste aller Zeilennummern enthält, die den angegebenen Adressbereich abdecken.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt eine Funktion, die alle in einer Funktion enthaltenen Zeilennummern mithilfe der virtuellen Adresse und Länge der Funktion abruft.

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
