---
title: 'Idiaenumtables:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 805be4cd9f40bdbdb0f02521a0d946c7121847c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939698"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Ruft eine Tabelle über einen Index oder Name ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 [in] Index oder Name des der [IDiaTable](../../debugger/debug-interface-access/idiatable.md) abgerufen werden sollen. Wenn eine ganze Zahl Variante verwendet wird, muss es im Bereich von 0 bis `count`-1 und, in denen `count` ist von zurückgegeben der [idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) Methode.  
  
 `table`  
 [out] Gibt eine [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Objekt, das die gewünschte Tabelle darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Variante der Zeichenfolge angegeben ist, benennt die Zeichenfolge eine bestimmte Tabelle. Der Name muss eine der Tabelle gemäß [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Beispiel  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)