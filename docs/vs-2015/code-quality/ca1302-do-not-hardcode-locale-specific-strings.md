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
ms.openlocfilehash: 18da0471b1ac62f0e61b303c60b46c15cdc2e428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539008"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode verwendet ein zeichenfolgenliteralelement, das einen Teil des Pfads bestimmter Systemordner darstellt.

## <a name="rule-description"></a>Beschreibung der Regel
 Die- <xref:System.Environment.SpecialFolder?displayProperty=fullName> Enumeration enthält Elemente, die auf spezielle Systemordner verweisen. Die Speicherorte dieser Ordner können unterschiedlichen Betriebssystemen unterschiedliche Werte aufweisen, der Benutzer kann einige der Standorte ändern, und die Speicherorte werden lokalisiert. Ein Beispiel für einen speziellen Ordner ist der System Ordner, der "c:\Windows\System32" on ist, [!INCLUDE[winxp](../includes/winxp-md.md)] aber "c:\WINNT\System32" unter [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)] . Die- <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Methode gibt die Speicherorte zurück, die der- <xref:System.Environment.SpecialFolder> Enumeration zugeordnet sind. Die Speicherorte, die von zurückgegeben werden, <xref:System.Environment.GetFolderPath%2A> sind lokalisiert und für den aktuell laufenden Computer geeignet.

 Mit dieser Regel werden die Ordner Pfade, die mithilfe der-Methode abgerufen werden, <xref:System.Environment.GetFolderPath%2A> in separate Verzeichnis Ebenen mit Token versehen. Jedes Zeichenfolgenliterale wird mit den Token verglichen. Wenn eine Entsprechung gefunden wird, wird davon ausgegangen, dass die Methode eine Zeichenfolge aufbaut, die auf den System Speicherort verweist, der dem Token zugeordnet ist. Verwenden Sie für Portabilität und Lokalisier barkeit die- <xref:System.Environment.GetFolderPath%2A> Methode, um die Speicherorte der speziellen Systemordner abzurufen, anstatt Zeichen folgen Literale zu verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Speicherort mithilfe der- <xref:System.Environment.GetFolderPath%2A> Methode ab.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn das Zeichenfolgenliterale nicht verwendet wird, um auf einen der Systemspeicher Orte zu verweisen, die mit der- <xref:System.Environment.SpecialFolder> Enumeration verknüpft sind.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der Pfad des Ordners für allgemeine Anwendungsdaten erstellt, der drei Warnungen aus dieser Regel generiert. Im folgenden Beispiel wird der Pfad mithilfe der-Methode abgerufen <xref:System.Environment.GetFolderPath%2A> .

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1303: Literale nicht als lokalisierte Parameter übergeben.](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
