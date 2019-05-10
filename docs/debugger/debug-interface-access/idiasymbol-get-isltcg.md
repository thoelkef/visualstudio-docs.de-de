---
title: 'Idiasymbol:: Get_isltcg | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f5fe47d8575c47756cce8fd1580ced5f3036766
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399959"
---
# <a name="idiasymbolgetisltcg"></a>IDiaSymbol::get_isLTCG
Ruft ein Flag, das angibt, ob die [Kompiliereinheit](../../debugger/debug-interface-access/compiland.md) verknüpft wurde mit den Linkerschalter [/LTCG (Link-Time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation), unterstützt die Optimierung des ganzen Programms. Diese Option gilt nur für verwalteten Code.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 pFlag

[out] Gibt `TRUE` Wenn die `compiland` mit den Linkerschalter "/ LTCG" verknüpft wurde, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)