---
title: 'Idialoadcallback:: Restrictregistryaccess | Microsoft-Dokumentation'
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
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e609c73bd0ce8ddc5756936b274fdab89c46e0aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515827"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idialoadcallback:: Restrictregistryaccess](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-restrictregistryaccess).  
  
Bestimmt, ob die Registrierung Abfragen verwendet werden können, um Symbolsuchpfade zu suchen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT RestrictRegistryAccess();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Code als Rückgabewert `S_OK` wird verhindert, dass die Registrierung für die Symbolsuchpfade Abfragen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



