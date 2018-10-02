---
title: IDiaStackWalker::getEnumFrames2 | Microsoft-Dokumentation
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
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf81e33b89a1a4361e73de4d2c532d4da3165f4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523722"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaStackWalker::getEnumFrames2](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalker-getenumframes2).  
  
Ruft ein Stack-Frame-Enumerator für eine bestimmte Plattform-Typ ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cpuid`  
 [in] Ein Wert aus der [CV_CPU_TYPE_e-Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md) Enumeration, der den Plattformtyp aus.  
  
 `pHelper`  
 [in] Das Hilfsprogramm [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) Objekt.  
  
 `ppEnum`  
 [out] Gibt eine [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) Objekt mit einer Liste von [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) Objekte.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Zum Abrufen einer Stack-Frame-Liste für die nur die X86-Plattform, rufen die [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV_CPU_TYPE_e-Enumeration](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)



