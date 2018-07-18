---
title: 'CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 514a062429168592fe46112ad008d0d1f4e60a28
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914783"
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