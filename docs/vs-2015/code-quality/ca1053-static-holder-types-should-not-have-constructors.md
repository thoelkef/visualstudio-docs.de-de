---
title: 'CA1053: statische Halter Typen sollten keine Konstruktoren aufweisen. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7de098d264dbdd6d7d9daea385de2e03d4e1ba35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653822"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statische Haltertypen sollten keine Konstruktoren aufweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder verschachtelter öffentlicher Typ deklariert nur statische Member und verfügt über einen öffentlichen oder geschützten Standardkonstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Der Konstruktor ist überflüssig, da zum Aufrufen statischer Member keine Instanz des Typs erforderlich ist. Da der Typ nicht über nicht statische Member verfügt, bietet das Erstellen einer-Instanz keinen Zugriff auf die Member des Typs.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Standardkonstruktor, oder legen Sie ihn als privat fest.

> [!NOTE]
> Einige Compiler erstellen automatisch einen öffentlichen Standardkonstruktor, wenn der Typ keine Konstruktoren definiert. Wenn dies der Fall für Ihren Typ ist, fügen Sie einen privaten Standardkonstruktor hinzu, um die Verletzung auszuschließen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Das vorhanden sein des Konstruktors deutet darauf hin, dass der Typ kein statischer Typ ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt. Beachten Sie, dass im Quellcode kein Standardkonstruktor vorhanden ist. Wenn dieser Code in eine Assembly kompiliert wird, fügt C# der Compiler einen Standardkonstruktor ein, der gegen diese Regel verstößt. Um dies zu korrigieren, deklarieren Sie einen privaten Konstruktor.

 [!code-csharp[FxCop.Design.StaticTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes/cs/FxCop.Design.StaticTypes.cs#1)]
