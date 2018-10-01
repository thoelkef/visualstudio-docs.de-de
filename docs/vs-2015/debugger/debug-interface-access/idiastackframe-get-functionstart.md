---
title: IDiaStackFrame::get_functionStart | Microsoft-Dokumentation
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
- IDiaStackFrame::get_functionStart
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4ecf2ca23ca63e746e955b8b3e55ded0cc8ea02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516205"
---
# <a name="idiastackframegetfunctionstart"></a>IDiaStackFrame::get_functionStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaStackFrame::get_functionStart](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackframe-get-functionstart).  
  
Ruft ein Flag, das angibt, ob der Block den Einstiegspunkt einer Funktion enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_functionStart (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` Wenn den Stapelrahmen den Einstiegspunkt einer Funktion; enthält andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` , wenn die Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



