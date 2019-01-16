---
title: IDiaStackWalkHelper::get_registerValue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af6faaea54ec7c1acc97e88e9cf56d87ca33527f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926912"
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
Ruft den Wert eines Registers.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 [in] Ein Wert aus der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) Enumeration, die angibt, die zu registrieren, dessen Wert abgerufen.  
  
 `pRetVal`  
 [out] Gibt den aktuellen Wert des Registers zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ungeachtet der Anzahl der `pRetVal` Parameter, eine Implementierung sollten speichern, was dem Registrieren normalerweise enthält nur. Eine 8-Bit-Register enthält z. B. nur die niedrigsten 8 Bits des angegebenen Werts. Dieser 8-Bit-Wert wird auf 64-Bit, nach der Rückkehr dieser Methode erweitert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)