---
title: 'Idiasymbol:: Get_types | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c53a8866856288aa039c0e23b6244da80184285d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Ruft ein Array von Compiler-spezifische Typen für dieses Symbol ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cTypes`  
 [in] Die Größe des Puffers zum Speichern der Daten.  
  
 `pcTypes`  
 [out] Gibt die Anzahl der Typen, die geschrieben wird, oder wenn die `types` Parameter ist `NULL`, klicken Sie dann die Gesamtzahl der verfügbaren Typen.  
  
 `types[]`  
 [out] Ein Array, das mit ausgefüllt werden die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekte, die alle Typen für dieses Symbol darstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)