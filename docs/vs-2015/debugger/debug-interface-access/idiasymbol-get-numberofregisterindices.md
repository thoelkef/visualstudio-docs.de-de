---
title: IDiaSymbol::get_numberOfRegisterIndices | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18506739ca113679590b63a3a6bec981374da144
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "68183141"
---
# <a name="idiasymbolgetnumberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Anzahl der Indizes, registrieren Sie sich ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_numberOfRegisterIndices(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `DWORD` , die die Anzahl der Register-Indizes enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
