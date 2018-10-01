---
title: 'Idiaenumtables:: Skip | Microsoft-Dokumentation'
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
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49e6e42cf2d24899c54057937b6ded310558298c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522991"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaenumtables:: Skip](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumtables-skip).  
  
Überspringt eine angegebene Anzahl von Tabellen in einer Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der Tabellen in der Enumerationsfolge übersprungen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` , wenn es keine weitere Tabellen sind zu überspringen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)



