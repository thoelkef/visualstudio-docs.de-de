---
title: 'Idiasymbol:: Get_targetsection | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetSection method
ms.assetid: 95382395-da41-4aa8-87f1-5b03da128565
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36adc59d9b3dbeb9484433acea7301c55b9e7195
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834541"
---
# <a name="idiasymbolgettargetsection"></a>IDiaSymbol::get_targetSection
Ruft den Adressabschnitt eines Thunk-Ziels ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_targetSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Abschnitt ein Thunk-Zieladresse Teil.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)