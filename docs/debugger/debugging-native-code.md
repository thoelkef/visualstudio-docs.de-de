---
title: Debugging von nativem Code | Microsoft-Dokumentation
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
ms.openlocfilehash: 8115d16b64096af343adb918ba4855d9655d4df0
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211146"
---
# <a name="debugging-native-code"></a>Debuggen von systemeigenem Code
In diesem Abschnitt werden einige allgemeine Debugprobleme und -verfahren für systemeigene Anwendungen erörtert. Bei den in diesem Abschnitt behandelten Verfahren wird Programmiererfahrung vorausgesetzt. Informationen zur Verwendung des Visual Studio-Debuggers finden Sie unter der [erste Einblick in den Debugger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Vorgehensweise: Debugoptimierter Code](../debugger/how-to-debug-optimized-code.md) bietet Tipps zum Debuggen von optimiertem Code, insbesondere, warum Sie eine nicht optimierte Version des Programms Debuggen, standardmäßige Optimierungs Einstellungen für Debug-und Releasekonfigurationen sowie Tipps zum Auffinden von Fehlern, die nur in optimiertem Code angezeigt (Optimierung in einer Debugbuildkonfiguration wird eingeschaltet).

 Debug [-und __debugbreak](../debugger/debugbreak-and-debugbreak.md) Beschreibt die Win32 `DebugBreak` -Funktion und stellt einen Link zu Ihrem Referenz Thema im Platform SDK bereit. Dort wird auch die systeminterne Funktion `__debugbreak` beschrieben.

 [C/C++ ](../debugger/c-cpp-assertions.md) Assertionen erläutert Assertionsanweisungen, ihre Funktionsweise, die Vorteile der Verwendung (das Abfangen von logischen Fehlern, das Überprüfen der Ergebnisse eines Vorgangs und das Testen von `_DEBUG`Fehlerbedingungen), ihre Interaktion mit und die Typen von Assertionen. unterstützt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]in.

 [Vorgehensweise: Debuggen von](../debugger/how-to-debug-inline-assembly-code.md) Inline-Assemblycode bietet kurze Anweisungen zum Verwenden des Fensters Disassembly zum Anzeigen der Assemblyanweisungen und des Fensters Register zum Anzeigen von Register Inhalten und bietet Links zu Themen zu diesen Fenstern.

 [MFC-Debugverfahren](../debugger/mfc-debugging-techniques.md) Verknüpft Sie mit Debuggingtechniken für MFC-Programme, einschließlich: AfxDebugBreak, das Trace-Makro, das Erkennen von Speicher Verlusten in MFC, MFC-Assertionen und das Reduzieren der Größe von MFC-Debugbuilds.

 [CRT-Debugverfahren](../debugger/crt-debugging-techniques.md) Links zu Debugtechniken für die C-Lauf Zeit Bibliothek, einschließlich der Verwendung der CRT-Debugbibliothek, Makros für die Berichterstellung, Unterschiede zwischen malloc und _malloc_dbg, Schreiben von Debug-Hook-Funktionen und der CRT-Debugheap.

 Häufig gestellte Fragen zum [Debuggen](../debugger/debugging-native-code-faqs.md) Bietet Antworten auf häufig gestellte Fragen zum Debuggen von visuellen C++ Programmen.

 [Com-und ActiveX-Debugging](../debugger/com-and-activex-debugging.md) Bietet Informationen zum Debuggen von com-und ActiveX-Anwendungen, einschließlich Tools, die Sie für com-und ActiveX-Debugging verwenden können

 [Vorgehensweise: Debuggefügter Code](../debugger/how-to-debug-injected-code.md) bietet Anleitungen zum Debuggen von Code, der Attribute verwendet. Zu den behandelten Themen gehören das Aktivieren von Quellcodeanmerkungen, das Anzeigen von eingefügtem Code sowie das Anzeigen des Disassemblycodes am aktuellen Ausführungspunkt.

 [Exemplarische Vorgehensweise: Beim Debuggen](../debugger/walkthrough-debugging-a-parallel-application.md) einer parallelen Anwendung wird beschrieben, wie Sie mit den Tool Fenstern **parallele Aufgaben** und **parallele Stapel** eine parallele Anwendung debuggen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Visuelle C++ Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md) bietet Links zu Themen, in denen beschrieben wird, wie Sie die systemeigenen Projekttypen C++ Debuggen, die von den visuellen Projektvorlagen erstellt werden

 [Debugging von DLL-Projekten](../debugger/debugging-dll-projects.md) Enthält Informationen zum Debuggen von nativen und verwalteten DLLs.

 [Der erste Blick auf den Debugger](../debugger/debugger-feature-tour.md) Enthält Links zu den größeren Abschnitten der debuggingdokumentation. Die Informationen umfassen: Neues im Debugger, Einstellungen und Vorbereitung, Haltepunkte, Ausnahmebehandlung, Bearbeiten und Fortfahren, Debuggen von verwaltetem Code, Debuggen von nativem Code, Debuggen von SQL sowie Referenzen zur Benutzeroberfläche.

## <a name="see-also"></a>Siehe auch

- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen in Visual Studio](../debugger/index.yml)