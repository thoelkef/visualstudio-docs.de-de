---
title: 'CA1302: keine hart Codierung für Gebiets Schema spezifische Zeichen folgen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661472"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode verwendet ein zeichenfolgenliteralelement, das einen Teil des Pfads bestimmter Systemordner darstellt.

## <a name="rule-description"></a>Regelbeschreibung
 Die <xref:System.Environment.SpecialFolder?displayProperty=fullName>-Enumeration enthält Elemente, die auf spezielle Systemordner verweisen. Die Speicherorte dieser Ordner können unterschiedlichen Betriebssystemen unterschiedliche Werte aufweisen, der Benutzer kann einige der Standorte ändern, und die Speicherorte werden lokalisiert. Ein Beispiel für einen speziellen Ordner ist der System Ordner, der "c:\Windows\System32" auf [!INCLUDE[winxp](../includes/winxp-md.md)], aber "c:\WINNT\System32" auf [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] ist. Die <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>-Methode gibt die Speicherorte zurück, die der <xref:System.Environment.SpecialFolder>-Enumeration zugeordnet sind. Die Speicherorte, die von <xref:System.Environment.GetFolderPath%2A> zurückgegeben werden, sind lokalisiert und für den aktuell laufenden Computer geeignet.

 Mit dieser Regel werden die Ordner Pfade, die mithilfe der <xref:System.Environment.GetFolderPath%2A>-Methode abgerufen werden, in separate Verzeichnis Ebenen mit einem Token versehen. Jedes Zeichenfolgenliterale wird mit den Token verglichen. Wenn eine Entsprechung gefunden wird, wird davon ausgegangen, dass die Methode eine Zeichenfolge aufbaut, die auf den System Speicherort verweist, der dem Token zugeordnet ist. Verwenden Sie für die Portabilität und Lokalisier barkeit die <xref:System.Environment.GetFolderPath%2A>-Methode, um die Speicherorte der speziellen Systemordner abzurufen, anstatt Zeichen folgen Literale zu verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Speicherort mit der <xref:System.Environment.GetFolderPath%2A>-Methode ab.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn das Zeichenfolgenliterale nicht verwendet wird, um auf einen der Systemspeicher Orte zu verweisen, die mit der <xref:System.Environment.SpecialFolder>-Enumeration verknüpft sind.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der Pfad des Ordners für allgemeine Anwendungsdaten erstellt, der drei Warnungen aus dieser Regel generiert. Im folgenden Beispiel wird der Pfad mithilfe der <xref:System.Environment.GetFolderPath%2A>-Methode abgerufen.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
