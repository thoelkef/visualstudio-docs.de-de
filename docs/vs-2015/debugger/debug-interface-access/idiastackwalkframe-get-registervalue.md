---
title: 'Idiastackwalkframe:: Get_registervalue | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaStackWalkFrame::get_registerValue method
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8ff950d5a798494bdf051a8b6ccd6b7be8df18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523354"
---
# <a name="idiastackwalkframegetregistervalue"></a>IDiaStackWalkFrame::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiastackwalkframe:: Get_registervalue](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkframe-get-registervalue).  
  
Ruft den Wert eines Registers.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `index`  
 [in] Ein Wert aus der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) -Enumeration, die das Register, um den Wert für angibt.  
  
 `pRetVal`  
 [out] Gibt den aktuellen Wert des Registers zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)



