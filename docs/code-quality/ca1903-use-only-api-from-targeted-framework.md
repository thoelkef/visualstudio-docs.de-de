---
title: 'CA1903: Nur API aus Zielframework verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e57607cdfa8790c9b9fd4e692956f7bb823981a
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744858"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Nur API aus Zielframework verwenden.

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Wichtige – Wenn der Gültigkeit der Signatur eines extern sichtbaren Members oder Typs ausgelöst.<br /><br /> Nicht unterbrechend – Wenn im Text einer Methode ausgelöst.|

## <a name="cause"></a>Ursache
 Ein Member oder Typ wird verwendet, ein Member oder Typ, der in einem Servicepack eingeführt wurde, die nicht mit dem Zielframework des Projekts enthalten ist.

## <a name="rule-description"></a>Regelbeschreibung
 Neue Elemente und Typen wurden in .NET Framework 2.0 Service Pack 1 und 2, .NET Framework 3.0 Servicepack 1 und 2 und .NET Framework 3.5 Servicepack 1 enthalten. Projekte, die die Hauptversionen von .NET Framework als Ziel können versehentlich Abhängigkeiten für diese neuen APIs nutzen. Um diese Abhängigkeit zu vermeiden, wird Sie mit dieser Regel für Verwendungen von neuen Membern und Typen, die nicht standardmäßig mit dem Zielframework des Projekts sind ausgelöst.

 **MSBuild-Zielframework und Service Pack-Abhängigkeiten**

|||
|-|-|
|Wenn Zielframework ist|Auslösung bei Verwendung von Membern aus|
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 Service Pack 2|
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 Service Pack 2, .NET Framework 3.0 SP1, .NET Framework 3.0 Service Pack 2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|Nicht zutreffend|

 Um das Zielframework des Projekts ändern möchten, finden Sie unter [Vorgehensweise: Eine Version von .NET als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um die Abhängigkeit des Servicepacks zu entfernen, entfernen Sie alle Verwendungen des neuen Member oder Typ. Ist dies eine absichtliche Abhängigkeit, die Warnung unterdrücken oder diese Regel deaktivieren.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel nicht, wenn dies keine absichtliche Abhängigkeit des angegebenen Servicepacks war. In diesem Fall kann Ihre Anwendung nicht auf Systemen ausgeführt werden soll, denen dieses Servicepack installiert. Unterdrücken Sie die Warnung oder diese Regel deaktivieren Sie, wenn dies beabsichtigt abhängig war.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die den Datentyp "DateTimeOffset" verwendet, die nur in .NET 2.0 Service Pack 1 verfügbar ist. Dieses Beispiel erfordert, dass .NET Framework 2.0 in der Dropdownliste das Zielframework in den Projekteigenschaften ausgewählt wurde.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Beispiel
 Im folgende Beispiel werden der zuvor beschriebenen Verstoß durch Verwendung von Typ "DateTimeOffset" ersetzen, mit dem Typ "DateTime" korrigiert.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Siehe auch

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Übersicht über .NET Framework](../ide/visual-studio-multi-targeting-overview.md)