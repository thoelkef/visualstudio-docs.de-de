---
title: 'Idiastackframe:: Get_lengthsavedregisters | Microsoft-Dokumentation'
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
- IDiaStackFrame::get_lengthSavedRegisters method
ms.assetid: b75fad6e-1ef4-44e6-89e3-c31c6fba10b3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a0a115eac0ddf5f12e1232b874845ed60d22bce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855117"
---
# <a name="idiastackframegetlengthsavedregisters"></a>IDiaStackFrame::get_lengthSavedRegisters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Anzahl der Bytes der gespeicherten Register, die auf dem Stapel abgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Bytes der gespeicherten Register zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` , wenn die Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



