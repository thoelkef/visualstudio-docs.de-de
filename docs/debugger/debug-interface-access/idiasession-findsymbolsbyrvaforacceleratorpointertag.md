---
title: 'IDiaSession:: findsymbolsbyrvaforacceleratorpointertag | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1b24d24de35de30b24937a6cfbf59d12f69482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741995"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Wenn ein entsprechender Tagwert angegeben ist, gibt diese Methode eine Enumeration von Symbolen zurück, die in einer angegebenen relativen virtuellen Adresse enthalten sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

in Eine `IDiaSymbol`, die der zu durchsuchenden Stub-Zugriffs Funktion entspricht.

 `tagValue`

in Der Zeiger Tagwert.

 `rva`

in Die relative virtuelle Adresse.

 `ppResult`

vorgenommen Ein Zeiger auf einen `IDiaEnumSymbols` Schnittstellen Zeiger, der mit dem Ergebnis initialisiert wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird nur für eine `IDiaSymbol`-Schnittstelle aufgerufen, die einer Zugriffstasten-Stub-Funktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)