---
title: 'CA1020: Namespaces mit wenigen Typen vermeiden.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 396208b9594e46aa179c3eebddc5a552ce0fca3c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779533"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Namespaces mit wenigen Typen vermeiden.

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein anderen Namespace als dem globalen Namespace enthält weniger als fünf Typen.

## <a name="rule-description"></a>Regelbeschreibung

Stellen Sie sicher, dass jeder der Namespaces logisch organisiert ist, ist und dass ein triftiger Grund zum Einfügen einer in einen wenig gefüllten Namespace Typen. Namespaces sollten Typen enthalten, die in den meisten Fällen zusammen verwendet werden. Wenn ihre Anwendungen gegenseitig exklusiv sind, sollten die Typen in verschiedenen Namespaces befinden. Z. B. die <xref:System.Web.UI> -Namespace enthält Typen, die in Webanwendungen verwendet werden und die <xref:System.Windows.Forms> -Namespace enthält Typen, die verwendet werden [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-Anwendungen. Obwohl beide Namespaces Typen, die Aspekte der Benutzeroberfläche steuern verfügen, sind diese Typen nicht für die Verwendung in der gleichen Anwendung konzipiert. Aus diesem Grund befinden sie sich in verschiedenen Namespaces. Eine sorgfältige Namespace-Organisation kann auch hilfreich sein, da es sich um die Auffindbarkeit einer Funktion erhöht. Untersuchen Sie die Namespacehierarchie, sollte Bibliotheksconsumer nach Typen suchen, die eine Funktion implementieren können.

> [!NOTE]
> Design-Time-Typen und -Berechtigungen sollten nicht in anderen Namespaces zur Einhaltung dieser Richtlinie zusammengeführt werden. Diese Typen gehören in ihre eigenen Namespaces unterhalb Ihrer, und die Namespaces enden sollte `.Design` und `.Permissions`bzw.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, versuchen Sie, Namespaces, die nur wenige Typen in einem einzigen Namespace enthalten.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher ist, eine Warnung dieser Regel zu unterdrücken, wenn der Namespace keine Typen enthalten, die mit den Typen in den anderen Namespaces verwendet werden.