---
title: 'CA1721: Eigenschaften Namen sollten nicht mit Get-Methoden identisch sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 77ec48a1164c7065ba5033ef51eb704b8361dc1c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544455"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt andernfalls mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. Ein Typ, der eine Methode mit dem Namen "GetColor" und eine Eigenschaft mit dem Namen "Color" enthält, verstößt z. b. gegen diese Regel.

## <a name="rule-description"></a>Beschreibung der Regel
 Get-Methoden und-Eigenschaften sollten Namen aufweisen, die ihre Funktion eindeutig unterscheiden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die erforderlich ist, um eine neue Software Bibliothek kennenzulernen, und steigert das Kunden Vertrauen, dass die Bibliothek von einem Benutzer entwickelt wurde, der über Kenntnisse in der Entwicklung von verwaltetem Code verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen so, dass er nicht mit dem Namen einer Methode identisch ist, der das Präfix "Get" vorangestellt ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

> [!NOTE]
> Diese Warnung wird möglicherweise ausgeschlossen, wenn die Get-Methode durch Implementieren der IExtenderProvider-Schnittstelle verursacht wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält eine-Methode und eine-Eigenschaft, die gegen diese Regel verstoßen.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: Nach Möglichkeit Eigenschaften verwenden.](../code-quality/ca1024-use-properties-where-appropriate.md)
