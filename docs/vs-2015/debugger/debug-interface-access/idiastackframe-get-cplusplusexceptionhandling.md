---
title: 'IDiaStackFrame:: get_cplusplusExceptionHandling | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f400135fab95925384947488b5582b2f3d996928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190596"
---
# <a name="idiastackframeget_cplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die C++-Ausnahmebehandlung wirksam ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt zurück `TRUE` , wenn die C++-Ausnahmebehandlung für diesen Frame wirksam ist; andernfalls wird zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn die Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die C++-Ausnahmebehandlung ist nicht identisch mit der strukturierten oder System Ausnahmebehandlung.  
  
 Um zu ermitteln, ob die strukturierte Ausnahmebehandlung wirksam ist, wird die [IDiaStackFrame:: get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) -Methode aufgerufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)
