---
title: 'CA2108: Deklarative Sicherheit auf Werttypen überprüfen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: c62704a99e5952c313c4ba11a71fd234070d6df8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882233"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Deklarative Sicherheit auf Werttypen überprüfen

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein öffentlicher oder geschützter Werttyp wird geschützt, indem eine [Daten und Modellierung](/dotnet/framework/data/index) oder [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Regelbeschreibung

Werttypen werden zugeordnet und durch die standardmäßige Konstruktoren initialisiert werden, bevor andere Konstruktoren ausgeführt. Wenn ein Werttyp wird durch einen Demand oder LinkDemand geschützt, und der Aufrufer verfügt nicht über die Berechtigungen, die die sicherheitsüberprüfung, die keinen Konstruktor außer erfüllen standardmäßig fehl, und eine Sicherheitsausnahme ausgelöst. Der Werttyp wird nicht freigegeben. Es bleibt im Zustand "" festlegen, indem die Standard-Konstruktor. Führen Sie Sie nicht davon gehen Sie aus, dass ein Aufrufer, der eine Instanz des Werttyps übergibt, verfügt über die Berechtigung zum Erstellen oder die Instanz zugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Sie können keinen Verstoß gegen diese Regel beheben, es sei denn, Sie die sicherheitsüberprüfung, von dem Typ entfernen und Verwendung methodensicherheit auf Zeilenebene an seiner Stelle überprüft. Beheben den Verstoß auf diese Weise verhindert nicht, dass Aufrufer mit unzureichenden Berechtigungen Abrufen von Instanzen des Werttyps. Sie müssen sicherstellen, dass eine Instanz des Werttyps, in seinem Standardzustand macht keine vertraulichen Informationen verfügbar, und kann nicht auf schädliche Weise verwendet werden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können eine Warnung dieser Regel unterdrücken, wenn ein Aufrufer die Instanzen des Werttyps in seinem Standardzustand abrufen kann, ohne die Sicherheit gefährden.

## <a name="example-1"></a>Beispiel 1

Das folgende Beispiel zeigt eine Bibliothek mit einem Werttyp, der gegen diese Regel verstößt. Die `StructureManager` Typs wird davon ausgegangen, dass ein Aufrufer, eine Instanz des Werttyps übergibt, verfügt über die Berechtigung zum Erstellen oder die Instanz zugreifen.

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>Beispiel 2

Die folgende Anwendung zeigt die Bibliotheks Schwachstelle.

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>Siehe auch

- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)
- [Daten und Modellierung](/dotnet/framework/data/index)
