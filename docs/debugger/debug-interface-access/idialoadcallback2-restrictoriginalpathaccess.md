---
title: 'Idialoadcallback2:: Restrictoriginalpathaccess | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84c9eabb3eaeaec29e790a12c802aae5b1cfb610
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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