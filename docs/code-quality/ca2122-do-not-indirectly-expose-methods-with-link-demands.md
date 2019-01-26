---
title: 'CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 701b44b8018e7493305c5269a38908c454889b9c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986149"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen.

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Member wurde ein [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) und wird aufgerufen, indem Sie ein Element, das keine sicherheitsüberprüfungen ausführt.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. Wenn ein Member `X` macht keine sicherheitsanforderungen der Aufrufer Code geschützt durch einen Linkaufruf, einen Aufrufer ohne die erforderliche Berechtigung verwenden, kann Aufrufe `X` auf den geschützten Member zuzugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie einen [Daten und Modellierung](/dotnet/framework/data/index) oder bei Bedarf in das Element verknüpfen, sodass es nicht mehr ungesicherten Zugriff auf den Link bei Bedarf geschützte Member bereitstellt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code seinen Aufrufern keinen Zugriff auf Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example-1"></a>Beispiel 1
 Die folgenden Beispiele zeigen eine Bibliothek, die gegen die Regel verstößt und eine Anwendung, die die Bibliothek aufzeigt. Die Beispielbibliothek bietet zwei Methoden, die zusammen die Regel verletzen. Die `EnvironmentSetting` Methode wird durch einen Linkaufruf für einen uneingeschränkten Zugriff auf Umgebungsvariablen geschützt. Die `DomainInformation` Methode macht keine sicherheitsanforderungen Aufrufer vor `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Beispiel 2
 Die folgende Anwendung ruft die ungeschützten Bibliothekmembers.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)
- [Daten und Modellierung](/dotnet/framework/data/index)