---
title: 'Idiasymbol:: Get_backendbuild | Microsoft-Dokumentation'
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
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad714ceb91d4ecfc60de1359785f27530fa584ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892141"
---
# <a name="idiasymbolgetbackendbuild"></a>IDiaSymbol::get_backEndBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Buildnummer der Back-End des Compilers ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Back-End-Build. Siehe Hinweise.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="remarks"></a>Hinweise  
 Ein Compiler besteht in der Regel zwei Hauptelemente: die Front-End (den Parser), der verarbeitet, analysiert den Quellcode in ein vorläufiges Formular, und ein Back-End (Codegenerator), konvertiert die vorläufiges Formular in der Assembly. Es ist nicht ungewöhnlich, dass das Front-End, um eine andere Version als das Back-End zu erhalten.  
  
 Ein Front-End oder Back-End-Versionsnummer besteht aus drei Teilen: \<wichtigen >.\< kleinere >. \<erstellen >, wobei \<wichtige > ist die Hauptversionsnummer \<Nebenversion > ist die Nummer der Nebenversion und \<erstellen > ist die Nummer des Builds. Beispiel: 13.10.3077.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK V7. 0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



