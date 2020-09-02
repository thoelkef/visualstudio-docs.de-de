---
title: 'Vorgehensweise: Aktivieren und Deaktivieren der vollständigen projektmappenanalyse für verwalteten Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646281"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Gewusst wie: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Dieses Thema gilt nur für Visual Studio 2015 Update 3 RC und höher.

 Die *vollständige projektmappenanalyse* ist ein Visual Studio-Feature, mit dem Sie auswählen können, ob Code Analyse Probleme nur in Open Visual c#-oder Visual Basic Dateien in der Projekt Mappe oder in offenen und geschlossenen Visual c#-oder Visual Basic-Dateien in der Projekt Mappe angezeigt werden.

 Obwohl es sinnvoll ist, alle Probleme in allen Dateien zu erkennen, ist es sehr nützlich, wenn die Projekt Mappe sehr groß ist oder viele Dateien enthält.  Um die Anzahl der angezeigten Probleme einzuschränken und die Leistung von Visual Studio zu verbessern, können Sie die vollständige projektmappenanalyse deaktivieren. Wenn Sie möchten, können Sie diese Funktion problemlos wieder aktivieren.

#### <a name="to-toggle-full-solution-analysis"></a>So schalten Sie die vollständige Lösungs Analyse um

1. Wählen Sie im Hauptmenü von Visual Studio **Extras &#124;** **Optionen** aus, um das Dialogfeld **Optionen** anzuzeigen.

2. Wählen Sie im Dialogfeld **Optionen die Option** **Text-Editor** &#124; **c#** oder **Basic** &#124; **erweitert**aus.

3. Aktivieren Sie das Kontrollkästchen **vollständige projektmappenanalyse aktivieren** , um die vollständige projektmappenanalyse zu aktivieren, oder deaktivieren Sie das Kontrollkästchen Wenn Sie fertig sind, klicken Sie auf die Schaltfläche **OK** .

     ![Aktivieren Sie das Kontrollkästchen vollständige projektmappenanalyse.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Ergebnisse der Aktivierung und Deaktivierung der vollständigen projektmappenanalyse
 Im folgenden Screenshot sehen Sie die Ergebnisse, wenn die vollständige projektmappenanalyse aktiviert ist. Alle Fehler und Code Analyse Probleme in *allen* Dateien in der Projekt Mappe werden angezeigt, unabhängig davon, ob die Dateien geöffnet sind oder nicht.

 ![Vollständige projektmappenanalyse aktiviert.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 Der folgende Screenshot zeigt die Ergebnisse der gleichen Projekt Mappe nach der Deaktivierung der vollständigen projektmappenanalyse. In den Fehlerliste werden nur Fehler und Code Analyse Probleme in geöffneten Projektmappendateien angezeigt.

 ![Vollständige projektmappenanalyse deaktiviert.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Automatische Deaktivierung der vollständigen projektmappenanalyse
 Wenn Visual Studio feststellt, dass es 200 MB oder weniger System Arbeitsspeicher zur Verfügung steht, werden die vollständige projektmappenanalyse (sowie einige andere Features) automatisch deaktiviert, wenn Sie aktiviert ist. Wenn dies der Fall ist, wird eine Warnung angezeigt, die Sie darüber informiert. Mit einer Schaltfläche können Sie die vollständige projektmappenanalyse wieder aktivieren, wenn Sie dies möchten.

 ![Warnungs Text zum Anhalten der vollständigen Lösungs Analyse](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Zusätzliche Details
 Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic aktiviert und für Visual c# deaktiviert.

 Visual Studio Update 3 RC enthält ein verbessertes Tool für die Code Analyzer-Diagnose v2, das die Speicherauslastung erheblich reduziert und die CPU-Zeit in den Leerlauf verringert, auch wenn die vollständige Lösungs Analyse aktiviert ist.
