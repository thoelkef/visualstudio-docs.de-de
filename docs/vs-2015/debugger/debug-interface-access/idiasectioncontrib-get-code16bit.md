---
title: 'Idiasectioncontrib:: Get_code16bit | Microsoft-Dokumentation'
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
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 000bed489a2d43c48dabc9e341f454f5f236408f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889446"
---
# <a name="idiasectioncontribgetcode16bit"></a>IDiaSectionContrib::get_code16bit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob der Abschnitt 16-Bit-Code enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` ist der Code in den Abschnitt, 16-Bit-; andernfalls, gibt `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt nur auf, wenn der Code 16-Bit ist. Wenn der Code keine 16-Bit ist, konnte es nichts anderes, z. B. 32-Bit oder 64-Bit-Code sein.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



