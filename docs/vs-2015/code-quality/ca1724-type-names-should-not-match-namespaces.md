---
title: 'CA1724: Typnamen sollten nicht übereinstimmen, Namespaces | Microsoft-Dokumentation'
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
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 64999653e326cc99ca9b1880966406dde41ce52e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246756"
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
 Ein Typname entspricht einem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Namespacenamen in einem Vergleich Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung
 Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Klassenbibliothek definierten Namespaces übereinstimmen. Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Namen, die nicht den Namen des übereinstimmen eine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Klassenbibliothek-Namespace.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Für neue Entwicklungen keine bekannte Szenarios auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Bevor Sie die Warnung unterdrücken, sollten Sie sorgfältig, wie die Benutzer Ihrer Bibliothek mit dem entsprechenden Namen verwechselt werden können. Um den rückversand für Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.



