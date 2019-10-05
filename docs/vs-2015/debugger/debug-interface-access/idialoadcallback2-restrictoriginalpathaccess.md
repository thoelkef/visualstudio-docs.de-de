---
title: 'Idialoadcallback2:: Restrictoriginalpathaccess | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 970a188b5d72353dbb3ccf64fd74f3354f1ba888
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151949"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bestimmt, ob eine PDB-Datei in das ursprüngliche Debugverzeichnis gesucht werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Code als Rückgabewert `S_OK` wird verhindert, dass eine PDB-Datei in das ursprüngliche Debugverzeichnis gesucht. Das ursprüngliche Debugverzeichnis ist der Pfad der Symboldatei, die in die ausführbare Datei kompiliert wird, wenn debugging aktiviert ist. Dieser Pfad ist nicht unbedingt mit dem der Pfad, in dem die ausführbare Datei vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
