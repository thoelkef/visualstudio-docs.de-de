---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft-Dokumentation
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
ms.openlocfilehash: 283533b20614ea727be620669ea5ab66cf00e5ed
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62835773"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Gibt die Anzahl der Tags von Accelerator-Zeiger in einer C++ AMP-Stub-Funktion zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_numberOfAcceleratorPointerTags(
   DWORD* count);
```

#### <a name="parameters"></a>Parameter
 `count`

[out] Ein Zeiger auf eine `DWORD` , enthält die Anzahl der Zugriffstaste Zeiger-Tags in einem C++ AMP-Stub-Funktion.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen, auf eine `IDiaSymbol` Schnittstelle, die eine C++-AMP-Beschleuniger Stub-Funktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)