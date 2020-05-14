---
title: Grafik-API- und Speicherstatistiken | Microsoft-Dokumentation
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735579"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafik-API- und Speicherstatistiken
<!-- VERSIONLESS -->
Visual Studio 2017 und höher unterstützt die Tools für Grafik-API-Statistiken und Speicherstatistiken.  Mit diesen beiden Tools können Sie verschiedene Informationen über die Direct3D-API-Verwendung und die GPU-Speicherbelegung verschiedener Ressourcen anzeigen.

## <a name="graphics-api-statistics"></a>Grafik-API-Statistiken
Mithilfe der Grafik-API-Statistiken in Visual Studio-Grafikdiagnose können Sie alle vorgenommenen Direct3D-Aufrufe und die Anzahl der einzelnen Aufrufe anzeigen.  Um das Fenster anzuzeigen, wählen Sie das Menüelement **Anzeigen > API-Statistiken** aus.

![API-Statistiken](media/gfx_diag_api_statistics.png)

Dieses Tool kann beim Ermitteln von DirectX-Aufrufen nützlich sein, von denen Sie nicht wissen, dass sie erfolgen, oder von Aufrufen, die zu oft erfolgen.

Sie können mit der rechten Maustaste auf das Fenster klicken, um alle Daten als CSV-Werte zu kopieren und zur weiteren Analyse in ein Programm wie beispielsweise Excel einzufügen.

## <a name="memory-statistics"></a>Speicherstatistiken
Mit diesem Tool wird angezeigt, wie viel Arbeitsspeicher der Grafiktreiber für die von Ihnen in einem Frame erstellten Ressourcen reserviert.  Um dieses Fenster anzuzeigen, wählen Sie das Menüelement **Anzeigen > Speicherstatistiken** aus.

![Speicherstatistiken](media/gfx_diag_memory_statistics.png)

In der Spalte **GPU-Zuordnung** wird die Menge des Arbeitsspeichers angezeigt, der von dem in der Spalte **Ereignis** angezeigten Ereignis verwendet wird.  Sie können auch das Uhrensymbol ![](media/gfx_watch.png) auswählen, um den [Ressourcenverlauf](graphics-event-list.md#resource-history) für das ausgewählte Ereignis anzuzeigen.

Wie beim API-Statistiktool können Sie auch hier mit der rechten Maustaste auf das Fenster klicken, um alle Daten als CSV-Werte zu kopieren und zur weiteren Analyse in ein Programm wie beispielsweise Excel einzufügen.

## <a name="see-also"></a>Siehe auch
- [Grafikdiagnose (Debuggen von DirectX-Grafiken)](visual-studio-graphics-diagnostics.md)
- [Ressourcenverlauf](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->