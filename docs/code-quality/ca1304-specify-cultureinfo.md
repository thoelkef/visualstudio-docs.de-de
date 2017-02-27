---
title: "CA1304: CultureInfo angeben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyCultureInfo"
  - "CA1304"
helpviewer_keywords: 
  - "SpecifyCultureInfo"
  - "CA1304"
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1304: CultureInfo angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|CheckId|CA1304|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode oder ein Konstruktor ruft einen Member auf, der eine Überladung besitzt, die einen <xref:System.Globalization.CultureInfo?displayProperty=fullName>\-Parameter akzeptiert. Die Methode oder der Konstruktor ruft die Überladung nicht auf, die den <xref:System.Globalization.CultureInfo> akzeptiert.  Diese Regel ignoriert Aufrufe der folgenden Methoden:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Regelbeschreibung  
 Wenn ein <xref:System.Globalization.CultureInfo>\-Objekt oder ein <xref:System.IFormatProvider?displayProperty=fullName>\-Objekt nicht angegeben wird, hat der Standardwert, der vom überladenen Member bereitgestellt wird, möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt.  Zudem basiert bei [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Membern die Auswahl von Standardkultur und Formatierung auf Annahmen, die möglicherweise nicht auf Ihren Code zutreffen.  Um sicherzustellen, dass der Code in den vorgesehenen Szenarien das erwartete Verhalten zeigt, sollten Sie sich bei der Angabe kulturspezifischer Daten an die folgenden Richtlinien halten:  
  
-   Wenn der Wert dem Benutzer angezeigt wird, verwenden Sie die aktuelle Kultur.  Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Wenn der Wert gespeichert wird und Software auf diesen Wert zugreift, d. h. wenn er in einer Datei oder Datenbank gespeichert wird, verwenden Sie die nicht variante Kultur.  Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Wenn Sie den Empfänger des Werts nicht kennen, lassen Sie den Datennutzer oder \-anbieter die Kultur angeben.  
  
 Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> nur verwendet wird, um lokalisierte Ressourcen mit einer Instanz der <xref:System.Resources.ResourceManager?displayProperty=fullName>\-Klasse abzurufen.  
  
 Auch wenn das Standardverhalten des überladenen Members für Ihre Zwecke geeignet ist, ist es besser, die kulturspezifische Überladung aufzurufen, damit der Code selbstdokumentierend und einfacher zu pflegen ist.  
  
## Behandeln von Verstößen  
 Um Verstöße gegen diese Regel zu beheben, verwenden Sie die Überladung, die ein <xref:System.Globalization.CultureInfo>\-Objekt oder <xref:System.IFormatProvider>\-Objekt als Parameter übernimmt, und geben das Argument entsprechend der oben angegebenen Richtlinien an.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn sicher ist, dass die Standardkultur\/der Formatanbieter die richtige Wahl darstellt und die Wartbarkeit des Codes keine hohe Entwicklungspriorität darstellt.  
  
## Beispiel  
 Im folgenden Beispiel verursacht `BadMethod` zwei Verstöße gegen diese Regel.  `GoodMethod` korrigiert den ersten Verstoß, indem sie die invariante Kultur an System.String.Compare übergeben, und korrigiert den zweiten Verstoß durch das Übergeben der aktuellen Kultur an <xref:System.String.ToLower%2A>, da dem Benutzer `string3` angezeigt wird.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht, welche Auswirkung die Standardkultur auf das voreingestellte <xref:System.IFormatProvider>\-Objekt hat, das vom <xref:System.DateTime>\-Typ ausgewählt wird.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **6\/4\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## Verwandte Regeln  
 [CA1305: IFormatProvider angeben](../code-quality/ca1305-specify-iformatprovider.md)  
  
## Siehe auch  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/de-de/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)