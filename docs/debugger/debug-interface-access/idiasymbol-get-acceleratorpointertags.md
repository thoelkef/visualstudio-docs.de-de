---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8467c25c8665dfb3fc91ea29d9b99c184b7ecce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Gibt alle Accelerator Zeiger Tagwert aufweisen, die entsprechen einer C++ AMP-Beschleuniger Stub-Funktion zurück.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cnt`  
 [in] Die Größe des Ausgabearrays `pPointerTags`.  
  
 `pcnt`  
 [out] Die Anzahl der Zugriffstaste Zeiger Tags in der C++ AMP-Beschleuniger Stub-Funktion.  
  
 `pPointerTags`  
 [out] Ein `DWORD` Array-Zeiger, der mit der Zugriffstaste Zeiger Tag-Werte in der C++ AMP-Beschleuniger Stub-Funktion gefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, auf eine `IDiaSymbol` -Schnittstelle, die an eine C++-AMP-Beschleuniger Stub-Funktion entspricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)