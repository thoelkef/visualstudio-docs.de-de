---
title: IDiaSession::findInlineFramesByAddr | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0f35f845642089a8ee2b14c6047e809d525e5bc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642897"
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
Ruft eine Enumeration, die einem Client zum iterieren durch alle Inlineframes auf einer bestimmten Adresse ermöglicht.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineFramesByAddr ( 
   IDiaSymbol*       parent,   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

[in] Ein `IDiaSymbol` Objekt, das das übergeordnete Element darstellt.

 `isect`

[in] Gibt die Komponente im Abschnitt der Adresse.

 `offset`

[in] Gibt die Offset-Komponente der Adresse.

 `ppResult`

[out] Enthält eine `IDiaEnumSymbols` Objekt, das die Liste der Frames enthält, die abgerufen werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)