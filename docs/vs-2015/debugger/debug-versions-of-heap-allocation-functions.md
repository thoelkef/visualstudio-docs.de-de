---
title: Debugversionen von Heapreservierungsfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c16bc2b1c887b8a33f907dd574ac647c5e0ffbc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523207"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Debugversionen von Heapreservierungsfunktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debuggen Versionen von Heapbelegungsfunktionen](https://docs.microsoft.com/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
Die C-Laufzeitbibliothek umfasst spezielle Debugversionen der Heapreservierungsfunktionen. Diese Funktionen haben dieselben Namen wie die Releaseversionen, gefolgt vom Suffix _dbg. In diesem Thema werden die Unterschiede zwischen der Releaseversion und der _dbg-Version einer CRT-Funktion beschrieben, wobei `malloc` und `_malloc_dbg` als Beispiele verwendet werden.  
  
 Wenn [_DEBUG](http://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) wird definiert, ordnet das CRT alle [Malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) Aufrufe von [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Aus diesem Grund müssen Sie den Code nicht umschreiben, indem Sie `_malloc_dbg` durch `malloc` ersetzen, um die Vorteile beim Debuggen nutzen zu können.  
  
 Unter Umständen möchten Sie `_malloc_dbg` jedoch explizit aufrufen. Der explizite Aufruf von `_malloc_dbg` bietet zusätzliche Vorteile:  
  
-   Nachverfolgen von `_CLIENT_BLOCK`-Reservierungen.  
  
-   Speichern von Quelldatei und Zeilennummer an der Stelle, an der die Reservierung angefordert wurde.  
  
 Wenn Sie nicht konvertieren möchten Ihre `malloc` Aufrufe von `_malloc_dbg`, Sie können die Informationen zur Quelldatei abrufen, indem Sie definieren [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), der bewirkt, dass der Präprozessor direkt Zuordnung alle Aufrufe von `malloc` zu `_malloc_dbg` statt auf einen Wrapper um `malloc`.  
  
 Um Reservierungstypen in Clientblöcken gesondert nachzuverfolgen, muss `_malloc_dbg` direkt aufgerufen und der `blockType`-Parameter auf `_CLIENT_BLOCK` festgelegt werden.  
  
 Wenn _DEBUG nicht definiert ist, Aufrufe von `malloc` nicht gestört werden, werden Aufrufe von `_malloc_dbg` werden aufgelöst, um `malloc`, die Definition der [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) wird ignoriert, und bezieht sich auf Dateiinformationen Quelle der Anforderung wurde nicht angegeben. Da `malloc` keinen Blocktypparameter hat, werden `_CLIENT_BLOCK`-Anforderungen wie Standardreservierungen behandelt.  
  
## <a name="see-also"></a>Siehe auch  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)



