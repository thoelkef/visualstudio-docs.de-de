---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft-Dokumentation
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
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62827293"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Gibt alle Accelerator Zeiger Tag-Werte, die entsprechen einer C++ AMP-Beschleuniger Stub-Funktion zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_acceleratorPointerTags(
   DWORD          cnt,
   DWORD*         pcnt,
   DWORD*         pPointerTags);
```

#### <a name="parameters"></a>Parameter
 `cnt`

[in] Die Größe des Ausgabearrays `pPointerTags`.

 `pcnt`

[out] Die Anzahl von Accelerator-Zeiger-Tags in der C++ AMP-Beschleuniger Stub-Funktion.

 `pPointerTags`

[out] Ein `DWORD` Array-Zeiger, der mit der Zugriffstaste Zeiger Tagwerten in gefüllt ist die C++ AMP-Beschleuniger Stub-Funktion.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen, auf eine `IDiaSymbol` Schnittstelle, die eine C++-AMP-Beschleuniger Stub-Funktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)