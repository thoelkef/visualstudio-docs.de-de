---
title: Automatische Funktions Unterbrechung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1dddc235131322a61cdb0106d866b138040d8c18
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508196"
---
# <a name="automatic-feature-suspension"></a>Automatisches Anhalten von Features
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Wenn Ihr verfügbarer System Arbeitsspeicher auf 200 MB oder weniger fällt, zeigt Visual Studio im Code-Editor die folgende Meldung an.

 ![Warnungs Text zum Anhalten der vollständigen Lösungs Analyse](../code-quality/media/fsa-alert.png "FSA_Alert")

 Wenn Visual Studio eine nicht genügend Arbeitsspeicher Bedingung erkennt, werden bestimmte erweiterte Funktionen automatisch angehalten, damit Sie stabil bleiben. Wenn diese Warnmeldung für erweiterte Features angezeigt wird, funktioniert Visual Studio weiterhin wie zuvor, aber die Leistung wird geringfügig beeinträchtigt.

 Bei einem Mangel an Arbeitsspeicher tritt Folgendes auf:

- Die vollständige projektmappenanalyse für Visual c# und Visual Basic ist deaktiviert.

- Der Modus für die [Garbage Collection](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) mit niedriger Latenz für Visual c# und Visual Basic ist deaktiviert.

- Visual Studio-Caches werden geleert.

## <a name="improve-visual-studio-performance"></a>Verbessern der Leistung von Visual Studio
 Tipps und Tricks zum Verbessern der Leistung von Visual Studio beim Umgang mit großen Lösungen oder Bedingungen mit geringem Arbeitsspeicher finden Sie unter [Überlegungen zur Leistung für große Lösungen](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="full-solution-analysis-suspended"></a>Vollständige Lösungs Analyse angehalten
 Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic aktiviert und für Visual c# deaktiviert. Bei einem Mangel an Arbeitsspeicher wird die vollständige projektmappenanalyse für Visual Basic und Visual c# jedoch unabhängig von Ihren Einstellungen im Dialogfeld Optionen automatisch deaktiviert. Sie können jedoch die vollständige projektmappenanalyse erneut aktivieren, indem Sie die Schaltfläche **erneut aktivieren** auf der Info Leiste auswählen, wenn Sie angezeigt wird, indem Sie das Kontrollkästchen **vollständige projektmappenanalyse aktivieren** im Dialogfeld Optionen aktivieren oder Visual Studio neu starten. Im Dialogfeld Optionen werden immer die aktuellen vollständigen projektmappenanalyse-Einstellungen angezeigt. Weitere Informationen finden Sie unter Gewusst [wie: Aktivieren und Deaktivieren der vollständigen projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC mit geringer Latenzzeit deaktiviert
 Starten Sie Visual Studio neu, um den GC-Modus mit niedriger Latenz wieder zu aktivieren.  Standardmäßig ermöglicht Visual Studio den GC-Modus mit niedriger Latenz, wenn Sie eingeben, um sicherzustellen, dass Ihre Typisierung keine GC-Vorgänge blockiert. Wenn in Visual Studio jedoch aufgrund von geringem Arbeitsspeicher die automatische anhaltewarnung angezeigt wird, ist der GC-Modus mit niedriger Latenzzeit für diese Sitzung deaktiviert. Wenn Sie Visual Studio neu starten, wird das standardmäßige GC-Verhalten erneut aktiviert. Weitere Informationen finden Sie unter <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>In Visual Studio geleerte Caches

Alle Visual Studio-Caches werden sofort geleert, werden jedoch erneut aufgefüllt, wenn Sie die aktuelle Entwicklungs Sitzung fortsetzen oder Visual Studio neu starten. Die geleerten Caches enthalten Caches für die folgenden Funktionen.

- Alle Verweise suchen

- Navigieren zu

- Hinzufügen mithilfe von

Außerdem werden Caches, die für interne Visual Studio-Vorgänge verwendet werden, ebenfalls gelöscht.

> [!NOTE]
> Die automatische Merkmals Unterbrechungs Warnung tritt nur einmal pro Lösung auf, nicht pro Sitzung. Dies bedeutet Folgendes: Wenn Sie von Visual Basic zu Visual c# wechseln (oder umgekehrt) und auf einen anderen Arbeitsspeicher Mangel stoßen, können Sie möglicherweise eine weitere Warnung zur automatischen Funktions Unterbrechung erhalten.

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Grundlagen der Garbage Collection](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Überlegungen zur Leistung für große Lösungen](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)