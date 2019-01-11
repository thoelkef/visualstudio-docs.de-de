---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94e052865c94d747bcb36cd81e0b1c023262b0c1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875153"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
Gibt die Anzahl der Tags von Accelerator-Zeiger in einer C++ AMP-Stub-Funktion zurück.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>Parameter  
 `count`  
 [out] Ein Zeiger auf eine `DWORD` , enthält die Anzahl der Zugriffstaste Zeiger-Tags in einer C++ AMP-Stub-Funktion.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, auf eine `IDiaSymbol` Schnittstelle, die eine C++-AMP-Beschleuniger Stub-Funktion entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)