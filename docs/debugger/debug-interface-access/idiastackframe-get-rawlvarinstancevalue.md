---
title: 'Idiastackframe:: Get_rawlvarinstancevalue | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5872c77a9154c72f6c3bcd76452792cff34452cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Diese Methode ruft den Wert der angegebenen lokalen Variablen als unformatierte Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pInstance`  
 [in] Ein `IDiaLVarInstance` Objekt, das eine Instanz der lokalen Variablen den Wert für die abzurufenden darstellt.  
  
 `cbDataMax`  
 [in] Maximale Anzahl von Bytes im Puffer verweist `pbData`. Dies kann maximal 8 Bytes (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Gibt die tatsächliche Anzahl von Bytes im Puffer gespeichert.  
  
 `pbData`  
 [out] Ein Puffer mit Daten gefüllt werden soll. Dies kann nicht `NULL`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)