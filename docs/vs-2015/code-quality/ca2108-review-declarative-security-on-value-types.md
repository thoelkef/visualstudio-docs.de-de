---
title: 'CA2108: deklarative Sicherheit für Werttypen überprüfen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a05b7098d75d368f893b2504f7663675611bc0ce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658725"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Deklarative Sicherheit auf Werttypen überprüfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Werttyp wird durch [Daten-, Modellierungs-](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oder Verknüpfungs Aufrufe [gesichert.](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)

## <a name="rule-description"></a>Regelbeschreibung
 Werttypen werden von ihren Standardkonstruktoren zugeordnet und initialisiert, bevor andere Konstruktoren ausgeführt werden. Wenn ein Werttyp durch einen Demand-oder LinkDemand-Wert geschützt wird und der Aufrufer nicht über die Berechtigungen verfügt, die die Sicherheitsüberprüfung erfüllen, schlägt jeder andere Konstruktor als der Standardwert fehl, und es wird eine Sicherheits Ausnahme ausgelöst. Die Zuordnung des Werttyps wird nicht aufgehoben. Sie bleibt im Zustand, der durch den Standardkonstruktor festgelegt wird. Nehmen Sie nicht an, dass ein Aufrufer, der eine Instanz des Werttyps übergibt, über die Berechtigung zum Erstellen oder zugreifen auf die Instanz verfügt

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Es ist nicht möglich, einen Verstoß gegen diese Regel zu beheben, es sei denn, Sie entfernen die Sicherheitsüberprüfung des Typs und verwenden Sicherheitsüberprüfungen auf Methoden Ebene. Beachten Sie, dass durch das Beheben des Verstoßes auf diese Weise nicht verhindert wird, dass Aufrufer mit unzureichenden Berechtigungen Instanzen des Werttyps erhalten. Sie müssen sicherstellen, dass eine Instanz des Werttyps in seinem Standardzustand keine sensiblen Informationen verfügbar macht und nicht schädlich verwendet werden kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können eine Warnung aus dieser Regel unterdrücken, wenn ein Aufrufer Instanzen des Werttyps im Standardzustand abrufen kann, ohne eine Bedrohung für die Sicherheit darstellen zu müssen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Bibliothek mit einem Werttyp, der gegen diese Regel verstößt. Beachten Sie, dass der `StructureManager` Typ annimmt, dass ein Aufrufer, der eine Instanz des Werttyps übergibt, über die Berechtigung zum Erstellen oder zugreifen auf die Instanz

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung veranschaulicht die Schwachstelle der Bibliothek.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Benutzerdefinierter Konstruktor der Struktur:** Fehler bei der Anforderung. 
**neue Werte SecuredTypeStructure 100 100** 
**neuen Werten SecuredTypeStructure 200 200**
## <a name="see-also"></a>Siehe auch
 [Verknüpfen](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) von Anforderungs [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
