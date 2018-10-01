---
title: 'Idiasymbol:: Get_backendmajor | Microsoft-Dokumentation'
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
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6244d731a694ce8c22692e653578a39b3981d909
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512969"
---
# <a name="idiasymbolgetbackendmajor"></a>IDiaSymbol::get_backEndMajor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasymbol:: Get_backendmajor](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-backendmajor).  
  
Ruft die Anzahl der Back-End-Hauptversion des Compilers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_backEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt zurück, die Back-End-Hauptversionsnummer. Siehe Hinweise.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
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



