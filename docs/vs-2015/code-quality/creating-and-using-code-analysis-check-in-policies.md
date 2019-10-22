---
title: Erstellen und Verwenden von Eincheck Richtlinien für die Code Analyse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667711"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei Verwendung der Team Foundation-Versionskontrolle (TFVC) können Sie für .NET Framework-Codeprojekte sowie für systemeigene Codeprojekte (vom Typ C/C++) eines Teamprojekts eine Eincheckrichtlinie für die Codeanalyse erstellen. Die Eincheckrichtlinie der Codeanalyse kann verwendet werden, um die Qualität des in die CodeBase eingecheckten Codes zu kontrollieren und zu verbessern.

 Die Richtlinie wird erfüllt, wenn der lokale Build auf dem neuesten Stand ist und die Codeanalyse für die neuesten Quelldateien ausgeführt wurde. Die im Codeprojekt aktivierten Codeanalyseregeln müssen mindestens die gleichen Regeln besitzen, die auch in der Teamprojekt-Eincheckrichtlinie definiert sind. Regeln, die in den Teamprojekteinstellungen als Fehler angegeben sind, müssen auch im Codeprojekt als Fehler angegeben werden.

> [!IMPORTANT]
> Eincheckrichtlinien für die Codeanalyse können nicht auf Websiteprojekte angewendet werden. Sie können auf Webanwendungsprojekte angewendet werden.

 Eincheckrichtlinien für die Codeanalyse werden mithilfe der Teamprojekteinstellungen der [!INCLUDE[esprscc](../includes/esprscc-md.md)] erstellt. Eincheckrichtlinien werden zwar für ein Teamprojekt angegeben und erzwungen, Codeanalysen werden jedoch für einzelne Codeprojekte auf lokalen Entwicklungscomputern konfiguriert und ausgeführt. In diesem Abschnitt wird beschrieben, wie für ein Teamprojekt Eincheckrichtlinien für die Codeanalyse angegeben und wie benutzerdefinierte Codeanalyserichtlinien für verwalteten Code implementiert werden.

## <a name="in-this-section"></a>In diesem Abschnitt
 Gewusst [wie: Erstellen oder Aktualisieren von Standard mäßigen Eincheck Richtlinien für die Code Analyse](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Erläutert die Schritte, die Sie verwenden, um eine Code Analyse Richtlinie für ein Teamprojekt festzulegen und zu ändern.

 [Implementieren von benutzerdefinierten Eincheck Richtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Erläutert die Schritte, die Sie zum Erstellen eines benutzerdefinierten Regelsatzes für die Eincheck Richtlinie eines Teamprojekts und zum Synchronisieren der Code Projekte des Teamprojekts mit der Check-in-Richtlinie verwenden.

 [Versions Kompatibilität für Eincheck Richtlinien für die Code Analyse](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Erläutert Kompatibilitätsprobleme bei der Code Analyse bei der Überprüfung von [!INCLUDE[vstsLong](../includes/vstslong-md.md)].

 Gewusst [wie: Anpassen des Code Analyse Wörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Erläutert, wie Wörter und Token zum Wörterbuch hinzugefügt werden, auf das in den Benennungs Regeln für die Code Analyse verwiesen wird.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Festlegen und Erzwingen von Quality Gates](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Verbessern der Codequalität mit Eincheckrichtlinien für das Teamprojekt](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
