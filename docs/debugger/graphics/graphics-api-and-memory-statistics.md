---
title: Grafik-API und Arbeitsspeicher Statistik | Microsoft-Dokumentation
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa808e76e6655c5d57108c923b19794d0398b80c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735579"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik-API und Arbeitsspeicher Statistik
<!-- VERSIONLESS -->
Visual Studio 2017 und höher unterstützen die Tools für Grafik-API-Statistiken und Arbeitsspeicher Statistiken.  Mit diesen beiden Tools können Sie verschiedene Informationen über die Direct3D-API-Verwendung sowie GPU-Speicher Belegung verschiedener Ressourcen anzeigen.

## <a name="graphics-api-statistics"></a>Grafik-API-Statistik
Mithilfe der Grafik-API-Statistik in Visual Studio Grafikdiagnose können Sie alle vorgenommenen Direct3D-Aufrufe und die Anzahl der einzelnen Aufrufe anzeigen.  Um das Fenster anzuzeigen, wählen Sie das Menü Element **> API-Statistik anzeigen** aus.

![API-Statistiken](media/gfx_diag_api_statistics.png)

Dieses Tool kann nützlich sein, um DirectX-Aufrufe zu ermitteln, die Sie möglicherweise nicht bemerken oder die Sie zu oft machen.

Sie können mit der rechten Maustaste in das Fenster klicken, um alle Daten als CSV zu kopieren, die zur weiteren Analyse in etwa Excel eingefügt werden können.

## <a name="memory-statistics"></a>Speicherstatistiken
Mit diesem Tool wird angezeigt, wie viel Arbeitsspeicher der Grafiktreiber für die von Ihnen in einem Frame erstellten Ressourcen zuordnet.  Um dieses Fenster anzuzeigen, wählen Sie das Menü Element **> Arbeitsspeicher Statistiken anzeigen** aus.

![Speicherstatistiken](media/gfx_diag_memory_statistics.png)

Die **GPU-Zuordnungs** Spalte zeigt den Umfang des Arbeitsspeichers an, der von dem in der **Ereignis** Spalte angezeigten Ereignis verwendet wird.  Sie können auch das Überwachungs Symbol ![watch Symbol ](media/gfx_watch.png) auswählen, um den [Ressourcen Verlauf](graphics-event-list.md#resource-history) für das ausgewählte Ereignis anzuzeigen.

Wie beim API Statistics-Tool können Sie auch mit der rechten Maustaste in das-Fenster klicken, um alle Daten als CSV-Datei zu kopieren, die zur weiteren Analyse in etwa Excel eingefügt werden kann.

## <a name="see-also"></a>Siehe auch
- [Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
- [Ressourcen Verlauf](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->