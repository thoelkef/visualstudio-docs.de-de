---
title: 'Idiaenumtables:: Skip | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d2741361ddb0e7483344c5fbe123e5d4ec03588c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Überspringt eine angegebene Anzahl von Tabellen in einer Enumerationsfolge an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der Tabellen in der Enumeration Sequenz zu überspringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` , wenn keine weitere Tabellen zu überspringen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)