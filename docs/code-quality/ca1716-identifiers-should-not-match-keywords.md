---
title: "CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4feb6293675437307e9ebd95b13457ef7439d5e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen
|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Namen für einen Namespace, einen Typ oder ein Element Schnittstellenmembers entspricht ein reserviertes Schlüsselwort in einer Programmiersprache Ihrer Wahl.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Bezeichner für Namespaces, Typen und virtuelle und Schnittstellenmember sollten nicht übereinstimmen, Schlüsselwörter, die von Sprachen definiert werden, die die common Language Runtime abzielen. Abhängig von der Sprache, die verwendet wird und das Schlüsselwort können Compilerfehlern und -Mehrdeutigkeiten die Verwendung die Bibliothek erschweren.  
  
 Diese Regel überprüft anhand von Schlüsselwörtern in den folgenden Sprachen:  
  
-   Visual Basic  
  
-   C#  
  
-   C++/CLI  
  
 Groß-und Kleinschreibung unterschieden wird zum [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] -Schlüsselwörter und Groß-/ kleinschreibungsvergleich für die anderen Sprachen verwendet wird.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wählen Sie einen Namen, der nicht angezeigt wird, in der Liste der Schlüsselwörter.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können eine Warnung dieser Regel unterdrücken, wenn Sie überzeugt sind, dass der Bezeichner keine Benutzer der API verwirrt und, dass die Bibliothek verwendet werden, kann in allen verfügbaren Sprachen in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].