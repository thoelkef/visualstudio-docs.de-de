---
title: 'CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cb5e3fe219d6ed8d976cf4bf03b3411dd5855a5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189773"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Name, der einen Namespace, einen Typ oder ein Element Schnittstellenmembers entspricht ein reserviertes Schlüsselwort in einer Programmiersprache.

## <a name="rule-description"></a>Regelbeschreibung
 Bezeichner für Namespaces, Typen und virtuelle und Schnittstellenmember sollten nicht übereinstimmen, Schlüsselwörter, die von Sprachen definiert sind, die die common Language Runtime abzielen. Abhängig von der Sprache, die verwendet wird und das Schlüsselwort, können c#-Compilerfehlern und Mehrdeutigkeiten bei die Bibliothek mit erschweren.

 Diese Regel überprüft für Schlüsselwörter in den folgenden Sprachen:

-   Visual Basic

-   C#

-   C++/CLI

 Groß-/Kleinschreibung Vergleich wird zum [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Schlüsselwörter und Vergleich Groß-/Kleinschreibung wird für die anderen Sprachen verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Namen, der nicht angezeigt wird, in der Liste der Schlüsselwörter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können eine Warnung dieser Regel unterdrücken, wenn Sie sicher sind, dass der Bezeichner nicht Benutzer der API verwechselt werden und die Bibliothek in alle verfügbaren Sprachen verwendbar ist die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].



