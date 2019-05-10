---
title: Visual C# /C++ benutzerdefinierte Schnellansicht-Kompatibilität
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901165"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C# /C++ benutzerdefinierte Schnellansicht-Kompatibilität

Ab Visual Studio-2019, Visual C++ umfasst einen verbesserten Debugger, die einen externen 64-Bit-Prozess zum Hosten seiner speicherintensive-Komponenten verwendet. Im Rahmen des Updates, bestimmte Erweiterungen für den Visual C /C++ ausdrucksauswertung muss aktualisiert werden, damit sie mit der neuen Debugger kompatibel sind.

Wenn Sie derzeit eine ältere C verwenden /C++ EE-Add-in oder C /C++ benutzerdefinierte Schnellansicht können Sie die Nutzung dieser externe Prozess aktivieren, indem Sie zu **Tools** > **Optionen**  >  **Debuggen**, und anschließend wieder deaktivieren **Load-Debug-Symbole in externen Prozess (nur systemeigen)**. Wenn Sie diese Option deaktivieren, wird eine starke Zunahme der speicherauslastung in der IDE (devenv.exe) Prozess auftreten. Also wenn Sie erwarten, um große Projekte zu debuggen, wird empfohlen, dass die Arbeit mit dem Besitzer der Erweiterung, die sie mit dieser Option für das Debuggen kompatibel zu machen.

Wenn Sie der Besitzer von einer älteren C /C++ EE-Add-in oder C /C++ benutzerdefinierte Schnellansicht, finden Sie weitere Informationen zur Entscheidung für die Erweiterung in einem Arbeitsprozess zu laden, auf die [Concord Erweiterbarkeit Beispiele Wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Sie erhalten auch eine [C /C++ benutzerdefinierte Schnellansicht Beispiel](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).