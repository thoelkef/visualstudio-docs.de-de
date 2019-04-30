---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1724ee3e81ac00ed048f323105842361ec22bc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827293"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt alle Accelerator Zeiger Tag-Werte, die entsprechen einer C++ AMP-Beschleuniger Stub-Funktion zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cnt`  
 [in] Die Größe des Ausgabearrays `pPointerTags`.  
  
 `pcnt`  
 [out] Die Anzahl von Accelerator-Zeiger-Tags in der C++ AMP-Beschleuniger Stub-Funktion.  
  
 `pPointerTags`  
 [out] Ein `DWORD` Array-Zeiger, der mit der Zugriffstaste Zeiger Tagwerten in gefüllt ist die C++ AMP-Beschleuniger Stub-Funktion.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, auf eine `IDiaSymbol` Schnittstelle, die eine C++-AMP-Beschleuniger Stub-Funktion entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
