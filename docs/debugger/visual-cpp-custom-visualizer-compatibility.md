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
ms.assetid: 64af5bed-e38b-420f-b9ce-d64f35100aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: a51f2d87b432bf6f4a3925b55622273b56cf5c32
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920963"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Benutzerdefinierte Schnellansicht Visual C/C++-Kompatibilität

Ab Visual Studio-2019 enthält Visual C++ einen verbesserte Debugger, der einen externen 64-Bit-Prozess zum Hosten seiner speicherintensive-Komponenten verwendet. Im Rahmen dieses Update wird müssen bestimmte Erweiterungen für die Visual C/C++-ausdrucksauswertung aktualisiert werden, damit sie mit der neuen Debugger kompatibel sind.

Wenn Sie derzeit einen älteren C/C++-EE-Add-in oder benutzerdefinierte C-/C++-Schnellansicht verwenden, Sie können deaktivieren Nutzung dieser externe Prozess auf **Tools** > **Optionen**  >   **Debuggen von**, und anschließend wieder deaktivieren **Load-Debug-Symbole in externen Prozess (nur systemeigen)**. Wenn Sie diese Option deaktivieren, wird eine starke Zunahme der speicherauslastung in der IDE (devenv.exe) Prozess auftreten. Also wenn Sie erwarten, um große Projekte zu debuggen, wird empfohlen, dass die Arbeit mit dem Besitzer der Erweiterung, die sie mit dieser Option für das Debuggen kompatibel zu machen.

Wenn Sie der Besitzer eines älteren C/C++-EE-Add-in oder eine benutzerdefinierte C/C++-Schnellansicht sind, finden Sie weitere Informationen über die Entscheidung für die Erweiterung in einem Arbeitsprozess zu laden, auf die [Concord Erweiterbarkeit Beispiele Wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Sie erhalten auch eine [die benutzerdefinierte Schnellansicht Beispiel C/C++-](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).