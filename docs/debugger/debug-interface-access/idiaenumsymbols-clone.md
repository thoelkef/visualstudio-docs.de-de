---
title: 'Idiaenumsymbols:: Clone | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Clone method
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc2f7a9bbba4d63837e3abe851f92b9b182978d0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915011"
---
# <a name="idiaenumsymbolsclone"></a>IDiaEnumSymbols::Clone
Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppenum  
 [out] Gibt eine [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) Objekt, das ein Duplikat des Enumerators enthält. Die Symbole sind nicht dupliziert werden, nur den Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)