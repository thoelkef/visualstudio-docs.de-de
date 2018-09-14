---
title: 'CA2103: Imperative Sicherheit überprüfen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f8975e3118e9907bf4688efe93dc60646b6d80b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547691"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Imperative Sicherheit überprüfen

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode verwendet imperative Sicherheit und erstellt möglicherweise die Berechtigung mit Zustandsinformationen oder Rückgabewerten, die sich ändern können, während die Forderung wirksam ist.

## <a name="rule-description"></a>Regelbeschreibung
 Imperativer Sicherheit verwendet verwaltete Objekte angeben, Berechtigungen und Sicherheitsaktionen während der codeausführung, im Vergleich zu deklarative Sicherheit, der Attribute verwendet, um Berechtigungen und Aktionen in den Metadaten zu speichern. Imperativer Sicherheit ist sehr flexibel, da es sich bei den Zustand eines Objekts Berechtigungen festlegen und wählen Sie die Sicherheitsaktionen mithilfe von Informationen, die bis zur Laufzeit nicht verfügbar ist. Zusammen mit, die aber auch Flexibilität das Risiko, das die Runtime-Informationen, die Sie verwenden, um zu bestimmen, dass der Zustand einer Berechtigung nicht bleibt unverändert, solange die Aktion ausgeführt wird.

 Verwenden Sie, wenn irgend möglich, deklarative Sicherheit. Deklarative Befehle sind einfacher zu verstehen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie die Anforderungen imperative Sicherheit, um sicherzustellen, dass der Zustand der Berechtigung nicht auf den Informationen abhängig ist, die sich ändern können, solange die Berechtigung verwendet wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Berechtigung zum Ändern von Daten nicht abhängig ist. Allerdings ist es besser, die die imperative Forderung in den entsprechenden deklarative zu ändern.

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Daten und Modellierung](/dotnet/framework/data/index)