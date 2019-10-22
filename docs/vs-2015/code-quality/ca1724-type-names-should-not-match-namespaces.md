---
title: 'CA1724: Typnamen sollten nicht mit Namespaces identisch sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53c99e34bf253b0962d054685ce637c3849a2857
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671599"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typname entspricht einem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Namespace Namen bei einem Vergleich ohne Berücksichtigung der Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung
 Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Klassenbibliothek definierten Namespaces übereinstimmen. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Typnamen aus, der nicht mit dem Namen eines [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Klassenbibliothek-Namespace identisch ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Bei der neuen Entwicklung treten keine bekannten Szenarien auf, in denen Sie eine Warnung aus dieser Regel unterdrücken müssen. Bevor Sie die Warnung unterdrücken, sollten Sie sorgfältig überlegen, wie die Benutzer Ihrer Bibliothek durch den übereinstimmenden Namen verwechselt werden könnten. Bei Versand Bibliotheken müssen Sie möglicherweise eine Warnung aus dieser Regel unterdrücken.
