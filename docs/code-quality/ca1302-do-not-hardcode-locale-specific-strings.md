---
title: 'CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e56c57343ae61709b6d5875c865857a7475363fd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550491"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode verwendet ein Zeichenfolgenliteral, das Teil des Pfads des bestimmten Systemordner darstellt.

## <a name="rule-description"></a>Regelbeschreibung
 Die <xref:System.Environment.SpecialFolder?displayProperty=fullName> -Enumeration enthält Elemente, die auf besondere Systemordner verweisen. Die Speicherorte dieser Ordner können unterschiedliche Werte aufweisen, unter verschiedenen Betriebssystemen, der Benutzer kann einige Speicherorte ändern und die Speicherorte sind lokalisiert. Ein Beispiel für einen speziellen Ordner ist der Ordner "System", "C:\WINDOWS\system32" wird auf [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] aber "C:\WINNT\system32" unter [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. Die <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Methode gibt die Speicherorte zurück, die zugeordnet werden die <xref:System.Environment.SpecialFolder> Enumeration. Die Speicherorte, die von zurückgegeben werden <xref:System.Environment.GetFolderPath%2A> werden lokalisiert und für den derzeit ausgeführten Computer geeignet.

 Diese Regel die Ordnerpfade, die mithilfe von abgerufen werden die <xref:System.Environment.GetFolderPath%2A> Methode in separate Verzeichnisebenen. Jeder String-literal wird mit den Token verglichen. Wenn eine Übereinstimmung gefunden wird, wird davon ausgegangen, dass die Methode eine Zeichenfolge erstellt, die auf das Dateisystem-Speicherort verweist, die dem Token zugeordnet ist. Verwenden Sie für Portabilität und Lokalisierbarkeit die <xref:System.Environment.GetFolderPath%2A> Methode, um die Speicherorte der besonderen Systemordner anstelle von Zeichenfolgenliteralen abzurufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Standort mithilfe der <xref:System.Environment.GetFolderPath%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn das Zeichenfolgenliteral nicht verwendet wird, finden in einem der System-Standorte, die zugeordnet wird die <xref:System.Environment.SpecialFolder> Enumeration.

## <a name="example"></a>Beispiel
 Das folgende Beispiel erstellt den Pfad des common Data Anwendungsordner, die, der drei Warnungen von dieser Regel generiert. Das Beispiel ruft dann den Pfad ab, mit der <xref:System.Environment.GetFolderPath%2A> Methode.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)