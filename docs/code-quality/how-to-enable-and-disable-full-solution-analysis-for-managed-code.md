---
title: "Vorgehensweise: Aktivieren und deaktivieren Sie vollständige Projektmappenanalyse für verwalteten Code | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 94cda949a713a773e5586e5b1ef284c6ba54839c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren und deaktivieren Sie vollständige Projektmappenanalyse für verwalteten Code
> [!NOTE]
>  Dieses Thema gilt nur für Visual Studio 2015 Update 3 RC und höher.  
  
 *Vollständige projektmappenanalyse* ist ein Feature von Visual Studio, mit dem Sie auswählen, ob Sie Codeanalysefehler nur in open-Visual c# oder Visual Basic-Dateien in der Projektmappe oder in offenen und geschlossenen Visual c# oder Visual Basic-Dateien in der Projektmappe angezeigt.  
  
 Werden alle Probleme in allen Dateien zu sehen ist, zwar hilfreich kann es irritierende und sogar verlangsamen das Visual Studio sein, wenn Ihre Lösung sehr groß ist oder viele Dateien hat.  Um die Anzahl der Probleme angezeigt und Visual Studio zur Leistungssteigerung, können Sie die vollständige projektmappenanalyse deaktivieren. Diese Funktion aktivieren können einfach erneut, wenn Sie möchten.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Vollständige projektmappenanalyse aktivieren bzw. deaktivieren  
  
1.  Wählen Sie im Hauptmenü in Visual Studio, **Tools** &#124; **Optionen** zum Anzeigen der **Optionen** (Dialogfeld).  
  
2.  In der **Optionen** Dialogfeld Wählen Sie **Texteditor** &#124; **C#** oder **grundlegende** &#124; **Erweiterte**.  
  
3.  Wählen Sie die **vollständige projektmappenanalyse aktivieren** Kontrollkästchen, um vollständige projektmappenanalyse aktivieren oder deaktivieren Sie das Kontrollkästchen, um ihn zu deaktivieren. Wählen Sie die **OK** Schaltfläche, wenn Sie fertig sind.  
  
     ![Vollständige Lösung Analysis Kontrollkästchen zu aktivieren. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Ergebnisse der aktivieren und deaktivieren die vollständige projektmappenanalyse  
 Im folgenden Screenshot sehen Sie die Ergebnisse, wenn vollständige projektmappenanalyse aktiviert ist. Alle Fehler und bei der Codeanalyse in *alle* der Dateien in der Projektmappe angezeigt, unabhängig davon, ob die Dateien geöffnet sind.  
  
 ![Vollständige projektmappenanalyse aktiviert. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 Der folgende Screenshot zeigt die Ergebnisse aus derselben Projektmappe nach dem Deaktivieren von vollständige projektmappenanalyse. Nur Fehler und bei der Codeanalyse in öffnen Lösung, die Dateien werden in der Fehlerliste.  
  
 ![Vollständige projektmappenanalyse deaktiviert. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Vollständige projektmappenanalyse deaktiviert automatisch  
 Wenn Visual Studio ermittelt, dass 200MB oder weniger Systemspeicher verfügbar ist, automatisch deaktiviert wird, vollständige projektmappenanalyse (sowie einige andere Funktionen), wenn diese Option aktiviert ist. In diesem Fall wird eine Warnung angezeigt, Sie über diese informiert. Eine Schaltfläche können Sie die vollständige projektmappenanalyse erneut zu aktivieren, wenn Sie dies tun möchten.  
  
 ![Text der Warnung bis zum Anhalten der vollständige projektmappenanalyse](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Weitere Informationen  
 Standardmäßig wird vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual c#.  
  
 Visual Studio Update 3 RC umfasst eine verbesserte Code Analyzer diagnostische v2-Modul, die erheblich reduziert die speicherauslastung und verringert CPU-Zeit im Leerlauf befindet, auch wenn die vollständige projektmappenanalyse aktiviert ist.