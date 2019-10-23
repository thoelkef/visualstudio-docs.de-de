---
title: 'IDiaEnumLineNumbers:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9bba71efce68864b8737011ab7dda5cb8da3267c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744402"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Ruft eine Zeilennummer mithilfe eines Indexes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaLineNumber** lineNumber
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) -Objekts, das abgerufen werden soll. Der Index liegt im Bereich von 0 bis `count`-1, wobei `count` von der [IDiaEnumLineNumbers:: get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) -Methode zurückgegeben wird.

 lineNumber

vorgenommen Gibt ein [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) -Objekt zurück, das die gewünschte Zeilennummer darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)