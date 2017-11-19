---
title: "CA1302: Keine hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a6fc1bac1b13d432f395842c7de4ce6250dd708
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden
|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Methode verwendet ein Zeichenfolgenliteral, das Teil des Pfads bestimmter Systemordner darstellt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die <xref:System.Environment.SpecialFolder?displayProperty=fullName> -Enumeration enthält Member, die auf besondere Systemordner verweisen. Die Speicherorte dieser Ordner können unter verschiedenen Betriebssystemen unterschiedliche Werte aufweisen, der Benutzer kann einige Speicherorte ändern und die Speicherorte sind lokalisiert. Ein Beispiel für einen besonderen Ordner befindet sich auf den Ordner "System", "C:\WINDOWS\system32" also [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] aber "C:\WINNT\system32" unter [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. Die <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> Methode gibt die Speicherorte, die zugeordnet sind die <xref:System.Environment.SpecialFolder> Enumeration. Die Speicherorte, die von zurückgegeben werden <xref:System.Environment.GetFolderPath%2A> sind lokalisiert und für den derzeit ausgeführten Computer geeignet.  
  
 Diese Regel die Ordnerpfade, die mit abgerufen werden die <xref:System.Environment.GetFolderPath%2A> Methode in separate Verzeichnisebenen. Jedes Zeichenfolgenliteral wird mit den Token verglichen. Wenn eine Übereinstimmung gefunden wird, wird davon ausgegangen, dass die Methode eine Zeichenfolge erstellt wird, die auf den Speicherort im Dateisystem verweist, die das Token zugeordnet ist. Verwenden Sie für Portabilität und Lokalisierbarkeit die <xref:System.Environment.GetFolderPath%2A> Methode, um die Speicherorte der speziellen Systemordner anstelle von Zeichenfolgenliteralen abzurufen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Speicherort mithilfe der <xref:System.Environment.GetFolderPath%2A> Methode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können zum Unterdrücken einer Warnung dieser Regel, wenn das Zeichenfolgenliteral nicht verwendet wird, finden in den Speicherorten im Dateisystem, das zugeordnete ruhig der <xref:System.Environment.SpecialFolder> Enumeration.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel erstellt den Pfad des der gemeinsamen Ordners für Anwendungsdaten, die von dieser Regel drei Warnungen generiert. Im Beispiel ruft anschließend den Pfad ab, mit der <xref:System.Environment.GetFolderPath%2A> Methode.  
  
 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)