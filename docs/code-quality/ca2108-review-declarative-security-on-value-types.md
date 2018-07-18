---
title: 'CA2108: Deklarative Sicherheit auf Werttypen überprüfen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa2ed7050ff7b804d3224390393c3c860bc25c30
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916037"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Deklarative Sicherheit auf Werttypen überprüfen
|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Werttyp wird durch gesichert eine [Daten und Modellierung](/dotnet/framework/data/index) oder [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Regelbeschreibung
 Werttypen werden zugeordnet und durch Standardkonstruktoren initialisiert werden, bevor die anderen Konstruktoren ausgeführt. Wenn ein Werttyp wird durch eine Forderung oder LinkDemand gesichert, und der Aufrufer verfügt nicht über die Berechtigungen, die die sicherheitsüberprüfung, einem beliebigen anderen Konstruktor außer erfüllen standardmäßig fehl, und eine Sicherheitsausnahme ausgelöst. Der Werttyp wird nicht freigegeben. Es bleibt in den Zustand von seinem Standardkonstruktor festgelegt. Führen Sie Sie nicht davon gehen Sie aus, dass ein Aufrufer, der eine Instanz des Werttyps übergibt, verfügt über die Berechtigung zum Erstellen oder die Instanz zugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Einen Verstoß gegen diese Regel kann nicht behoben werden, es sei denn, Sie die sicherheitsüberprüfung von dem Typ entfernen und Verwendung methodensicherheit auf Zeilenebene an seiner Stelle überprüft. Beachten Sie, dass Aufrufer mit unzureichenden Berechtigungen Abrufen von Instanzen des Werttyps korrigieren und die Verletzung auf diese Weise nicht verhindert werden. Sie müssen sicherstellen, dass eine Instanz des Werttyps in seinem Standardzustand nicht vertrauliche Informationen verfügbar machen, und kann nicht auf schädliche Weise verwendet werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können eine Warnung dieser Regel unterdrücken, wenn einer der Aufrufer Instanzen des Werttyps in seinem Standardzustand abrufen kann, ohne die Sicherheit gefährden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Bibliothek mit einem Werttyp, der mit dieser Regel verletzt. Beachten Sie, dass die `StructureManager` Typs wird davon ausgegangen, dass ein Aufrufer, eine Instanz des Werttyps übergibt, verfügt über die Berechtigung zum Erstellen oder die Instanz zugreifen.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung zeigt diese Schwäche der Bibliothek.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

 Folgende Ergebnisse werden zurückgegeben:

 **Benutzerdefinierte strukturkonstruktors: Fehler bei der Anforderung. ** 
 **Neue Werte SecuredTypeStructure 100 100**
**neue Werte SecuredTypeStructure 200 200**
## <a name="see-also"></a>Siehe auch
 [Verknüpfen von Forderungen](/dotnet/framework/misc/link-demands) [Daten und Modellierung](/dotnet/framework/data/index)