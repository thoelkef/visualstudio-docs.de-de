---
title: 'IDiaLoadCallback2:: RestrictDBGAccess | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c40aca343821f26213ee9e609a341918b9a7ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187314"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bestimmt, ob die Suche nach Debuginformationen aus dbg-Dateien zulässig ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein anderer Rückgabewert als `S_OK` , um zu verhindern, dass Debuginformationen von dbg-Dateien gesucht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
