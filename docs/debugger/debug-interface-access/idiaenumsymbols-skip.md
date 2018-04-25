---
title: 'Idiaenumsymbols:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 65e96f2f03229b12c378a096ecfd7555af1f5cce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Überspringt eine angegebene Anzahl der Symbole in einem Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Symbole in der Enumeration Sequenz zu überspringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` treten keine weitere Symbole zu überspringen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)