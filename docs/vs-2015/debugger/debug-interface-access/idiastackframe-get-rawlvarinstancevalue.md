---
title: 'Idiastackframe:: Get_rawlvarinstancevalue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58955982"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Methode ruft den Wert der angegebenen lokalen Variable als unformatierte Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
