---
title: 'Idiasymbol:: Get_typeids | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed742971a75d15eccfd6765dbaf242f0afc7890
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Ruft ein Array von Werten compilerspezifisch Bezeichner für dieses Symbol ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cTypeIds`  
 [in] Die Größe des Puffers zum Speichern der Daten.  
  
 `pcTypeIds`  
 [out] Gibt die Anzahl der `typeIds` geschrieben, oder wenn `typeIds` ist `NULL`, klicken Sie dann die Gesamtzahl der Typ-IDs zur Verfügung.  
  
 `typeIds[]`  
 [out] Ein Array, das mit dem Typ-IDs ausgefüllt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)