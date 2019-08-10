---
title: 'CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0b3789b5e786038c2bf1fe5e823a1b0fb4f7a7c9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922729"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden.

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Methode verwendet ein zeichenfolgenliteralelement, das einen Teil des Pfads bestimmter Systemordner darstellt.

## <a name="rule-description"></a>Regelbeschreibung
Die <xref:System.Environment.SpecialFolder?displayProperty=fullName> -Enumeration enthält Elemente, die auf spezielle Systemordner verweisen. Die Speicherorte dieser Ordner können unterschiedlichen Betriebssystemen unterschiedliche Werte aufweisen, der Benutzer kann einige der Standorte ändern, und die Speicherorte werden lokalisiert. Ein Beispiel für einen speziellen Ordner ist der System Ordner, der "c:\Windows\System32" on [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] ist, aber "c:\WINNT\System32" unter. [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] Die <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> -Methode gibt die Speicherorte zurück, die <xref:System.Environment.SpecialFolder> der-Enumeration zugeordnet sind. Die Speicherorte, die von <xref:System.Environment.GetFolderPath%2A> zurückgegeben werden, sind lokalisiert und für den aktuell laufenden Computer geeignet.

Mit dieser Regel werden die Ordner Pfade, die mithilfe der <xref:System.Environment.GetFolderPath%2A> -Methode abgerufen werden, in separate Verzeichnis Ebenen mit Token versehen. Jedes Zeichenfolgenliterale wird mit den Token verglichen. Wenn eine Entsprechung gefunden wird, wird davon ausgegangen, dass die Methode eine Zeichenfolge aufbaut, die auf den System Speicherort verweist, der dem Token zugeordnet ist. Verwenden Sie für Portabilität und Lokalisier <xref:System.Environment.GetFolderPath%2A> barkeit die-Methode, um die Speicherorte der speziellen Systemordner abzurufen, anstatt Zeichen folgen Literale zu verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Speicherort <xref:System.Environment.GetFolderPath%2A> mithilfe der-Methode ab.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn das Zeichenfolgenliterale nicht verwendet wird, um auf einen der System <xref:System.Environment.SpecialFolder> Speicherorte zu verweisen, die mit der-Enumeration verknüpft sind.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird der Pfad des Ordners für allgemeine Anwendungsdaten erstellt, der drei Warnungen aus dieser Regel generiert. Im folgenden Beispiel wird der Pfad mithilfe der <xref:System.Environment.GetFolderPath%2A> -Methode abgerufen.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)