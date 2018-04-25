---
title: 'CA1020: Namespaces mit wenigen Typen vermeiden'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e01d8b3f4686c062ac16fa76a31d59b0c6cf8fe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Namespaces mit wenigen Typen vermeiden
|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein anderen Namespace als dem globalen Namespace enthält Typen, die weniger als fünf.

## <a name="rule-description"></a>Regelbeschreibung
 Stellen Sie sicher, dass jeder der Namespaces logisch organisiert und ein zulässigen Grund vorhanden ist, zum Einfügen einer in einen wenig gefüllten Namespace Typen. Namespaces sollten Typen enthalten, die in den meisten Szenarien zusammen verwendet werden. Wenn ihre Anwendungen gegenseitig sind, sollten die Typen in separaten Namespaces befinden. Z. B. die <xref:System.Web.UI> -Namespace enthält Typen, die in Webanwendungen verwendet werden und die <xref:System.Windows.Forms> -Namespace enthält Typen, die in verwendet werden [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-basierenden Anwendungen. Obwohl beide Namespaces Typen, die Aspekte der Benutzeroberfläche steuern enthalten, sind diese Typen nicht für die Verwendung in der gleichen Anwendung entwickelt. Aus diesem Grund befinden sie sich in separaten Namespaces. Eine sorgfältige Namespace Organisation kann auch hilfreich sein, da es die Erkennbarkeit einer Funktion erhöht. Untersuchen Sie die Namespacehierarchie, sollte Bibliotheksconsumer nach Typen suchen, die eine Funktion implementieren können.

> [!NOTE]
>  Entwurfszeittypen und Berechtigungen sollten nicht in anderen Namespaces, um die Einhaltung dieser Richtlinie zusammengeführt werden. Diese Typen gehören in ihre eigenen Namespaces unterhalb der und die Namespaces auf enden sollte `.Design` und `.Permissions`zugeordnet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, versuchen Sie, Namespaces zu kombinieren, die nur wenige Typen in einem einzelnen Namespace enthalten.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn der Namespace keine Typen enthalten, die mit den Typen in den anderen Namespaces verwendet werden.