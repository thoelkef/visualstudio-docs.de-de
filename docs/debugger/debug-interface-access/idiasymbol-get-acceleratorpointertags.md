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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607953"
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

[out] Ein `DWORD` Array-Zeiger, der mit der Zugriffstaste Zeiger-Tag-Werte in der Stub-Funktion von C++ AMP-Beschleuniger gefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="remarks"></a>Anmerkungen
 Diese Methode wird aufgerufen, auf eine `IDiaSymbol` Schnittstelle, die eine C++-AMP-Beschleuniger Stub-Funktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)