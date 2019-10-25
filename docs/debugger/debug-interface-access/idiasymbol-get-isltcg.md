---
title: 'Idiasymmetribol:: get_isLTCG | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1d3fa97d5612b61151d9c435b91f500c87af0b23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740217"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
Ruft ein Flag ab, das angibt, ob die [Kompilierungen](../../debugger/debug-interface-access/compiland.md) mit dem [Linkerschalter/LTCG (Link-Time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation)verknüpft wurde, was bei der Optimierung des gesamten Programms hilft. Dieser Switch gilt nur für verwalteten Code.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parameter
 PFLAG

vorgenommen Gibt `TRUE` zurück, wenn die `compiland` mit dem/LTCG Linker-Schalter verknüpft war. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|Dia SDK v 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)