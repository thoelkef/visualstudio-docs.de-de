---
title: Debugtechniken CRT | Microsoft-Dokumentation
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
- c.runtime.debugging
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [CRT]
- CRT, debugging
- debugging [C++], CRT debug support
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2743c7185f09f19353ca5fedab0327593dc33bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515355"
---
# <a name="crt-debugging-techniques"></a>CRT-Debugverfahren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CRT-Debugverfahren](https://docs.microsoft.com/visualstudio/debugger/crt-debugging-techniques).  
  
Die folgenden Debugverfahren können beim Debuggen von Programmen hilfreich sein, die die C-Laufzeitbibliothek verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verwenden der CRT-Debugbibliothek](../debugger/crt-debug-library-use.md)  
 Hier wird beschrieben, wie die C-Laufzeitbibliothek das Debuggen unterstützt, und Sie erhalten Hinweise für den Zugriff auf die betreffenden Tools.  
  
 [Makros für die Berichterstellung](../debugger/macros-for-reporting.md)  
 Enthält Informationen über die **_RPTn** und **_RPTFn** Makros (die in CRTDBG.H definiert werden. H), die die Verwendung von ersetzt `printf` Anweisungen für das Debuggen.  
  
 [Debugversionen von Heapreservierungsfunktionen](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Erörtert die speziellen Debugversionen von Heapreservierungsfunktionen. Zu den behandelten Themen gehören die Zuordnung von Aufrufen durch die CRT-Laufzeitbibliothek, Vorteile des expliziten Aufrufs, Vermeiden von Konvertierungen, Dokumentieren der einzelnen Reservierungstypen in Clientblocks und die Ergebnisse bei nicht definiertem _DEBUG.  
  
 [Details zum CRT-Debugheap](../debugger/crt-debug-heap-details.md)  
 Enthält Links zu den Themen Speicherverwaltung und Debugheap, Blocktypen auf dem Debugheap, Verwenden des Debugheaps, Berichtsfunktionen für den Heapzustand und Nachverfolgen von Heapreservierungsanforderungen.  
  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)  
 Enthält Links zu den Themen Hookfunktionen für Clientblöcke, Hookfunktionen für Reservierungen, Reservierungshooks und CRT-Speicherbelegungen sowie Hookfunktionen für Berichte.  
  
 [Suchen von Arbeitsspeicherverlusten mit der CRT-Bibliothek](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Hier werden Verfahren zum Erkennen und Isolieren von Arbeitsspeicherverlusten mithilfe des Debuggers und der C-Laufzeitbibliothek erläutert.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)  
 Hier werden einige allgemeine Probleme und Verfahren beim Debuggen für C- und C++-Anwendungen erörtert.  
  
 [Debuggersicherheit](../debugger/debugger-security.md)  
 Enthält Empfehlungen für mehr Sicherheit beim Debuggen.



