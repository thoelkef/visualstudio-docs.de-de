---
title: 'Idiasymbol:: Get_language | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_language method
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b214e16538ba6447ce97ed6569bfbb580cf222e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935873"
---
# <a name="idiasymbolgetlanguage"></a>IDiaSymbol::get_language
Ruft die Sprache der Datenquelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt einen Wert aus der [CV_CFL_LANG-Enumeration](../../debugger/debug-interface-access/cv-cfl-lang.md) Enumeration, die die Sprache der Quelle angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CFL_LANG-Enumeration](../../debugger/debug-interface-access/cv-cfl-lang.md)