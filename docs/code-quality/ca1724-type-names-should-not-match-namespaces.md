---
title: 'CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c178558743ca69fb3b62eccaf8164e4b49167ad3
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547567"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen
|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typname entspricht einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Namespacenamen in einem Vergleich Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung
 Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Klassenbibliothek definierten Namespaces übereinstimmen. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Namen, die nicht den Namen des übereinstimmen eine [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Klassenbibliothek-Namespace.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Für neue Entwicklungen keine bekannte Szenarios auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Bevor Sie die Warnung unterdrücken, sollten Sie sorgfältig, wie die Benutzer Ihrer Bibliothek mit dem entsprechenden Namen verwechselt werden können. Um den rückversand für Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.