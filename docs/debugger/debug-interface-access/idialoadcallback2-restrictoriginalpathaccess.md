---
title: 'Idialoadcallback2:: Restrictoriginalpathaccess | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27bf39aea5b095860f9e5aebf864abb4df6bf86d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54964391"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Bestimmt, ob eine PDB-Datei in das ursprüngliche Debugverzeichnis gesucht werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Code als Rückgabewert `S_OK` wird verhindert, dass eine PDB-Datei in das ursprüngliche Debugverzeichnis gesucht. Das ursprüngliche Debugverzeichnis ist der Pfad der Symboldatei, die in die ausführbare Datei kompiliert wird, wenn debugging aktiviert ist. Dieser Pfad ist nicht unbedingt mit dem der Pfad, in dem die ausführbare Datei vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)