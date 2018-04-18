---
title: 'Idiaenumsectioncontribs:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6e383cbd24c86116300ae020a3abe7c2b680947
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Ruft eine angegebene Anzahl von Abschnitt Beiträge in die Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Abschnitt Beiträge in den Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Ein Array mit gefüllt werden soll, die [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) Objekte, die den gewünschten Abschnitt Beiträge darstellen.  
  
 pceltFetched  
 [out] Gibt die Anzahl der Abschnitt Beiträge im Enumerator abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn keine weitere Abschnitt Beiträge vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)