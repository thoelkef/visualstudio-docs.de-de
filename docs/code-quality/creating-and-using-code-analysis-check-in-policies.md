---
title: "Erstellen und Verwenden von Eincheckrichtlinien für die Analyse | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b16b7e9f4dba55babfc7ad2ad90affe0ca93c508
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse
Bei Verwendung der Team Foundation-Versionskontrolle (TFVC) können Sie für .NET Framework-Codeprojekte sowie für native Codeprojekte (vom Typ C/C++) eines Teamprojekts eine Eincheckrichtlinie für die Codeanalyse erstellen. Die Eincheckrichtlinie der Codeanalyse kann verwendet werden, um die Qualität des in die CodeBase eingecheckten Codes zu kontrollieren und zu verbessern.  
  
 Die Richtlinie wird erfüllt, wenn der lokale Build auf dem neuesten Stand ist und die Codeanalyse für die neuesten Quelldateien ausgeführt wurde. Die im Codeprojekt aktivierten Codeanalyseregeln müssen mindestens die gleichen Regeln besitzen, die auch in der Teamprojekt-Eincheckrichtlinie definiert sind. Regeln, die in den Teamprojekteinstellungen als Fehler angegeben sind, müssen auch im Codeprojekt als Fehler angegeben werden.  
  
> [!IMPORTANT]
>  Eincheckrichtlinien für die Codeanalyse können nicht auf Websiteprojekte angewendet werden. Sie können auf Webanwendungsprojekte angewendet werden.  
  
 Eincheckrichtlinien für die Codeanalyse werden mithilfe der Teamprojekteinstellungen der [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)] erstellt. Eincheckrichtlinien werden zwar für ein Teamprojekt angegeben und erzwungen, Codeanalysen werden jedoch für einzelne Codeprojekte auf lokalen Entwicklungscomputern konfiguriert und ausgeführt. In diesem Abschnitt wird beschrieben, wie für ein Teamprojekt Eincheckrichtlinien für die Codeanalyse angegeben und wie benutzerdefinierte Codeanalyserichtlinien für verwalteten Code implementiert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Gewusst wie: Erstellen oder Aktualisieren von Standardeincheckrichtlinien für die Codeanalyse](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Erläutert die Schritte zum Festlegen und Ändern einer Codeanalyserichtlinie für ein Teamprojekt.  
  
 [Implementieren von benutzerdefinierten Eincheckrichtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Erläutert die Schritte zum Erstellen eines benutzerdefinierten Regelsatzes für die Eincheckrichtlinie für ein Teamprojekt sowie die Schritte zum Synchronisieren der Codeprojekte des Teamprojekts mit der Eincheckrichtlinie.  
  
 [Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Erläutert Kompatibilitätsprobleme bei der Eincheckrichtlinie für die Codeanalyse zwischen unterschiedlichen Versionen von [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Erläutert die Vorgehensweise zum Hinzufügen von Wörtern und Token zu dem Wörterbuch, auf das in den Benennungsregeln für die Codeanalyse verwiesen wird.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Festlegen und Erzwingen von Quality Gates](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)