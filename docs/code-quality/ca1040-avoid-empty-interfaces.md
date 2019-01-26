---
title: 'CA1040: Leere Schnittstellen vermeiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ffdea7cadbf7bfc2803573a78fdd9bbc74b1d287
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936865"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Leere Schnittstellen vermeiden.

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die Schnittstelle keine Member deklarieren oder zwei oder mehr Schnittstellen implementieren.

## <a name="rule-description"></a>Regelbeschreibung
 Schnittstellen definieren Member, die ein Verhalten oder einen Verwendungsvertrag bereitstellen. Die durch die Schnittstelle beschriebene Funktionalität kann von jedem Typ übernommen werden, unabhängig davon, an welcher Stelle der Typ in der Vererbungshierarchie steht. Ein Typ implementiert eine Schnittstelle, indem er Implementierungen für die Member der Schnittstelle bereitstellt. Eine leere Schnittstelle definiert keine Member. Aus diesem Grund ist es keinen Vertrag zu definieren, der implementiert werden können.

 Wenn es sich bei Ihrem Entwurf leerer enthält Schnittstellen, die Typen implementieren sollen, verwenden Sie wahrscheinlich eine Schnittstelle als eine Markierung oder eine Möglichkeit, eine Gruppe von Typen zu identifizieren. Diese Identifikation zur Laufzeit erfolgt, ist die richtige Vorgehensweise zu diesem Zweck ein benutzerdefiniertes Attribut zu verwenden. Verwenden Sie das Vorhandensein oder Abwesenheit des Attributs, oder die Eigenschaften des Attributs, um die Zieltypen zu identifizieren. Wenn die ID zum Zeitpunkt der Kompilierung erfolgen muss, ist es akzeptabel, eine leere Schnittstelle verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie die Schnittstelle, oder fügen Sie Mitglieder hinzu. Wenn die leere Schnittstelle zum Bezeichnen eines Satz von Typen verwendet wird, ersetzen Sie die Schnittstelle mit einem benutzerdefinierten Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel aus, wenn die Schnittstelle verwendet wird, um einen Satz von Typen zum Zeitpunkt der Kompilierung zu identifizieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine leere Schnittstelle.

 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]