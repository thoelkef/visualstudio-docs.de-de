---
title: "&#220;bersicht &#252;ber die Analyse von verwaltetem Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectpropertypages.codeanalysis"
helpviewer_keywords: 
  - "Codeanalyse, verwalteter Code"
  - "verwalteter Code, Codeanalyse"
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 35
caps.handback.revision: 35
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#220;bersicht &#252;ber die Analyse von verwaltetem Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Codeanalyse für verwalteten Code analysiert verwaltete Assemblys und erstellt einen Bericht mit Informationen zu diesen Assemblys, in dem z. B. Verletzungen der in den Microsoft .NET Framework\-Entwurfsrichtlinien festgelegten Programmierungs\- und Entwurfsregeln gemeldet werden.  
  
 Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar.  In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.  
  
## Integration in die integrierte Entwicklungsumgebung \(Integrated Development Environment – IDE\)  
 Entwickler können die Codeanalyse im Projekt entweder automatisch oder manuell ausführen.  
  
 Wenn die Codeanalyse bei jeder Projekterstellung ausgeführt werden soll, aktivieren Sie auf der Eigenschaftenseite des Projekts das Kontrollkästchen **Codeanalyse beim Erstellen aktivieren \(definiert die CODE\_ANALYSIS\-Konstante\)**.  Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Um die Codeanalyse in einem Projekt manuell auszuführen, klicken Sie im Menü **Analysieren** auf **Codeanalyse für *ProjectName* ausführen.** Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## Regelsätze  
 Codeanalyseregeln für verwalteten Code werden in *Regelsätzen* gruppiert.  Sie können einen Standardregelsatz von Microsoft verwenden, oder Sie können eine benutzerdefinierte Regel erstellen, um eine bestimmte Anforderung zu erfüllen.  Weitere Informationen finden Sie unter [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## Unterdrückung im Quellcode  
 Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist.  Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.  
  
 Die Unterdrückung von Warnungen im Quellcode wird durch benutzerdefinierte Attribute implementiert.  Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Weitere Informationen finden Sie unter [Unterdrücken von Warnungen mithilfe des SuppressMessage\-Attributs](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien  
 In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen.  Insbesondere die folgenden Richtlinien sollten eingehalten werden:  
  
-   Code muss beim Einchecken frei von Buildfehlern sein.  
  
-   Die Codeanalyse muss als Teil des letzten Builds ausgeführt worden sein.  
  
 Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten.  Weitere Informationen finden Sie unter [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## Team Build\-Integration  
 Sie können die integrierten Features des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen.  Weitere Informationen finden Sie unter [Erstellen der Anwendung](../Topic/Build%20the%20application.md).  
  
## Siehe auch  
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Gewusst wie: Aktivieren und Deaktivieren der automatischen Codeanalyse](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)