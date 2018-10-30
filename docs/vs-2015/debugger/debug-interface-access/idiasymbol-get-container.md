---
title: 'Idiasymbol:: Get_container | Microsoft-Dokumentation'
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
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 127c76776285c747de27fa2a277226e541a4e981
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828948"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Funktion ruft einen Zeiger auf ein Symbol, das den übergeordneten/Container dieses Symbols darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt einen Zeiger auf ein `IDiaSymbol` mit Informationen über den Container, der dieses Symbol.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. andernfalls S_FALSE oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von S_FALSE bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK 8.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



