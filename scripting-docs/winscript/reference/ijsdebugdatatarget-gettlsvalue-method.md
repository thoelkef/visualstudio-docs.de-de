---
title: 'Ijsdebugdatatarget:: GetTLSValue-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577603"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue-Methode
Für den Thread, der debuggt wird, wird der Wert im Slot des threadlokalen Speichers (TLS) für den angegebenen TLS-Index abgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `threadId`  
 [in] Im Zielprozess ausgeführter Thread, aus dem gelesen werden soll.  
  
 `tlsIndex`  
 [in] Der TLS-Index, der belegt wurde, als der Zielprozess die TlsAlloc-Funktion aufrief.  
  
 `pValue`  
 [out] Der Wert mit Zeigergröße, der im TLS-Slot des Threads gespeichert wurde. Wenn der Zielthread 32-Bit ist, sind die oberen 32-Bit dieses Werts null.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Jeder Thread eines Prozesses hat seinen eigenen Slot für jeden TLS-Index.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)