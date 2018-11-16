---
title: 'Idiasymbol:: Get_typeids | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aeec63119c89ef3c75d4e45d65cac8a52107291f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788484"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Array von Compiler-spezifischer Typ-ID-Werten für dieses Symbol ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [out] Ein Array, das sich mit dem Typ-IDs gefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



