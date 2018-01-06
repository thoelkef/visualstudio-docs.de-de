---
title: "Vorgehensweise: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Analyse | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 19d8761abea6934c59673c332ea09e8a0b4e6997
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Gewusst wie: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Codeanalyse
Entwickler können das Tool Codemetrik zum Messen von Komplexität und verwaltbarkeit des Codes verwenden, aber sie können keine Codemetrik aufrufen, als Teil einer in der Eincheckrichtlinie. Allerdings kann ein Team Codeanalyseregeln aktiviert, die überprüfen Sie die Kompatibilität des Codes mit Codemetrik-Standards und erzwingen Sie diese Regeln über Eincheckrichtlinien. Weitere Informationen zu Metriken für Code finden Sie unter der [Codemetrikwerte](../code-quality/code-metrics-values.md).  
  
 Entwickler können die Vererbungstiefe, Klassenkopplung Wartbarkeitsindex und Komplexitätsregeln zum Erzwingen von wartbarem Code mit der Codeanalyse in der Eincheckrichtlinien aktivieren. Alle vier Regeln befinden sich unter der Kategorie "Verwaltbarkeit Regeln" in der Codeanalyse Gruppenrichtlinienverwaltungs-Editor.  
  
 Kontrolle über die Administratoren der Version für [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] können die Anforderungen in der Eincheckrichtlinie Verwaltbarkeit Codeanalyseregeln hinzufügen. Diese einchecken, müssen Sie für Richtlinien Entwickler basierend auf diese regeländerungen vor dem Initiieren eines Eincheckvorgangs Codeanalyse ausgeführt.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Um den Code Analysis-Gruppenrichtlinienverwaltungs-Editor zu öffnen  
  
1.  In **Team Explorer**mit der rechten Maustaste auf das Teamprojekt, klicken Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
     Die **Quellcodeverwaltung** Dialogfeld wird angezeigt.  
  
2.  Auf der **Eincheckrichtlinie** Registerkarte, und klicken Sie auf **hinzufügen**.  
  
     Die **hinzufügen in der Eincheckrichtlinie** Dialogfeld wird angezeigt.  
  
3.  In der **Eincheckrichtlinie** Liste der **Codeanalyse** Kontrollkästchen, und klicken Sie dann auf **OK**.  
  
     Die **Code Analysis-Editor für Gruppenrichtlinien** Dialogfeld wird angezeigt.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>So aktivieren Sie die Verwaltbarkeit von Codeanalyseregeln  
  
1.  In der **Code Analysis-Editor für Gruppenrichtlinien** Dialogfeld unter **Regeleinstellungen**, erweitern Sie die **Verwaltbarkeit Regeln** Knoten.  
  
2.  Wählen Sie die Kontrollkästchen für die folgenden Regeln:  
  
    -   Die Tiefe der Vererbung: **CA1501 AvoidExcessiveInheritance** -Schwellenwert: Warnung bei einer Tiefe von mehr als 5 Ebenen  
  
    -   Komplexität: **CA1502 AvoidExcessiveComplexity** -Schwellenwert: Warnung bei mehr als 25  
  
    -   Wartbarkeitsindex: **CA1505 AvoidUnmaintainableCode** -Schwellenwert: Warnung bei weniger als 20  
  
    -   Klassenkopplungen: **CA1506 AvoidExcessiveClassCoupling** -Schwellenwert: Warnung bei mehr als 80 für eine Klasse und mehr als 30 für eine Methode  
  
    -   Wenn Sie einen Verstoß gegen eine Codeanalyseregel ein Builds verhindern möchten, wählen Sie außerdem, die **Warnung als ein Fehler behandeln** das Kontrollkästchen neben der Beschreibung der Regel.  
  
3.  Klicken Sie auf **OK**. Die neue Richtlinie gilt nun für Eincheckvorgängen.  
  
## <a name="see-also"></a>Siehe auch  
 [Codemetrikwerte](../code-quality/code-metrics-values.md)   
 [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)