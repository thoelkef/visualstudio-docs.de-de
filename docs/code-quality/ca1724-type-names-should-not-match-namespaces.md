---
title: 'CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen'
ms.date: 09/28/2018
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
ms.openlocfilehash: bf359ffcc098fa2b5653c28da302e2777216ea5b
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860263"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen

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