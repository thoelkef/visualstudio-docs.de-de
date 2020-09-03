---
title: Debugversionen von Heapreservierungsfunktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691156"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Debugversionen von Heapreservierungsfunktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die C-Laufzeitbibliothek umfasst spezielle Debugversionen der Heapreservierungsfunktionen. Diese Funktionen haben dieselben Namen wie die Releaseversionen, gefolgt vom Suffix _dbg. In diesem Thema werden die Unterschiede zwischen der Releaseversion und der _dbg-Version einer CRT-Funktion beschrieben, wobei `malloc` und `_malloc_dbg` als Beispiele verwendet werden.  
  
 Wenn [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) definiert ist, ordnet die CRT alle [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0)-Aufrufe [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) zu. Aus diesem Grund müssen Sie den Code nicht umschreiben, indem Sie `_malloc_dbg` durch `malloc` ersetzen, um die Vorteile beim Debuggen nutzen zu können.  
  
 Unter Umständen möchten Sie `_malloc_dbg` jedoch explizit aufrufen. Der explizite Aufruf von `_malloc_dbg` bietet zusätzliche Vorteile:  
  
- Nachverfolgen von `_CLIENT_BLOCK`-Reservierungen.  
  
- Speichern von Quelldatei und Zeilennummer an der Stelle, an der die Reservierung angefordert wurde.  
  
  Wenn Sie die `malloc`-Aufrufe nicht in `_malloc_dbg` konvertieren möchten, können Sie die Informationen zur Quelldatei auch durch die Definition von [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) abrufen. Dadurch werden alle Aufrufe von `malloc` vom Präprozessor direkt `_malloc_dbg` zugeordnet, sodass kein Wrapper für `malloc` erforderlich ist.  
  
  Um Reservierungstypen in Clientblöcken gesondert nachzuverfolgen, muss `_malloc_dbg` direkt aufgerufen und der `blockType`-Parameter auf `_CLIENT_BLOCK` festgelegt werden.  
  
  Wird _DEBUG nicht definiert, geschieht Folgendes:`malloc` -Aufrufe werden nicht behindert, `_malloc_dbg`-Aufrufe werden in `malloc`-Aufrufe aufgelöst, die Definition von [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) wird ignoriert, und es werden keine Quelldateiinformationen zur Reservierungsanforderung bereitgestellt. Da `malloc` keinen Blocktypparameter hat, werden `_CLIENT_BLOCK`-Anforderungen wie Standardreservierungen behandelt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)
