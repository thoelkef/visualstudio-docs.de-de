---
title: IDiaSymbol::findInlineFramesByAddr | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57cb155d5cfcb4f2b59c101388dcc4907e1b6d80
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741181"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer bestimmten Adresse durchlaufen kann.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineFramesByAddr ( 
   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `isect`

in Gibt die Abschnitts Komponente der Adresse an.

 `offset`

in Gibt die Offset Komponente der Adresse an.

 `ppResult`

vorgenommen Enthält ein `IDiaEnumSymbols` Objekt, das die Liste der abgerufenen Frames enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)