---
title: 'Idialoadcallback2:: Restrictsystemrootaccess | Microsoft-Dokumentation'
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
- IDiaLoadCallback2::RestrictSystemRootAccess method
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 733518a50ab54417004ac769647007a8af5c1f7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515373"
---
# <a name="idialoadcallback2restrictsystemrootaccess"></a>IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idialoadcallback2:: Restrictsystemrootaccess](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess).  
  
Bestimmt, ob die Suche nach PDB-Dateien im Stammverzeichnis Systems zugelassen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Code als Rückgabewert `S_OK` wird verhindert, dass das Systemstammverzeichnis nach PDB-Dateien zu suchen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



