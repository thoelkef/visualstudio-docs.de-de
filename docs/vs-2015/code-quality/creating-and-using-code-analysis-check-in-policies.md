---
title: Erstellen und Verwenden von Eincheckrichtlinien für die Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2aef2183cde96bfb5faa1bb62fa341f901dd7018
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947302"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei Verwendung der Team Foundation-Versionskontrolle (TFVC) können Sie für .NET Framework-Codeprojekte sowie für systemeigene Codeprojekte (vom Typ C/C++) eines Teamprojekts eine Eincheckrichtlinie für die Codeanalyse erstellen. Die Eincheckrichtlinie der Codeanalyse kann verwendet werden, um die Qualität des in die CodeBase eingecheckten Codes zu kontrollieren und zu verbessern.  
  
 Die Richtlinie wird erfüllt, wenn der lokale Build auf dem neuesten Stand ist und die Codeanalyse für die neuesten Quelldateien ausgeführt wurde. Die im Codeprojekt aktivierten Codeanalyseregeln müssen mindestens die gleichen Regeln besitzen, die auch in der Teamprojekt-Eincheckrichtlinie definiert sind. Regeln, die in den Teamprojekteinstellungen als Fehler angegeben sind, müssen auch im Codeprojekt als Fehler angegeben werden.  
  
> [!IMPORTANT]
>  Eincheckrichtlinien für die Codeanalyse können nicht auf Websiteprojekte angewendet werden. Sie können auf Webanwendungsprojekte angewendet werden.  
  
 Eincheckrichtlinien für die Codeanalyse werden mithilfe der Teamprojekteinstellungen der [!INCLUDE[esprscc](../includes/esprscc-md.md)] erstellt. Eincheckrichtlinien werden zwar für ein Teamprojekt angegeben und erzwungen, Codeanalysen werden jedoch für einzelne Codeprojekte auf lokalen Entwicklungscomputern konfiguriert und ausgeführt. In diesem Abschnitt wird beschrieben, wie für ein Teamprojekt Eincheckrichtlinien für die Codeanalyse angegeben und wie benutzerdefinierte Codeanalyserichtlinien für verwalteten Code implementiert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Vorgehensweise: Erstellen oder Aktualisieren von Standardeincheckrichtlinien Codeanalyse-Eincheckrichtlinien](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Erläutert die Schritte zum Festlegen und Ändern einer Codeanalyserichtlinie für ein Teamprojekt.  
  
 [Implementieren von benutzerdefinierten Eincheckrichtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Erläutert die Schritte zum Erstellen eines benutzerdefinierten Regelsatzes für die Eincheckrichtlinie für ein Teamprojekt sowie die Schritte zum Synchronisieren der Codeprojekte des Teamprojekts mit der Eincheckrichtlinie.  
  
 [Versionskompatibilität für die Eincheckrichtlinien der Codeanalyse](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Erläutert Kompatibilitätsprobleme bei der Eincheckrichtlinie für die Codeanalyse zwischen unterschiedlichen Versionen von [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Erläutert die Vorgehensweise zum Hinzufügen von Wörtern und Token zu dem Wörterbuch, auf das in den Benennungsregeln für die Codeanalyse verwiesen wird.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Festlegen und Erzwingen von Quality Gates](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
