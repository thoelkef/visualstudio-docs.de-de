---
title: 'Idiasymmetribol:: get_acceleratorPointerTags | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36b4bf9fdd362f4941e33745d59d481a473c607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741116"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Gibt alle Zugriffstasten Zeiger-Tagwerte zurück, C++ die einer amp-Beschleuniger-Stub-Funktion entsprechen.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parameter
 `cnt`

in Die Größe des Ausgabe Arrays `pPointerTags`.

 `pcnt`

vorgenommen Die Anzahl von Zugriffstasten-Zeiger Tags C++ in der amp-Accelerator-Stub-Funktion.

 `pPointerTags`

vorgenommen Ein `DWORD` Array Zeiger, der mit den Zugriffstasten-Tagwerten in der C++ amp-Beschleuniger-Stub-Funktion gefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird für eine `IDiaSymbol`-Schnittstelle aufgerufen, die C++ einer amp-Accelerator-stubfunktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)