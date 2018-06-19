---
title: 'Idialoadcallback2:: Restrictoriginalpathaccess | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd3cd1f4989e88c41039328cdc4d54071ff49bac
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458933"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Bestimmt, ob es angemessen, eine PDB-Datei im ursprünglichen Debugverzeichnis suchen ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Alle Rückgabecode außer `S_OK` wird verhindert, dass eine PDB-Datei im ursprünglichen Debugverzeichnis suchen. Das ursprüngliche Debugverzeichnis ist der Pfad der Symboldatei in die ausführbare Datei kompiliert werden, wenn Debuggen aktiviert ist. Dieser Pfad ist nicht unbedingt mit dem der Pfad, in dem die ausführbare Datei vorhanden ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)