---
title: IDiaStackWalkHelper::get_registerValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d956b1d246d0a43ae058bb58635117c093602c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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
 [in] Ein Wert aus der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) Enumeration angeben, die Registrierung auf dem der Wert abgerufen.  
  
 `pRetVal`  
 [out] Gibt den aktuellen Wert des Registers.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Trotz der Größe von der `pRetVal` Parameter, eine Implementierung sollte nur was normalerweise die Registrierung enthält speichern. Eine 8-Bit-Registrierung enthält z. B. nur die niedrigsten 8 Bits des angegebenen Werts. Dieser 8-Bit-Wert wird auf 64-Bit nach der Rückgabe dieser Methode erweitert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)