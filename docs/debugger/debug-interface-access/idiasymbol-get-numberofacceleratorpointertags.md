---
title: 'Idiasymmetribol:: get_numberOfAcceleratorPointerTags | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47c5827348c7b7cb450017a0e6176d71f555c841
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739701"
---
# <a name="idiasymbolget_numberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Gibt die Anzahl von Zugriffstasten-Zeiger Tags C++ in einer amp-Stub-Funktion zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parameter
 `count`

vorgenommen Ein Zeiger auf eine `DWORD`, die die Anzahl von Zugriffstasten-Zeiger Tags C++ in einer amp-stubfunktion enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird für eine `IDiaSymbol`-Schnittstelle aufgerufen, die C++ einer amp-Accelerator-stubfunktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)