---
title: 'CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.'
ms.date: 09/28/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3554a352cb1c32879397e91dba3ce53f31a14bd0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233853"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Typnamen sollten nicht mit Namespaces identisch sein.

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typname stimmt mit einem Namespace Namen überein, auf den verwiesen wird, der einen oder mehrere extern sichtbare Typen aufweist. Beim Namensvergleich wird keine Groß-/Kleinschreibung beachtet.

## <a name="rule-description"></a>Regelbeschreibung

Vom Benutzer erstellte Typnamen sollten nicht mit den Namen von Namespaces, auf die verwiesen wird, mit extern sichtbaren Typen verglichen werden. Durch das verletzen dieser Regel kann die Benutzerfreundlichkeit der Bibliothek reduziert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Benennen Sie den Typ so um, dass er nicht mit dem Namen eines referenzierten Namespace mit extern sichtbaren Typen identisch ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Bei der neuen Entwicklung treten keine bekannten Szenarien auf, in denen Sie eine Warnung aus dieser Regel unterdrücken müssen. Bevor Sie die Warnung unterdrücken, sollten Sie sorgfältig überlegen, wie die Benutzer Ihrer Bibliothek durch den übereinstimmenden Namen verwechselt werden könnten. Bei Versand Bibliotheken müssen Sie möglicherweise eine Warnung aus dieser Regel unterdrücken.