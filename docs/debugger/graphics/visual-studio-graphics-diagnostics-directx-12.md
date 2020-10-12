---
title: DirectX 12-Unterstützung in Visual Studio | Microsoft-Dokumentation
description: DirectX 12-Benutzern wird empfohlen, für eine vollständige grafische Debugoberfläche PIX on Windows zu verwenden.
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671415"
---
# <a name="directx-12-support-in-visual-studio"></a>DirectX 12-Unterstützung in Visual Studio

## <a name="directx-12-support"></a>DirectX 12-Unterstützung

Die Grafikdiagnose von Visual Studio unterstützt keine DirectX 12-Spiele. Für grafisches Debuggen mit vollständiger DirectX 12-Unterstützung empfiehlt Visual Studio *PIX on Windows*. 

PIX on Windows ist ein Tool zum Optimieren der Leistung und Debuggen mit Remotefunktionen. Es bietet sieben Hauptfeatures, die Ihre Anforderungen für grafisches Debuggen erfüllen. Debuggen und Analysieren Sie die Leistung von Direct3D 12-Grafikrendering mit GPU-Aufzeichnungen. Verwenden Sie Zeitaufzeichnungen, um Informationen zu Leistung und Threading für die gesamte CPU- und GPU-Arbeit Ihres Spiels zu erhalten. Identifizieren Sie mithilfe von Datei-E/A-Aufzeichnungen Ineffizienzen in den Datenträger-E/A-Mustern und im Paketlayout Ihres Titels.

Verbessern Sie das grafische Debuggen mit [**PIX on Windows**](https://aka.ms/PIXonWindows).

[**Laden Sie PIX on Windows herunter**](https://aka.ms/downloadPIX), oder [**sehen Sie sich die Dokumentation an**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX on Windows

PIX on Windows bietet sieben Hauptbetriebsmodi:
1. **GPU-Aufzeichnungen** zum Debuggen und Analysieren der Leistung von Direct3D 12-Grafikrendering
2. **Zeitaufzeichnungen** für Informationen zu Leistung und Threading für die gesamte CPU- und GPU-Arbeit Ihres Spiels sowie zur Nachverfolgung der GPU-Speicherauslastung
3. **Funktionszusammenfassungsaufzeichnungen** sammeln Informationen darüber, wie lange die einzelnen Funktionen ausgeführt werden und wie oft sie jeweils aufgerufen werden.
4. **Aufrufdiagrammaufzeichnungen** überwachen die Ausführung einer einzelnen Funktion
5. **Speicherbelegungsaufzeichnungen** bieten Erkenntnisse zu den Speicherbelegungen durch Ihr Spiel.
6. **Datei-E/A-Aufzeichnungen** unterstützen Sie beim Identifizieren von Ineffizienzen in den Datenträger-E/A-Mustern und im Paketlayout Ihres Titels.
7. Der **Systemmonitor** zeigt Echtzeitdaten für Indikatoren an, während das Spiel ausgeführt wird.

Eine ausführliche Videoeinführung zu PIX on Windows finden Sie [**hier**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB).
