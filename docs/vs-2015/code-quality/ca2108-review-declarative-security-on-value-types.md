---
title: 'CA2108: Deklarative Sicherheit auf Werttypen überprüfen | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f6a17bf57f00923cfd31bd477f211ba66169672a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687369"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Deklarative Sicherheit auf Werttypen überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Werttyp wird geschützt, indem eine [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oder [Verknüpfungsaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Regelbeschreibung
 Werttypen werden zugeordnet und durch die standardmäßige Konstruktoren initialisiert werden, bevor andere Konstruktoren ausgeführt. Wenn ein Werttyp wird durch einen Demand oder LinkDemand geschützt, und der Aufrufer verfügt nicht über die Berechtigungen, die die sicherheitsüberprüfung, die keinen Konstruktor außer erfüllen standardmäßig fehl, und eine Sicherheitsausnahme ausgelöst. Der Werttyp wird nicht freigegeben. Es bleibt im Zustand "" festlegen, indem die Standard-Konstruktor. Führen Sie Sie nicht davon gehen Sie aus, dass ein Aufrufer, der eine Instanz des Werttyps übergibt, verfügt über die Berechtigung zum Erstellen oder die Instanz zugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sie können keinen Verstoß gegen diese Regel beheben, es sei denn, Sie die sicherheitsüberprüfung, von dem Typ entfernen und Verwendung methodensicherheit auf Zeilenebene an seiner Stelle überprüft. Beachten Sie, dass Aufrufer mit unzureichenden Berechtigungen Abrufen von Instanzen des Werttyps Behebung des Verstoßes auf diese Weise nicht verhindert wird. Sie müssen sicherstellen, dass eine Instanz des Werttyps, in seinem Standardzustand macht keine vertraulichen Informationen verfügbar, und kann nicht auf schädliche Weise verwendet werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können eine Warnung dieser Regel unterdrücken, wenn ein Aufrufer die Instanzen des Werttyps in seinem Standardzustand abrufen kann, ohne die Sicherheit gefährden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Bibliothek mit einem Werttyp, der gegen diese Regel verstößt. Beachten Sie, dass die `StructureManager` Typs wird davon ausgegangen, dass ein Aufrufer, eine Instanz des Werttyps übergibt, verfügt über die Berechtigung zum Erstellen oder die Instanz zugreifen.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung zeigt die Bibliotheks Schwachstelle.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Benutzerdefinierte Struktur-Konstruktor: Fehler bei Anforderung.** 
**Neue Werte SecuredTypeStructure 100 100**
**neue Werte SecuredTypeStructure 200 200**
## <a name="see-also"></a>Siehe auch
 [Linkaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
