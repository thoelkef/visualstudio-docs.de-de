---
title: 'Idiaenumsectioncontribs:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01b09f132d7afadc5462602bde2eeb0a3da3bead
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520875"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaenumsectioncontribs:: Next](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsectioncontribs-next).  
  
Ruft eine angegebene Anzahl von Abschnitt Beiträge in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der im Abschnitt Beiträge im Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Ein Array mit gefüllt werden soll, die [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) Objekte, die die gewünschten Abschnitt Beiträge darstellen.  
  
 pceltFetched  
 [out] Gibt die Anzahl der im Abschnitt Beiträge im Enumerator abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` treten keine weitere Beiträge des Abschnitts. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



