---
title: 'IDiaEnumSymbols:: Skip | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7a6a3f06572392cad2edbf125d0ff6491b508c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563701"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Überspringt eine angegebene Anzahl von Symbolen in einer enumerationssequenz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 in Die Anzahl der zu über springenden Symbole in der enumerationssequenz.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben, `S_FALSE` Wenn keine weiteren Symbole zum Überspringen vorhanden sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
