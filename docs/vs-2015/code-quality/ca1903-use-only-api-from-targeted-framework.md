---
title: 'CA1903: nur API aus Ziel Framework verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10649b4106a280089fd6b086167c7e92bff1300b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545248"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Nur API aus Zielframework verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1903: nur API aus Ziel Framework verwenden](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|Element|Wert|
|-|-|
|TypName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategorie|Microsoft. Portabilität|
|Unterbrechende Änderung|Unterbrechen: Wenn Sie für die Signatur eines extern sichtbaren Members oder Typs ausgelöst werden.<br /><br /> Nicht unterbrechend: beim Auslösen im Text einer Methode.|

## <a name="cause"></a>Ursache
 Ein Member oder Typ verwendet einen Member oder Typ, der in einem Service Pack eingeführt wurde, das nicht im Ziel Framework des Projekts enthalten war.

## <a name="rule-description"></a>Beschreibung der Regel
 In .NET Framework 2,0 Service Pack 1 und 2, .NET Framework 3,0 Service Pack 1 und 2 und .NET Framework 3,5 Service Pack 1 sind neue Member und Typen enthalten. Projekte, die auf die Hauptversionen des .NET Framework abzielen, können unbeabsichtigt Abhängigkeiten von diesen neuen APIs annehmen. Um diese Abhängigkeit zu verhindern, wird diese Regel für Verwendungen von neuen Membern und Typen ausgelöst, die nicht standardmäßig mit dem Ziel Framework des Projekts eingeschlossen wurden.

 **Ziel Framework-und Service Pack-Abhängigkeiten**

|Element|Wert|
|-|-|
|Wenn das Ziel Framework|Ausgelöst bei der Verwendung von Membern, die in eingeführt wurden|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|Nicht zutreffend|

 Informationen zum Ändern des Ziel-Frameworks eines Projekts finden Sie unter [Ausrichten einer bestimmten .NET Framework Version](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie alle Verwendungen des neuen Members oder Typs, um die Abhängigkeit des Service Pack zu entfernen. Wenn es sich um eine absichtliche Abhängigkeit handelt, sollten Sie entweder die Warnung unterdrücken oder diese Regel deaktivieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung aus dieser Regel, wenn dies keine absichtliche Abhängigkeit vom angegebenen Service Pack war. In dieser Situation kann die Anwendung möglicherweise nicht auf Systemen ausgeführt werden, auf denen dieses Service Pack nicht installiert ist. Unterdrücken Sie die Warnung, oder deaktivieren Sie diese Regel, wenn es sich um eine absichtliche Abhängigkeit handelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Klasse, die den Typ DateTimeOffset verwendet, der nur in .NET 2,0 Service Pack 1 verfügbar ist. In diesem Beispiel muss .NET Framework 2,0 in der Dropdown Liste Ziel Framework in den Projekteigenschaften ausgewählt worden sein.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die zuvor beschriebene Verletzung behoben, indem die Verwendungen des DateTimeOffset-Typs durch den DateTime-Typ ersetzt werden.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 [Portabilitäts Warnungen](../code-quality/portability-warnings.md) für [eine bestimmte .NET Framework Version](../ide/targeting-a-specific-dotnet-framework-version.md)
