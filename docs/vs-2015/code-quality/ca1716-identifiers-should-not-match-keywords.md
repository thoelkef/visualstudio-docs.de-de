---
title: 'CA1716: Bezeichner sollten nicht mit Schlüsselwörtern vergleichen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543701"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Namespace, eines Typs oder eines Viritual oder Schnittstellenmembers stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein.

## <a name="rule-description"></a>Beschreibung der Regel
 Bezeichner für Namespaces, Typen und virtuelle Elemente und Schnittstellenmember sollten nicht mit Schlüsselwörtern verglichen werden, die von Sprachen definiert werden, die auf die Common Language Runtime abzielen. Abhängig von der verwendeten Sprache und dem Schlüsselwort können Compilerfehler und Mehrdeutigkeiten die Verwendung der Bibliothek erschweren.

 Diese Regel überprüft Schlüsselwörter in den folgenden Sprachen:

- Visual Basic

- C#

- C++/CLI

  Der Vergleich ohne Berücksichtigung der Groß-/Kleinschreibung wird für [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Schlüsselwörter verwendet, und für die anderen Sprachen wird die Groß-/Kleinschreibung beachtet

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Namen aus, der nicht in der Liste der Schlüsselwörter angezeigt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können eine Warnung aus dieser Regel unterdrücken, wenn Sie davon überzeugt sind, dass der Bezeichner die Benutzer der API nicht verwechselt und die Bibliothek in allen verfügbaren Sprachen in verwendet werden kann [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
