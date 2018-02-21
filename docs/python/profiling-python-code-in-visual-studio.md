---
title: Messen der Leistung von Python-Code in Visual Studio | Microsoft-Dokumentation
description: "Verwenden der Visual Studio-Profilerstellung zum Überprüfen der Leistung von Python-Code beim Einsatz von auf CPython basierenden Interpretern."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 4b6b2be69cc0d52774c0fc5c8cd7f3b60273fd02
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="profiling-python-code"></a>Profilerstellung für Python-Code

Sie können eine Python-Anwendung unter Verwendung von CPython-basierten Interpreten profilen. (Weitere Informationen zur Verfügbarkeit dieses Features für die verschiedenen Visual Studio-Versionen finden Sie unter [Featurematrix: Profilerstellung](overview-of-python-tools-for-visual-studio.md#matrix-profiling).)

Die Profilerstellung wird mit dem Menübefehl **Analysieren > Python-Profilerstellung starten** gestartet, worauf ein Konfigurationsdialogfeld geöffnet wird:

![Konfigurationsdialogfeld für Profilerstellung](media/profiling-start.png)

Wenn Sie die Option **OK** wählen, wird der Profiler ausgeführt und öffnet einen Leistungsbericht, anhand dessen Sie den Zeitaufwand in der Anwendung untersuchen können:

![Leistungsbericht für Profilerstellung](media/profiling-results.png)

Eine Veranschaulichung finden Sie im Video [Profiling Python (Profilerstellung in Python)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=s6FoC6LWE_1005918567) (Microsoft Virtual Academy, 03:00 min).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567]

## <a name="profiling-for-ironpython"></a>Profilerstellung für IronPython

Da IronPython kein CPython-basierter Interpreter ist, funktioniert die oben genannte Profilerstellungsfunktion nicht.

Verwenden Sie stattdessen den Visual Studio .NET-Profiler, indem Sie `ipy.exe` direkt als Zielanwendung starten und die entsprechenden Argumente zum Starten Ihres Startskripts verwenden. Beziehen Sie `-X:Debug` in die Befehlszeile ein, um sicherzustellen, dass für Ihren gesamten Python-Code Debugging und Profilerstellung durchgeführt werden kann. Dieses Argument generiert einen Leistungsbericht einschließlich der sowohl in der IronPython-Laufzeit als auch Ihrem Code aufgewendeten Zeit. Ihr Code wird anhand beschädigter Namen identifiziert.

Alternativ verfügt IronPython über eigene integrierte Profilerstellungsmethoden, wofür es derzeit aber keine gute Schnellansicht gibt. Unter [An IronPython-Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Ein IronPython-Profiler) (MSDN-Blogs) erfahren Sie, was verfügbar ist.