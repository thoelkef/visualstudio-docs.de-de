---
title: 'Idiastackframe:: Get_rawlvarinstancevalue | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ee04a345d95ee521c13f2023ab4a5a525003dac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887171"
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



