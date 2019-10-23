---
title: 'Idiasymmetribol:: get_virtualTableShapeId | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShapeId method
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3134d504625435706c36e1afc7c9df64611a7516
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738814"
---
# <a name="idiasymbolget_virtualtableshapeid"></a>IDiaSymbol::get_virtualTableShapeId
Ruft den Symbol Bezeichner für die virtuelle Tabellenform des Symbols ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_virtualTableShapeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Form Symbol-ID der virtuellen Tabelle des Symbols zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Der Bezeichner ist ein eindeutiger Wert, der vom Dia SDK erstellt wird, um alle Symbole als eindeutig zu markieren.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)