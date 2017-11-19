---
title: 'Idiasymbol:: Get_backendbuild | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc1d06aa488335c8a7d551d59d9ecf3d3beea9f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetbackendbuild"></a>IDiaSymbol::get_backEndBuild
Ruft die Back-End-Build-Nummer des Compilers ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Back-End-Build. Siehe Hinweise.  
  
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