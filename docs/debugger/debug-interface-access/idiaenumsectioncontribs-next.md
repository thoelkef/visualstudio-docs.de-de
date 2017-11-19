---
title: 'Idiaenumsectioncontribs:: Next | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50682486041327270b69c6ec86b81a2df2b3a426
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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