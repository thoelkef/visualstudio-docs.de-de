---
title: Grundlagen zu Ressourcenkonflikt-Datenwerten| Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c06722e9270269ca674370d5bf8b1925d850ce00
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477404"
---
# <a name="understand-resource-contention-data-values"></a>Grundlagen zu Ressourcenkonflikt-Datenwerten

Bei der Profilerstellung für Ressourcenkonflikte werden immer dann ausführliche Aufruflisteninformationen gesammelt, wenn konkurrierende Threads in einer Anwendung auf den Zugriff auf eine gemeinsam genutzte Ressource warten müssen.

Ressourcenkonfliktberichte enthalten für die Module, Funktionen, Quellcodezeilen und Anweisungen, in denen die Verzögerung aufgetreten ist, die Gesamtanzahl von Konflikten sowie die Gesamtwartezeit für eine Ressource.

- Inklusive Werte geben Aufschluss über die Gesamtanzahl von Konflikten (sortiert nach Ressourcenkonflikten), aufgrund derer die Verzögerung für die Funktion aufgetreten ist, sowie über die Gesamtwartezeit der Funktion.  In den inklusiven Werten sind auch Konflikte enthalten, die durch untergeordnete, von der Funktion aufgerufene Funktionen verursacht wurden.

- Exklusive Werte geben nur Aufschluss über die Anzahl von Konflikten, die die Verzögerung einer Funktion zur Folge hatten und durch Code im Funktionstext verursacht wurden. Von untergeordneten Funktionen verursachte Konflikte werden nicht berücksichtigt. Die exklusive Zeit für die Funktion enthält auch nur die Wartezeiten, die von Anweisungen im Funktionsrumpf verursacht wurden.

Die Ansichten des Ressourcenkonfliktberichts enthalten auch Zeitachsendiagramme mit den einzelnen Konfliktereignissen im Zeitverlauf und die Aufruflisten, von denen das Ereignis erstellt wurde. Weitere Informationen finden Sie in einem der folgenden Themen:

- [Threaddetailansicht](../profiling/thread-details-view-contention-data.md)

- [Ressourcendetailansicht](../profiling/resource-details-view-contention-data.md)

Weitere Informationen zum zweiten Modus der Parallelitätsprofilerstellung finden Sie unter [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md).