---
title: 'Idiastackframe:: Get_rawlvarinstancevalue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96851912abb6593ce1fe72bd3eebdd67c120c26b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992788"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Diese Methode ruft den Wert der angegebenen lokalen Variable als unformatierte Bytes ab.  
  
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
 [in] Ein `IDiaLVarInstance` Objekt, das eine Instanz der lokalen Variablen auf den Wert für darstellt.  
  
 `cbDataMax`  
 [in] Maximale Anzahl von Bytes im Puffer verweist `pbData`. Dies kann bis zu 8 Bytes sein (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Gibt die tatsächliche Anzahl der Bytes im Puffer gespeichert.  
  
 `pbData`  
 [out] Ein Puffer mit Daten gefüllt werden soll. Dieser darf nicht `NULL` sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)