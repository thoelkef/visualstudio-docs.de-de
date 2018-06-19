---
title: Grafik-API und einer Speicherstatistik | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48c8ed3c8c2ebffc57ac46e987dbc37950cba0fd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481527"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik-API und einer Speicherstatistik
<!-- VERSIONLESS -->
Visual Studio-2017 und mehr Unterstützung die Grafik-API-Statistiken und einer Speicherstatistik Tools.  Diese beiden Tools können Sie verschiedene Bits von Informationen zur Verwendung der Direct3D-API als auch GPU-Speicherverbrauch verschiedene Ressourcen anzeigen.

## <a name="graphics-api-statistics"></a>Grafik-API-Statistik
Die Grafik-API-Statistiken in Visual Studio-Grafikdiagnose können Sie anzeigen, alle Direct3D-Aufrufe, die vorgenommen wurden, und die Anzahl der pro Aufruf.  Wählen Sie zum Anzeigen des Fensters die **Ansicht > API Statistiken** Menüelement.

![API-Statistik](media/gfx_diag_api_statistics.png)

Dieses Tool kann nützlich sein, in erkennen, dass die DirectX-Funktionsaufrufe, dass Sie nicht bewusst möglicherweise vornehmen möchten, oder Aufrufe, die Sie zu häufig vornehmen.

Sie können in einem Fenster auf Kopieren aller Daten als CSV-Datei, mit der rechten Maustaste, die zur weiteren Analyse in etwa wie Excel eingefügt werden können.

## <a name="memory-statistics"></a>Einer Speicherstatistik
Dieses Tool zeigt, wie viel Arbeitsspeicher der Grafiktreiber für die Ressourcen zuordnen, wird Sie in einem Frame erstellen.  Um dieses Fenster anzuzeigen, wählen Sie die **Ansicht > einer Speicherstatistik** Menüelement.

![Einer Speicherstatistik](media/gfx_diag_memory_statistics.png)

Die **GPU-Zuordnung** Spalte zeigt die Arbeitsspeichermenge, die verwendet wird, von dem Ereignis angezeigt, der **Ereignis** Spalte.  Sie können auch auswählen, das Symbol "überwachen" ![Symbol "überwachen"](media/gfx_watch.png) zum Anzeigen der [Ressource Verlauf](graphics-event-list.md#resource-history) für das ausgewählte Ereignis.

Wie bei der API-Statistik-Tool können Sie in einem Fenster auf Kopieren aller Daten als CSV-Datei, mit der rechten Maustaste, die zur weiteren Analyse in etwa wie Excel eingefügt werden können.

## <a name="see-also"></a>Siehe auch  
[Grafikdiagnose (Debuggen DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)   
[Verlauf der Ressource](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->