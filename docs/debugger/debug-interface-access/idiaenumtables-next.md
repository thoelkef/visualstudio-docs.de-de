---
title: 'Idiaenumtables:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43c7a038bbc6fecddb69950722f4423ab326c1b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875800"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Ruft eine angegebene Anzahl von Tabellen in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der Tabellen in der Enumerator abgerufen werden sollen.  
  
 `rgelt`  
 [out] Ein Array, das mit gefüllt werden soll die [IDiaTable](../../debugger/debug-interface-access/idiatable.md) Objekte, die die gewünschten Tabellen darstellen.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der Tabellen in der abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn keine weitere Tabellen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)