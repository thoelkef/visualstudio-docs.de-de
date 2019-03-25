---
title: Messen der Leistung von Python-Code
description: Verwenden der Visual Studio-Profilerstellung zum Überprüfen der Leistung von Python-Code beim Einsatz von auf CPython basierenden Interpretern
ms.date: 11/12/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 840ebd6d5341bd38fb8961f4ead15fe5181e1ca3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149626"
---
# <a name="profile-python-code"></a>Profilerstellung für Python-Code

Sie können eine Python-Anwendung unter Verwendung von CPython-basierten Interpreten profilen. (Weitere Informationen zur Verfügbarkeit dieses Features für die verschiedenen Visual Studio-Versionen finden Sie unter [Featurematrix: Profilerstellung](overview-of-python-tools-for-visual-studio.md#matrix-profiling).)

## <a name="profiling-for-cpython-based-interpreters"></a>Profilerstellung für CPython-basierte Interpreter

Die Profilerstellung wird mit dem Menübefehl **Analysieren** > **Python-Profilerstellung starten** gestartet, worauf ein Konfigurationsdialogfeld geöffnet wird:

![Konfigurationsdialogfeld für Profilerstellung](media/profiling-start.png)

Wenn Sie die Option **OK** wählen, wird der Profiler ausgeführt und öffnet einen Leistungsbericht, anhand dessen Sie den Zeitaufwand in der Anwendung untersuchen können:

![Leistungsbericht für Profilerstellung](media/profiling-results.png)

> [!Note]
> Gegenwärtig unterstützt Visual Studio nur diese Stufe der vollständigen Erstellung von Anwendungsprofilen, aber wir freuen uns auf jeden Fall über Ihr Feedback zu künftigen Funktionen. Verwenden Sie unten auf dieser Seite die Schaltfläche **Produktfeedback**.

## <a name="profiling-for-ironpython"></a>Profilerstellung für IronPython

Da IronPython kein CPython-basierter Interpreter ist, funktioniert die oben genannte Profilerstellungsfunktion nicht.

Verwenden Sie stattdessen den Visual Studio .NET-Profiler, indem Sie *ipy.exe* direkt als Zielanwendung starten und die entsprechenden Argumente zum Starten Ihres Startskripts verwenden. Beziehen Sie `-X:Debug` in die Befehlszeile ein, um sicherzustellen, dass für Ihren gesamten Python-Code Debugging und Profilerstellung durchgeführt werden kann. Dieses Argument generiert einen Leistungsbericht einschließlich der sowohl in der IronPython-Laufzeit als auch Ihrem Code aufgewendeten Zeit. Ihr Code wird anhand beschädigter Namen identifiziert.

Alternativ verfügt IronPython über eigene integrierte Profilerstellungsmethoden, wofür es derzeit aber keine gute Schnellansicht gibt. Unter [An IronPython-Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (Ein IronPython-Profiler) (MSDN-Blogs) erfahren Sie, was verfügbar ist.
