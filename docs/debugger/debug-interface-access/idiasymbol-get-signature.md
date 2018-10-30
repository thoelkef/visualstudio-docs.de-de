---
title: 'Idiasymbol:: Get_signature | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_signature method
ms.assetid: 0efefa39-49a5-4282-9d41-e50832d927e0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ab1af02478673de77f7a0f27965e0841bedec0b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888123"
---
# <a name="idiasymbolgetsignature"></a>IDiaSymbol::get_signature
Ruft den Symbolwert der Signatur ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_signature (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt das Symbol des Signatur-Wert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)