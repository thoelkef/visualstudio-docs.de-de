---
title: Kompatibilität von VisualC++ C/benutzerdefinierten Visualisierungen
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430618"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Kompatibilität von VisualC++ C/benutzerdefinierten Visualisierungen

Ab Visual Studio 2019 C++ enthält einen verbesserten Debugger, der einen externen 64-Bit-Prozess zum Hosting seiner speicherintensiven Komponenten verwendet. Im Rahmen dieses Updates müssen bestimmte Erweiterungen für die C/ExpressionC++ -Auswertung aktualisiert werden, damit Sie mit dem neuen Debugger kompatibel sind.

Wenn Sie zurzeit ein Legacy-c/C++ EE-Add-inC++ oder eine c/Custom-Schnellansicht verwenden, können Sie die Nutzung dieses externen Prozesses **deaktivieren, indem** Sie zu Extras  > **Optionen**  >  Debugging wechseln und dann **Debuggen Laden auswählen. Symbole in externem Prozess (nur nativ)** . Wenn Sie diese Option deaktivieren, wird eine beträchtliche Zunahme der Speicherauslastung innerhalb des IDE-Prozesses (devenv. exe) ausgeführt. Wenn Sie also große Projekte debuggen möchten, wird empfohlen, dass Sie mit dem Besitzer der Erweiterung arbeiten, damit er mit dieser Debugoption kompatibel ist.

Wenn Sie Besitzer eines älteren c/EE-AddC++ -ins oder einer cC++ /Custom-Schnellansicht sind, finden Sie weitere Informationen zum Abonnieren der Erweiterung in einem Workerprozess im [wiki-Erweiterungs Beispielen-wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Sie finden auch ein [Beispiel für eineC++ C/Custom-](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)Schnellansicht.