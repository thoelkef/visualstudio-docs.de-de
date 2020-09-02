---
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151949"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bestimmt, ob es in Ordnung ist, im ursprünglichen Debugverzeichnis nach einer PDB-Datei zu suchen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Jeder andere Rückgabecode als `S_OK` verhindert das Suchen nach einer PDB-Datei im ursprünglichen Debugverzeichnis. Das ursprüngliche Debugverzeichnis ist der Pfad zu der Symbol Datei, die in die ausführbare Datei kompiliert wird, wenn Debugging aktiviert ist. Dieser Pfad ist nicht notwendigerweise identisch mit dem Pfad, in dem die ausführbare Datei vorhanden ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
