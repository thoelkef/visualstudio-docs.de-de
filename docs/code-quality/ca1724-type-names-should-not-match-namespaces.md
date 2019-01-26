---
title: 'CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: b0bd410fabbeebc05d13eaee94db79cc346881e5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989220"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typname mit einem referenzierten Namespace-Namen, die mindestens eine extern sichtbare Typen übereinstimmt. Der Vergleich wird die Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung

Benutzererstellte Typnamen sollten nicht die Namen der referenzierten Namespaces überein, die extern sichtbare Typen aufweisen. Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek reduzieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Benennen Sie den Typ, den Namen eines referenzierten Namespaces keine Übereinstimmung, die extern sichtbare Typen verfügt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Für neue Entwicklungen keine bekannte Szenarios auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Bevor Sie die Warnung unterdrücken, sollten Sie sorgfältig, wie die Benutzer Ihrer Bibliothek mit dem entsprechenden Namen verwechselt werden können. Um den rückversand für Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.