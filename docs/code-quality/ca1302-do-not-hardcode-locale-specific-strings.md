---
title: "CA1302: Keine Hartkodierung f&#252;r gebietsschemaspezifische Zeichenfolgen verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302: Keine Hartkodierung f&#252;r gebietsschemaspezifische Zeichenfolgen verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode verwendet ein Zeichenfolgenliteral, das einen Teil des Pfads bestimmter Systemordner darstellt.  
  
## Regelbeschreibung  
 Die <xref:System.Environment.SpecialFolder?displayProperty=fullName>\-Enumeration enthält Member, die auf besondere Systemordner verweisen.  Die Speicherorte dieser Ordner können sich von Betriebssystem zu Betriebssystem unterscheiden. Der Benutzer kann einige Speicherorte ändern, und die Speicherorte sind lokalisiert.  Ein Beispiel für einen besonderen Ordner ist der Systemordner, der "C:\\WINDOWS\\system32" unter [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], aber "C:\\WINNT\\system32" unter [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] ist.  Die <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName>\-Methode gibt die der <xref:System.Environment.SpecialFolder>\-Enumeration zugeordneten Speicherorte zurück.  Die von <xref:System.Environment.GetFolderPath%2A> zurückgegebenen Speicherorte sind lokalisiert und dem aktuell aktiven Computer angepasst.  
  
 Diese Regel löst die Ordnerpfade, die mit der <xref:System.Environment.GetFolderPath%2A>\-Methode abgerufen werden, mithilfe von Token in separate Verzeichnisebenen auf.  Jedes Zeichenfolgenliteral wird mit den Token verglichen.  Wenn eine Entsprechung gefunden wird, wird davon ausgegangen, dass die Methode eine Zeichenfolge erzeugt, die auf den mit dem Token verknüpften Systemspeicherort verweist.  Verwenden Sie zwecks Portabilität und Lokalisierbarkeit die <xref:System.Environment.GetFolderPath%2A>\-Methode, um die Speicherorte der speziellen Systemordner abzurufen, anstatt die Zeichenfolgenliterale zu verwenden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Speicherort mit der <xref:System.Environment.GetFolderPath%2A>\-Methode ab.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn für den Verweis auf einen der Systemspeicherorte, die mit der <xref:System.Environment.SpecialFolder>\-Enumeration verknüpft sind, nicht das Zeichenfolgenliteral verwendet wird.  
  
## Beispiel  
 Im folgenden Beispiel wird der Pfad zum gemeinsamen Anwendungsdatenordner erstellt, wobei diese Regel drei Warnungen generiert.  Danach wird im Beispiel der Pfad mit der <xref:System.Environment.GetFolderPath%2A>\-Methode abgerufen.  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## Verwandte Regeln  
 [CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)