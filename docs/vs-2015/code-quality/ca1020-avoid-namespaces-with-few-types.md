---
title: 'CA1020: Namespaces mit wenigen Typen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 81eaf2735869668b86ca8879478e3d76d77a2811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662308"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: Namespaces mit wenigen Typen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein anderer Namespace als der globale-Namespace enthält weniger als fünf Typen.

## <a name="rule-description"></a>Regelbeschreibung
 Stellen Sie sicher, dass jeder Ihrer Namespaces über eine logische Organisation verfügt und dass ein gültiger Grund für das Einfügen von Typen in einen spärlich aufgefüllten Namespace vorliegt. Namespaces sollten Typen enthalten, die in den meisten Szenarien zusammen verwendet werden. Wenn sich Ihre Anwendungen gegenseitig ausschließen, sollten sich die Typen in separaten Namespaces befinden. Der <xref:System.Web.UI>-Namespace enthält z. b. Typen, die in Webanwendungen verwendet werden, und der <xref:System.Windows.Forms>-Namespace enthält Typen, die in [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] basierten Anwendungen verwendet werden. Obwohl beide Namespaces über Typen verfügen, die Aspekte der Benutzeroberfläche steuern, sind diese Typen nicht für die Verwendung in derselben Anwendung konzipiert. Sie befinden sich daher in separaten Namespaces. Eine sorgfältige Namespace Organisation kann auch hilfreich sein, da Sie die Auffindbarkeit eines Features erhöht. Durch Untersuchen der Namespace Hierarchie sollten Bibliotheks Consumer in der Lage sein, die Typen zu finden, die eine Funktion implementieren.

> [!NOTE]
> Entwurfszeit Typen und-Berechtigungen sollten nicht in anderen Namespaces zusammengeführt werden, um diese Richtlinien einzuhalten. Diese Typen gehören in ihren eigenen Namespaces unter dem Haupt Namespace, und die Namespaces sollten jeweils mit `.Design` und `.Permissions` enden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, versuchen Sie, Namespaces, die nur einige wenige Typen enthalten, in einem einzelnen Namespace zu kombinieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Namespace keine Typen enthält, die mit den Typen in ihren anderen Namespaces verwendet werden.
