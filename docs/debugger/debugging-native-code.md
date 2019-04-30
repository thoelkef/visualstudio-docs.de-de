---
title: Debuggen von nativem Code | Microsoft-Dokumentation
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 5a7cf0b150c45037941010bf7e611f4bc21252c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851905"
---
# <a name="debugging-native-code"></a>Debuggen von systemeigenem Code
In diesem Abschnitt werden einige allgemeine Debugprobleme und -verfahren für systemeigene Anwendungen erörtert. Bei den in diesem Abschnitt behandelten Verfahren wird Programmiererfahrung vorausgesetzt. Veranschaulicht, wie Visual Studio-Debugger, finden Sie unter [ein erster Blick auf der Debugger](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Vorgehensweise: Debuggen von optimiertem Code](../debugger/how-to-debug-optimized-code.md) erhalten Sie Tipps zum Debuggen von optimierten Codes, insbesondere eine nicht optimierte Version des Programms, standardoptimierungseinstellungen für Debug- und Releasekonfigurationen, Debuggen und Tipps für das Suchen von Fehlern, die nur für die in optimiertem Code (Aktivieren der Optimierung in einer Debugbuildkonfiguration) angezeigt.

 [DebugBreak und __debugbreak](../debugger/debugbreak-and-debugbreak.md) wird beschrieben, die Win32 `DebugBreak` Funktion, und enthält einen Link zum betreffenden Referenzthema im Plattform-SDK. Dort wird auch die systeminterne Funktion `__debugbreak` beschrieben.

 [C /C++ Assertionen](../debugger/c-cpp-assertions.md) erläutert assertionsanweisungen, deren Funktionsweise, die Vorteile Ihrer Verwendung (von logikfehlern, Überprüfen der Ergebnisse einer Operation und Testen von Fehlerzuständen), die Interaktion mit `_DEBUG`, und die Arten von Assertionen in unterstützt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Vorgehensweise: Debuggen von Inline-Assemblycode](../debugger/how-to-debug-inline-assembly-code.md) kurze Anweisungen zur Verwendung des Fensters Disassembly an die Assemblyanweisungen und die Fenster "Register" Anzeigen von Registerinhalten und stellt Links zu Themen über diese Fenster.

 [MFC-Debugverfahren](../debugger/mfc-debugging-techniques.md) enthält Links zu Debugtechniken für MFC‑Programme, darunter: AfxDebugBreak, das TRACE-Makro, Erkennen von Speicherverlusten in MFC, MFC‑Assertionen und Verringern der Größe eines MFC-Debugbuilds.

 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md) enthält Links zu Debugtechniken für die C-Laufzeitbibliothek, einschließlich der Verwendung der CRT-Debugbibliothek, Makros für die berichterstellung, Unterschiede zwischen Malloc und _malloc_dbg, Schreiben von Hookfunktionen und CRT-Debugheap.

 [Debuggen von systemeigenem Code häufig gestellte Fragen zur](../debugger/debugging-native-code-faqs.md) finden Sie Antworten auf häufig gestellte Fragen zum Debuggen von Visual C++ Programme

 [Debuggen von COM und ActiveX-](../debugger/com-and-activex-debugging.md) enthält Informationen zum Debuggen von COM und ActiveX-Anwendungen, einschließlich Tools Sie für COM können und ActiveX-Debuggen.

 [Vorgehensweise: Debuggen von Injiziertem Code](../debugger/how-to-debug-injected-code.md) bietet Hinweise zum Debuggen von Code, der Attribute verwendet. Zu den behandelten Themen gehören das Aktivieren von Quellcodeanmerkungen, das Anzeigen von eingefügtem Code sowie das Anzeigen des Disassemblycodes am aktuellen Ausführungspunkt.

 [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md) beschreibt, wie die **Parallele Aufgaben** und **parallele Stapel** Toolfenster zum Debuggen einer parallelen Anwendung.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Visual C++ Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md) enthält Links zu Themen, Gewusst wie: Debuggen der systemeigener Projekttypen, die von der Visualisierung erstellt C++ -Projektvorlagen.

 [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md) erläutert, wie Sie native und verwaltete DLLs zu debuggen.

 [Ein erster Blick auf der Debugger](../debugger/debugger-feature-tour.md) enthält Links zu den ausführlicheren Abschnitten der Debugdokumentation. Die Informationen umfassen: Neues im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von nativem Code, Debuggen von SQL sowie Referenzen zur Benutzeroberfläche.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen in Visual Studio](../debugger/index.md)