---
title: 'Idiasymmetribol:: get_token | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_token method
ms.assetid: 7ee7a9be-a0d8-48e4-9fef-d37b3d6ae4ef
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2eaf078ca37ff278a5ef03aec8727377969dbf8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840842"
---
# <a name="idiasymbolget_token"></a>IDiaSymbol::get_token
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft das Metadatentoken einer verwalteten Funktion oder Variablen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_token (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt das Metadatentoken einer verwalteten Funktion oder Variablen zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
