---
title: Debugversionen von Heap Zuordnungs Funktionen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0fde776e9f2bd48aca92c7ba6d7f1fe1e23f01a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738373"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Debugversionen von Heapreservierungsfunktionen
Die C-Laufzeitbibliothek umfasst spezielle Debugversionen der Heapreservierungsfunktionen. Diese Funktionen haben dieselben Namen wie die Releaseversionen, gefolgt vom Suffix _dbg. In diesem Thema werden die Unterschiede zwischen der Releaseversion und der _dbg-Version einer CRT-Funktion beschrieben, wobei `malloc` und `_malloc_dbg` als Beispiele verwendet werden.

 Wenn [_DEBUG](/cpp/c-runtime-library/debug) definiert ist, ordnet die CRT alle [malloc](/cpp/c-runtime-library/reference/malloc) -Aufrufe [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)zu. Aus diesem Grund müssen Sie den Code nicht umschreiben, indem Sie `_malloc_dbg` durch `malloc` ersetzen, um die Vorteile beim Debuggen nutzen zu können.

 Unter Umständen möchten Sie `_malloc_dbg` jedoch explizit aufrufen. Der explizite Aufruf von `_malloc_dbg` bietet zusätzliche Vorteile:

- Nachverfolgen von `_CLIENT_BLOCK`-Reservierungen.

- Speichern von Quelldatei und Zeilennummer an der Stelle, an der die Reservierung angefordert wurde.

  Wenn Sie Ihre `malloc` Aufrufe nicht in `_malloc_dbg` konvertieren möchten, können Sie die Quelldatei Informationen abrufen, indem Sie [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc)definieren, wodurch der Präprozessor alle Aufrufe von `malloc` direkt den `_malloc_dbg` zuordnet, anstatt sich auf einen Wrapper zu verlassen.  `malloc`.

  Um Reservierungstypen in Clientblöcken gesondert nachzuverfolgen, muss `_malloc_dbg` direkt aufgerufen und der `blockType`-Parameter auf `_CLIENT_BLOCK` festgelegt werden.

  Wenn _DEBUG nicht definiert ist, werden Aufrufe von `malloc` nicht gestört, Aufrufe `_malloc_dbg` werden zu `malloc` aufgelöst, die Definition von [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc) wird ignoriert, und es werden keine Quelldatei Informationen zur Zuordnungs Anforderung bereitgestellt. Da `malloc` keinen Blocktypparameter hat, werden `_CLIENT_BLOCK`-Anforderungen wie Standardreservierungen behandelt.

## <a name="see-also"></a>Siehe auch

- [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md)