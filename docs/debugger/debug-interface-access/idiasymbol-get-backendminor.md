---
title: 'Idiasymbol:: Get_backendminor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 474b62f702655472327f94370f75955695192795
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
Ruft die Nebenversionsnummer der Back-End des Compilers ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Nebenversionsnummer der Back-End zurück. Siehe Hinweise.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein Compiler besteht in der Regel zwei Hauptelemente: Front-End (Parser), der verarbeitet die Analyse des Quellcodes in eine temporäre Form, und ein Back-End (Code-Generator), die in der Assembly intermediate Format konvertiert. Es ist nicht ungewöhnlich, dass front-End für eine andere Version als der Back-End haben.  
  
 Ein front-End- oder Back-End-Versionsnummer besteht aus drei Teilen: \<wichtigen >.\< kleinere >. \<erstellen >, wobei \<wichtigen > ist die Hauptversionsnummer \<kleinere > ist die Nummer der Nebenversion und \<erstellen > Nummer des Builds. Beispielsweise 13.10.3077.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK Version 7.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)