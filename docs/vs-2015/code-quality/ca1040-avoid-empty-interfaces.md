---
title: 'CA1040: Leere Schnittstellen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc785967b4e27599b4a04aeb7740b53b5076938d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960330"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Leere Schnittstellen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel aus, wenn die Schnittstelle verwendet wird, um einen Satz von Typen zum Zeitpunkt der Kompilierung zu identifizieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine leere Schnittstelle.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
