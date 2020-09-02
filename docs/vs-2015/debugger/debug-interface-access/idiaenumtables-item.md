---
title: 'IDiaEnumTables:: Item | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9eec94a5a02eda8fe9b1b3bf8f76f5050ab1e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423867"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine Tabelle mithilfe eines Indexes oder Namens ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 in Der Index oder Name der zu abzurufenden [idisierbaren](../../debugger/debug-interface-access/idiatable.md) . Wenn eine ganzzahlige Variante verwendet wird, muss Sie im Bereich von 0 bis `count` -1 liegen, wobei `count` von der [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) -Methode zurückgegeben wird.  
  
 `table`  
 vorgenommen Gibt ein [idisierbares](../../debugger/debug-interface-access/idiatable.md) Objekt zurück, das die gewünschte Tabelle darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Zeichen folgen Variante angegeben wird, benennt die Zeichenfolge eine bestimmte Tabelle. Der Name muss einer der Tabellennamen sein, wie in [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)definiert.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
