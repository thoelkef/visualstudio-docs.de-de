---
title: Messen der Leistung von Python-Code in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: f01c42f073859e2e609123eb67cc9df8e26cef75
ms.contentlocale: de-de
ms.lasthandoff: 07/18/2017

---

# <a name="profiling-python-code"></a>Profilerstellung von Python-Code

Visual Studio unterstützt die Profilerstellung einer Python-Anwendung bei Verwendung CPython-basierter Interpreter.

Die Profilerstellung wird mit dem Menübefehl **Analysieren > Python-Profilerstellung starten** gestartet, worauf ein Konfigurationsdialogfeld geöffnet wird:

![Konfigurationsdialogfeld für Profilerstellung](media/profiling-start.png)

Wenn Sie die Option **OK** wählen, wird der Profiler ausgeführt und öffnet einen Leistungsbericht, anhand dessen Sie den Zeitaufwand in der Anwendung untersuchen können:

![Leistungsbericht für Profilerstellung](media/profiling-results.png)

Eine Übersicht finden Sie hier:

Eine exemplarische Vorgehensweise finden Sie unter [Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k) (Profilerstellung mit Python-Tools für Visual Studio), Video (8 Min. 52 Sek.).

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>Profilerstellung für IronPython

Da IronPython kein CPython-basierter Interpreter ist, funktioniert die oben genannte Profilerstellungsfunktion nicht.

Verwenden Sie stattdessen den Visual Studio .NET-Profiler, indem Sie `ipy.exe` direkt als Zielanwendung starten und die entsprechenden Argumente zum Starten Ihres Startskripts verwenden. Beziehen Sie `-X:Debug` in die Befehlszeile ein, um zu erzwingen, dass Ihr gesamter Python-Code debugfähig und profilierbar ist. Dieses Argument generiert einen Leistungsbericht einschließlich der sowohl in der IronPython-Laufzeit als auch Ihrem Code aufgewendeten Zeit. Ihr Code wird anhand beschädigter Namen identifiziert.

Alternativ verfügt IronPython über eigene integrierte Profilerstellungsmethoden, wofür es derzeit aber keine gute Schnellansicht gibt. Unter [An IronPython-Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Ein IronPython-Profiler) (MSDN-Blogs) erfahren Sie, was verfügbar ist.
