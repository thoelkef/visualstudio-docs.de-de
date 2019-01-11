---
title: 'Idiaenumsectioncontribs:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a6b02218f9d4aba3f9cc3b3785c70594a92457a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864176"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Überspringt eine angegebene Anzahl von Abschnitt Beiträge in einer Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Skip(   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der im Abschnitt Beiträge in der Enumerationsfolge übersprungen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` treten keine weitere Beiträge von Abschnitt überspringen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)