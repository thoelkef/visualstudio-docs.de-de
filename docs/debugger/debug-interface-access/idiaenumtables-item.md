---
title: 'Idiaenumtables:: Item | Microsoft Docs'
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
ms.openlocfilehash: 68a9dbba4226e0fa4f591bfc48b03add62ad75b3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459333"
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
 [in] Index oder Name des der [IDiaTable](../../debugger/debug-interface-access/idiatable.md) abgerufen werden sollen. Eine ganze Zahl Variante verwendet wird, muss er im Bereich 0 bis `count`-1 und, in denen `count` wie zurückgegeben wird die [idiaenumtables:: Get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) Methode.  
  
 `table`  
 [out] Gibt eine [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Objekt, das die gewünschte Tabelle darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Variante der Zeichenfolge angegeben wird, benennt die Zeichenfolge eine bestimmte Tabelle. Der Name eines die Tabellennamen sein sollte, gemäß [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
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