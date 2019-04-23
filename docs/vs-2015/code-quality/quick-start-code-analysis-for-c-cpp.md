---
title: 'Schnellstart: Codeanalyse für C / C++ | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 5e334d4e081c4afcb8046e3bbe3026fc0edbb20e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099363"
---
# <a name="quick-start-code-analysis-for-cc"></a>Schnellstart: Codeanalyse für C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Qualität Ihrer Anwendung verbessern, indem Codeanalysen für C oder C++-Code regelmäßig ausgeführt werden. Damit können Sie allgemeine Probleme, Verstöße gegen guten Programmierstil oder Fehler, die nur schwer durch Tests ermittelt werden, finden. Codeanalysewarnungen unterscheiden sich von Compilerfehlern und -warnungen, da die Codeanalyse nach bestimmten Codeschemata sucht, die gültig sind, jedoch Probleme für Sie oder andere Personen bereiten können, die den Code verwenden.  
  
## <a name="in-this-topic"></a>In diesem Thema  
  
- [Konfigurieren von Regelsätzen für ein Projekt](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Ausführen der Codeanalyse](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Analysieren und Auflösen von codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Unterdrücken der Codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Erstellen von Arbeitselementen für codeanalysewarnungen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Durchsuchen und Filtern von Codeanalyseergebnissen](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="BKMK_ConfigureRuleSets"></a> Konfigurieren von Regelsätzen für ein Projekt  
  
1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektnamen, und wählen Sie dann **Eigenschaften**.  
  
2. Die folgenden Schritte sind optional:  
  
    1. In der **Konfiguration** und **Plattform** Listen, wählen Sie die Buildplattform und die Zielplattform.  
  
    2. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.  
  
        > [!NOTE]
        >  Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Der Quellcode für ein Formular oder eine Vorlage kann sowohl angezeigt als auch verwaltet werden.  
  
3. Codeanalyse ausführen jedes Mal, wenn das Projekt mit der ausgewählten Konfiguration erstellt wird, wählen die **Codeanalyse für C/C++ auf Build aktivieren** Kontrollkästchen. Sie können die Codeanalyse auch manuell ausführen, indem Sie öffnen die **analysieren** Menü auswählen und dann **Ausführen der Codeanalyse für** *ProjectName*.  
  
4. In der **diesen Regelsatz ausführen** aufzulisten, führen Sie eine der folgenden:  
  
    - Wählen Sie den Regelsatz, den Sie verwenden möchten.  
  
    - Wählen Sie  **\<durchsuchen... >** einen vorhandenen benutzerdefinierten Regelsatz anzugeben, ist nicht in der Liste.  
  
    - Definieren Sie einen benutzerdefinierten Regelsatz.  
  
         Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standard-C/C++-Regelsätze  
 Visual Studio enthält zwei Standardregelsätze für systemeigenen Code:  
  
|Regelsatz|Beschreibung|  
|--------------|-----------------|  
|Von Microsoft empfohlene Mindestregeln für eigene Projekte|Dieser Regelsatz zielt auf die kritischsten Probleme in Ihrem nativen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|  
|Von Microsoft empfohlene Regeln für eigene Projekte|Dieser Regelsatz umfasst eine Vielzahl von Problemen. Sie enthält alle Regeln in den von Microsoft empfohlenen Mindestregeln für eigene Projekte|  
  
## <a name="BKMK_Run"></a> Ausführen der Codeanalyse  
 Auf der Codeanalyseseite von den Eigenschaftenseiten des Projekts können Sie die Codeanalyse so konfigurieren, dass Sie bei jedem Erstellen des Projekts ausgeführt wird. Sie können die Codeanalyse auch manuell ausführen.  
  
 Zum Ausführen der Codeanalyse in einer Projektmappe:  
  
- Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.  
  
  Zum Ausführen der Codeanalyse in einem Projekt:  
  
- Wählen Sie im Projektmappen-Explorer den Namen des Projektes aus.  
  
- Auf der **erstellen** Menü wählen **Ausführen der Codeanalyse für** *Projektname*.  
  
  Das Projekt oder die Projektmappe wird kompiliert und Codeanalyse wird ausgeführt. Die Ergebnisse werden im Codeanalysefenster angezeigt.  
  
## <a name="BKMK_Analyze"></a> Analysieren und Auflösen von codeanalysewarnungen  
 Um eine bestimmte Warnung zu analysieren, wählen Sie den Titel der Warnung im Fenster "Codeanalyse" aus. Die Warnung wird erweitert, um weitere Informationen zu diesem Problem anzuzeigen. Wenn möglich, zeigt die Codeanalyse die Zeilennummern und Analyselogik, die zu der Warnung geführt hat. Ausführliche Informationen zur Warnung, einschließlich der möglichen Lösungen für das Problem, wählen Sie die Warnungs-Id, um das Hilfethema für diese Meldung in der MSND Bibliothek anzuzeigen.  
  
 Wenn Sie eine Warnung erweitern, wird die Codezeile, die die Warnung verursacht hat im Code-Editor von Visual Studio hervorgehoben.  
  
 Nachdem Sie das Problem verstanden haben, können Sie es in Ihrem Code beheben. Wiederholen Sie die Codeanalyse, um sicherzustellen, dass die Warnung nicht mehr im Codeanalysefenster angezeigt wird und dass die Lösung des Problems keine neuen Warnungen ausgelöst hat.  
  
> [!TIP]
>  Sie können die Codeanalyse im Codeanalysefenster erneut ausführen. Wählen Sie die **analysieren** Schaltfläche, und wählen Sie den Bereich der Analyse. Sie können die Analyse für die gesamte Projektmappe oder für ein ausgewähltes Projekt erneut ausführen.  
  
## <a name="BKMK_Suppress"></a> Unterdrücken der Codeanalysewarnungen  
 Mitunter möchten Sie möglicherweise darauf verzichten, eine Codeanalysewarnung zu korrigieren. So kann es beispielsweise vorkommen, dass das Auflösen der Warnung im Verhältnis zur Wahrscheinlichkeit, dass das Problem in einer realen Implementierung des Codes auftritt, eine zu große Bearbeitung des Codes erfordert. Oder Sie gehen davon aus, dass die für die Warnung verwendete Analyse für den jeweiligen Kontext ungeeignet ist. Sie können Warnungen unterdrücken, sodass diese nicht mehr im Codeanalysefenster angezeigt werden.  
  
 So unterdrücken Sie eine Warnung  
  
1. Wenn die ausführliche Information nicht angezeigt wird, wählen Sie den Titel der Warnung, um sie zu erweitern.  
  
2. Wählen Sie unten in der Warnung den Link **Aktionen** aus.  
  
3. Wählen Sie **Meldung unterdrücken** und wählen Sie dann **In Quelle**.  
  
   Unterdrücken einer Meldung fügt `#pragma warning (disable:`*WarningId*`)` ein, das die Warnung für die Codezeile unterdrückt.  
  
## <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Erstellen von Arbeitselementen für codeanalysewarnungen  
 Funktionen für die Arbeitsaufgabenverfolgung können Sie in Visual Studio protokollieren. Um diese Funktion verwenden zu können, müssen Sie sich mit einer Instanz von Team Foundation Server verbinden.  
  
 **Um ein Arbeitselement für eine oder mehrere Warnungen für C/C++-Code zu erstellen.**  
  
1. Klicken Sie im Codeanalysefenster die Warnungen, um sie zu erweitern und auszuwählen.  
  
2. Wählen Sie auf das Kontextmenü für die Warnungen, **Arbeitsaufgabe erstellen**, und wählen Sie dann den Arbeitselementtyp.  
  
3. Visual Studio erstellt ein einzelnes Arbeitselement für die ausgewählten Warnungen und zeigt das Arbeitselement in einem Dokumentfenster der IDE.  
  
4. Fügen Sie zusätzliche Informationen hinzu, und wählen Sie dann **Arbeitsaufgabe speichern**.  
  
## <a name="BKMK_Search"></a> Suchen und Filtern der Codeanalyseergebnisse  
 Sie können lange Listen mit Warnmeldungen durchsuchen und Warnungen in Projektmappen mit mehreren Projekten filtern.  
  
1. **Filter-Warnungen nach Titel oder Warnungs-Id**: Geben Sie das Schlüsselwort in der **Filter** Textfeld.  
  
2. **Filter-Warnungen vom Projekt**: Wählen Sie in einer Projektmappe mit mehreren Projekten ein oder mehrere Projekte in der Liste am oberen rechten Rand des Fensters des Code-Analyse. Wählen Sie den Namen der Projektmappe, um alle Warnungen anzuzeigen.  
  
3. **Filter-Warnungen nach Schweregrad**: Standardmäßig werden Codeanalysen einen Schweregrad der zugewiesen **Warnung**. Sie können den Schweregrad der eine oder mehrere Nachrichten als zuweisen **Fehler** in einer benutzerdefinierten Regel festgelegt. Wählen Sie entweder **Warnung** oder **Fehler** nur die Meldungen angezeigt, die den jeweiligen Schweregrad zugewiesen sind. Wählen Sie **alle** um alle Meldungen anzuzeigen.
