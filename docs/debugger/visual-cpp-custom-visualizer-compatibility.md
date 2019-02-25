---
title: Benutzerdefinierte Schnellansicht Visual C/C++-Kompatibilität
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335180"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Benutzerdefinierte Schnellansicht Visual C/C++-Kompatibilität

Ab Visual Studio-2019 enthält Visual C++ einen verbesserte Debugger, der einen externen 64-Bit-Prozess zum Hosten seiner speicherintensive-Komponenten verwendet. Im Rahmen dieses Update wird müssen bestimmte Erweiterungen für die Visual C/C++-ausdrucksauswertung aktualisiert werden, damit sie mit der neuen Debugger kompatibel sind.

Wenn Sie derzeit einen älteren C/C++-EE-Add-in oder benutzerdefinierte C-/C++-Schnellansicht verwenden, Sie können deaktivieren Nutzung dieser externe Prozess auf **Tools** > **Optionen**  >   **Debuggen von**, und anschließend wieder deaktivieren **Load-Debug-Symbole in externen Prozess (nur systemeigen)**. Wenn Sie diese Option deaktivieren, wird eine starke Zunahme der speicherauslastung in der IDE (devenv.exe) Prozess auftreten. Also wenn Sie erwarten, um große Projekte zu debuggen, wird empfohlen, dass die Arbeit mit dem Besitzer der Erweiterung, die sie mit dieser Option für das Debuggen kompatibel zu machen.

Wenn Sie der Besitzer eines älteren C/C++-EE-Add-in oder eine benutzerdefinierte C/C++-Schnellansicht sind, finden Sie weitere Informationen über die Entscheidung für die Erweiterung in einem Arbeitsprozess zu laden, auf die [Concord Erweiterbarkeit Beispiele Wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Sie erhalten auch eine [die benutzerdefinierte Schnellansicht Beispiel C/C++-](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).