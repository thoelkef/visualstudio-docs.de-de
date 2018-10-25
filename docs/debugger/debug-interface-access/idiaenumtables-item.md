---
title: 'Idiaenumtables:: Item | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc95fe0f57eabbd933f8de842d842914948f3e4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819953"
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
 [Idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)