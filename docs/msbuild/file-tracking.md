---
title: Dateinachverfolgung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968066"
---
# <a name="file-tracking"></a>Dateinachverfolgung
Die Dateinachverfolgung protokolliert Aufrufe an das Windows-Dateisystem für einen Prozess und dessen untergeordnete Prozesse. Durch das Aufrufen der unten aufgeführten Funktionen wird gesteuert, wann diese Protokollierung aktiviert oder deaktiviert wird, und die zu verwendende Protokolldatei angegeben.

- [EndTrackingContext:](../msbuild/endtrackingcontext.md) Beendet der Nachverfolgung des aktuellen Kontexts.

- [ResumeTracking:](../msbuild/resumetracking.md) Setzt die Nachverfolgung nach einem Aufruf von [SuspendTracking](../msbuild/suspendtracking.md) fort.

- [SetThreadCount:](../msbuild/setthreadcount.md) Legt die Anzahl der Threads fest, die zur Nachverfolgung verwendet werden sollen.

- [StartTrackingContext:](../msbuild/starttrackingcontext.md) Startet einen neuen Nachverfolgungskontext.

- [StartTrackingContextWithRoot:](../msbuild/starttrackingcontextwithroot.md) Startet einen neuen Nachverfolgungskontext mit einem angegebenen Stamm.

- [StopTrackingAndCleanup:](../msbuild/stoptrackingandcleanup.md) Beendet die Nachverfolgung und gibt die verwendeten Ressourcen frei.

- [SuspendTracking:](../msbuild/suspendtracking.md) Hält die Nachverfolgung vorübergehend an.

- [WriteAllTLogs:](../msbuild/writealltlogs.md) Erstellt Nachverfolgungsprotokolle für alle Kontexte.

- [WriteContextTLogs:](../msbuild/writecontexttlogs.md) Erstellt ein Nachverfolgungsprotokoll für den aktuellen Kontext.