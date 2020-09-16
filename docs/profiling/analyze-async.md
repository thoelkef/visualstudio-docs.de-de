---
title: Analysieren der Leistung von asynchronem .NET-Code | Microsoft-Dokumentation
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: e6f690b77b7e573fdf1c54fdaeca6237c6bbc146
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037542"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analysieren der Leistung von asynchronem .NET-Code

Mit dem Tool .NET Async können Sie die Leistung von asynchronem Code in Ihrer App analysieren.

> [!NOTE]
> Das Tool .NET Async erfordert mindestens Visual Studio 2019 Version 16.7 und ein .NET-Projekt, das **async** und **await** verwendet.

## <a name="setup"></a>Setup

1. Öffnen Sie über **ALT+F2** den Leistungs-Profiler in Visual Studio.

1. Aktivieren Sie das Kontrollkästchen **.NET Async**.

   ![Ausgewähltes Tool .NET Async](../profiling/media/async-tool-selected.png "Ausgewähltes Tool .NET Async")

1. Klicken Sie auf die Schaltfläche **Start**, um das Tool auszuführen.

1. Gehen Sie nach dem Start des Tools das Szenario durch, für das Sie in Ihrer App ein Profil erstellen möchten. Klicken Sie dann auf **Sammlung beenden**, oder schließen Sie Ihre App, um die Daten anzuzeigen.

1. Nach Beendigung der Sammlung sehen Sie eine Tabelle mit den Aktivitäten, die während Ihrer Profilerstellungssitzung erfolgt sind.

   ![Angehaltenes Tool .NET Async](../profiling/media/async-tool-opened.png "Angehaltenes Tool .NET Async")

Asynchrone Ereignisse werden in Aktivitäten chronologisch organisiert. Für jede wird die Startzeit, Endzeit und Dauer angezeigt.

Jede Zeile, die einer [Aufgabe](/dotnet/api/system.threading.tasks) entspricht, wird in der Spalte **Name** bezeichnet. Für alle Aufgabennamen, die nicht aufgelöst werden können, wird die Bezeichnung **Aufgabe in** angezeigt. Darauf folgt der Name der Methode, in der die Aufgabe auftritt. Wenn eine asynchrone Aktivität nicht innerhalb der Erfassungssitzung abgeschlossen wird, wird in der Spalte **Endzeit** die Bezeichnung **Unvollständig** angezeigt.

Um eine bestimmte Aufgabe oder Aktivität weiter zu untersuchen, klicken Sie mit der rechten Maustaste auf die Zeile. Wählen Sie dann **Zur Quelldatei wechseln**, um zu ermitteln, wo in Ihrem Code diese Aktivität stattgefunden hat.

![Tool .NET Async mit ausgewählter Option „Zur Quelldatei wechseln“](../profiling/media/async-tool-gotosource.png "Ausgewählte Option „Zur Quelldatei wechseln“")

## <a name="see-also"></a>Siehe auch

- [Optimieren der Profilereinstellungen](../profiling/optimize-profiler-settings.md)