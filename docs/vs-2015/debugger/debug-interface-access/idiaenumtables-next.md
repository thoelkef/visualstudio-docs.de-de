---
title: 'Idiaenumtables:: Next | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69e96ad3c19a488546ad8f2a95c94c9c521fa914
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197563"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Tabellen in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn keine weitere Tabellen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
