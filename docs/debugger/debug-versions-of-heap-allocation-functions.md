---
title: "Debugversionen von Heapreservierungsfunktionen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC-Makro"
  - "_malloc_dbg-Funktion"
  - "Debuggen [CRT], Heapzuordnungsfunktionen"
  - "Debuggen von Speicherverlusten, CRT-Debugbibliotheksfunktionen"
  - "Heapzuordnung, Debug"
  - "malloc-Funktion"
  - "Speicherverluste, CRT-Debugbibliotheksfunktionen"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debugversionen von Heapreservierungsfunktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die C\-Laufzeitbibliothek umfasst spezielle Debugversionen der Heapreservierungsfunktionen.  Diese Funktionen haben dieselben Namen wie die Releaseversionen, gefolgt vom Suffix \_dbg.  In diesem Thema werden die Unterschiede zwischen der Releaseversion und der \_dbg\-Version einer CRT\-Funktion beschrieben, wobei `malloc` und `_malloc_dbg` als Beispiele verwendet werden.  
  
 Wenn [\_DEBUG](/visual-cpp/c-runtime-library/debug) definiert wird, ordnet das CRT alle [malloc](/visual-cpp/c-runtime-library/reference/malloc)\-Aufrufe [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg) zu.  Aus diesem Grund müssen Sie den Code nicht umschreiben, indem Sie `malloc` durch `_malloc_dbg` ersetzen, um die Vorteile beim Debuggen nutzen zu können.  
  
 Unter Umständen möchten Sie `_malloc_dbg` jedoch explizit aufrufen.  Der explizite Aufruf von `_malloc_dbg` bietet zusätzliche Vorteile:  
  
-   Nachverfolgen von `_CLIENT_BLOCK`\-Reservierungen.  
  
-   Speichern von Quelldatei und Zeilennummer an der Stelle, an der die Reservierung angefordert wurde.  
  
 Wenn Sie die `malloc`\-Aufrufe nicht in `_malloc_dbg`\-Aufrufe konvertieren möchten, erhalten Sie die Informationen zur Quelldatei auch durch die Definition von [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc). Dadurch werden alle `malloc`\-Aufrufe vom Präprozessor direkt `_malloc_dbg` zugeordnet, sodass kein Wrapper für `malloc` erforderlich ist.  
  
 Um Reservierungstypen in Clientblöcken gesondert nachzuverfolgen, muss `_malloc_dbg` direkt aufgerufen und der `blockType`\-Parameter auf `_CLIENT_BLOCK` festgelegt werden.  
  
 Wird \_DEBUG nicht definiert, geschieht Folgendes: `malloc`\-Aufrufe werden nicht behindert, `_malloc_dbg`\-Aufrufe werden in `malloc`\-Aufrufe aufgelöst, die Definition von [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) wird ignoriert, und es werden keine Quelldateiinformationen zur Reservierungsanforderung bereitgestellt.  Da `malloc` keinen Blocktypparameter hat, werden `_CLIENT_BLOCK`\-Anforderungen wie Standardreservierungen behandelt.  
  
## Siehe auch  
 [CRT\-Debugverfahren](../debugger/crt-debugging-techniques.md)