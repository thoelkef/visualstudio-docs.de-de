---
title: 'Idiasymbol:: Get_token | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_token method
ms.assetid: 7ee7a9be-a0d8-48e4-9fef-d37b3d6ae4ef
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de9996e9bbe482060af8f10ed232230c4068358c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887539"
---
# <a name="idiasymbolgettoken"></a>IDiaSymbol::get_token
Ruft das Metadatentoken für eine verwaltete Funktion oder Variable ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_token (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt das Metadatentoken für eine verwaltete Funktion oder Variable zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)