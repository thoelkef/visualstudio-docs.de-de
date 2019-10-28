---
title: Übersicht über die Analyse von verwaltetem Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33ab4a000fac75c51c32e8a6d37de62e006160b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610071"
---
# <a name="code-analysis-for-managed-code-overview"></a>Übersicht über die Analyse von verwaltetem Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Codeanalyse für verwalteten Code analysiert verwaltete Assemblys und erstellt einen Bericht mit Informationen zu diesen Assemblys, in dem z. B. Verletzungen der in den Microsoft .NET Framework-Entwurfsrichtlinien festgelegten Programmierungs- und Entwurfsregeln gemeldet werden.

 Das Analysetool stellt die während einer Analyse durchgeführten Prüfungen als Warnmeldungen dar. In diesen Warnmeldungen werden alle relevanten Probleme im Zusammenhang mit Programmierung und Entwurf benannt. Nach Möglichkeit wird außerdem angegeben, wie das jeweilige Problem gelöst werden kann.

## <a name="ide-integrated-development-environment-integration"></a>Integration in die integrierte Entwicklungsumgebung (Integrated Development Environment – IDE)
 Entwickler können die Codeanalyse im Projekt entweder automatisch oder manuell ausführen.

 Wenn die Codeanalyse bei jeder Projekterstellung ausgeführt werden soll, aktivieren Sie auf der Eigenschaftenseite des Projekts das Kontrollkästchen **Enable Code Analysis on Build (defines CODE_ANALYSIS constant)** (Codeanalyse beim Erstellen aktivieren (definiert die CODE_ANALYSIS-Konstante)). Weitere Informationen finden Sie unter [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Um die Codeanalyse in einem Projekt manuell auszuführen, klicken Sie im Menü **Analysieren** auf **Codeanalyse für _Projektname_** ausführen. Weitere Informationen finden Sie unter [Vorgehensweise: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Regelsätze
 Codeanalyseregeln für verwalteten Code werden in *Regelsätze* gruppiert. Sie können einen Standardregelsatz von Microsoft verwenden, oder Sie können eine benutzerdefinierte Regel erstellen, um eine bestimmte Anforderung zu erfüllen. Weitere Informationen finden Sie unter [Using Rule Sets to Group Code Analysis Rules (Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln)](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>Unterdrückung im Quellcode
 Es kann häufig hilfreich sein anzugeben, dass eine Warnung nicht zutreffend ist. Entwickler und andere Personen, die später möglicherweise den Code überprüfen, wissen dann, dass eine Warnung untersucht und unterdrückt oder ignoriert wurde.

 Die Unterdrückung von Warnungen im Quellcode wird durch benutzerdefinierte Attribute implementiert. Fügen Sie zum Unterdrücken einer Warnung das Attribut `SuppressMessage` zum Quellcode hinzu, wie im folgenden Beispiel dargestellt:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Weitere Informationen finden Sie unter [Suppress Warnings By Using the SuppressMessage Attribute (Unterdrücken von Warnungen mithilfe des SuppressMessage-Attributs)](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Ausführen der Codeanalyse im Rahmen der Eincheckrichtlinien
 In einer Organisation ist es sinnvoll festzulegen, dass beim Einchecken stets bestimmte Richtlinien beachtet werden müssen. Insbesondere die folgenden Richtlinien sollten eingehalten werden:

- Code muss beim Einchecken frei von Buildfehlern sein.

- Die Codeanalyse muss als Teil des letzten Builds ausgeführt worden sein.

  Die Einhaltung dieser Vorgaben können Sie durch das Definieren von Eincheckrichtlinien gewährleisten. Weitere Informationen finden Sie unter [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Team Build-Integration
 Sie können die integrierten Features des Buildsystems verwenden, um das Analysetool im Rahmen des Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Build the application (Erstellen der Anwendung)](/azure/devops/pipelines/index).

## <a name="see-also"></a>Siehe auch
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [Gewusst wie: Enable and Disable Automatic Code Analysis (Vorgehensweise: Aktivieren und Deaktivieren der automatischen Codeanalyse)](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
