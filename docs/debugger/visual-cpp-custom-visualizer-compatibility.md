---
title: Kompatibilität mit der benutzerdefinierten Visual C- und Visual C++-Schnellansicht
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430618"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Kompatibilität mit der benutzerdefinierten Visual C- und Visual C++-Schnellansicht

Ab Visual Studio 2019 ist ein verbesserter C++-Debugger vorhanden, der einen externen 64-Bit-Prozess zum Hosten seiner speicherintensiven Komponenten verwendet. Im Rahmen dieses Updates müssen bestimmte Erweiterungen für die C- und C++-Ausdrucksauswertung aktualisiert werden, damit sie mit dem neuen Debugger kompatibel sind.

Wenn Sie derzeit ein älteres EE-Add-In für oder eine ältere benutzerdefinierte Schnellansicht für C oder C++ nutzen, können Sie diesen externen Prozess deaktivieren, indem Sie zu **Extras** > **Optionen** > **Debuggen** navigieren und **Debugsymbole in externem Prozess laden (nur nativ)** deaktivieren. Wenn Sie diese Option deaktivieren, nimmt die Arbeitsspeicherauslastung im IDE-Prozess (devenv.exe) erheblich zu. Wenn Sie große Projekte debuggen möchten, wird deshalb empfohlen, mit dem Besitzer der Erweiterung zusammenzuarbeiten, damit diese mit dieser Debugoption kompatibel ist.

Wenn Sie der Besitzer eines älteren EE-Add-Ins oder einer älteren benutzerdefinierten Schnellansicht für C oder C++ sind, finden Sie im [Wiki für Concord-Erweiterbarkeitsbeispiele](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting) weitere Informationen dazu, wie Sie das Laden Ihrer Erweiterung in einen Workerprozess aktivieren können. Sie können auch ein [Beispiel für benutzerdefinierte C- oder C++-Schnellansichten](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer) nutzen.