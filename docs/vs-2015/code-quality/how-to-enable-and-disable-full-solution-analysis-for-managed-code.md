---
title: 'Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse für verwalteten Code | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: af0aae4020182f6414d44a2004f98a6fc0df23ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221870"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Vorgehensweise: Aktivieren und Deaktivieren der vollständigen Projektmappenanalyse für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
>  Dieses Thema gilt nur für Visual Studio 2015 Update 3 RC und höher.  
  
 *Vollständige projektmappenanalyse* ist ein Visual Studio-Feature, können Sie auswählen, ob bei der Codeanalyse nur in open-Visual c# oder Visual Basic-Dateien in der Projektmappe oder in einer offenen und geschlossenen Visual c# oder Visual Basic-Dateien in der Projektmappe angezeigt.  
  
 Während nützlich dass Sie alle Probleme in allen Dateien ist, kann er störend und sogar Visual Studio verlangsamt werden, wenn Ihre Lösung sehr groß ist oder viele Dateien weist.  Um die Anzahl der angezeigten Probleme, und Verbessern der Leistung von Visual Studio, können Sie die vollständige projektmappenanalyse deaktivieren. Sie können einfach diese Funktion wieder aktivieren, wenn Sie möchten.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Zum Umschalten der vollständigen projektmappenanalyse  
  
1.  Wählen Sie im Hauptmenü in Visual Studio **Tools** &#124; **Optionen** zum Anzeigen der **Optionen** Dialogfeld.  
  
2.  In der **Optionen** Dialogfeld wählen **Text-Editor** &#124; **c#** oder **grundlegende** &#124; **erweitert**.  
  
3.  Wählen Sie die **vollständige projektmappenanalyse aktivieren** Kontrollkästchen, um die vollständige projektmappenanalyse aktivieren oder deaktivieren Sie das Kontrollkästchen, um es zu deaktivieren. Wählen Sie die **OK** Schaltfläche, wenn Sie fertig sind.  
  
     ![Aktivieren Sie die vollständige Lösung Analysis-Kontrollkästchen. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Ergebnisse der aktivieren und Deaktivieren der vollständigen projektmappenanalyse  
 Im folgenden Screenshot sehen Sie die Ergebnisse, wenn vollständige projektmappenanalyse aktiviert ist. Alle Fehler und bei der Codeanalyse in *alle* der Dateien in der Projektmappe angezeigt, unabhängig davon, ob die Dateien geöffnet oder nicht sind.  
  
 ![Vollständige projektmappenanalyse aktiviert. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 Der folgende Screenshot zeigt die Ergebnisse aus der gleichen Projektmappe nach dem Deaktivieren der vollständigen projektmappenanalyse. Nur Fehler und bei der Codeanalyse in öffnen Sie in der Fehlerliste Lösung, die Dateien angezeigt werden.  
  
 ![Vollständige projektmappenanalyse deaktiviert. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Deaktivieren automatisch vollständige projektmappenanalyse  
 Wenn Visual Studio ermittelt, dass 200MB oder weniger Arbeitsspeicher verfügbar ist, automatisch deaktiviert wird, vollständige projektmappenanalyse (sowie einige andere Features) wird aktiviert. In diesem Fall wird eine Warnung angezeigt, Sie über diese informiert. Eine Schaltfläche können Sie die vollständige projektmappenanalyse erneut zu aktivieren, wenn Sie dies tun möchten.  
  
 ![Anhalten der vollständigen projektmappenanalyse Warntext](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Weitere Informationen  
 Standardmäßig ist die vollständige projektmappenanalyse für Visual Basic aktiviert und deaktiviert für Visual c#.  
  
 Visual Studio Update 3 RC enthält ein erweiterter Code-Analyzer-Diagnose v2-Modul, das erheblich verringert die speicherauslastung und CPU-Zeit im Leerlauf, verringert wird, auch wenn vollständige projektmappenanalyse aktiviert ist.



