---
title: "CA1305: IFormatProvider angeben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1305: IFormatProvider angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die Überladungen besitzen und einen <xref:System.IFormatProvider?displayProperty=fullName>\-Parameter akzeptieren; die Methode oder der Konstruktor ruft diejenige Überladung nicht auf, die den <xref:System.IFormatProvider>\-Parameter annimmt.  Diese Regel ignoriert Aufrufe von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Methoden, bei denen dokumentiert ist, dass sie den <xref:System.IFormatProvider>\-Parameter ignorieren, und zusätzlich folgende Methoden:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Regelbeschreibung  
 Wenn ein <xref:System.Globalization.CultureInfo?displayProperty=fullName>\-Objekt oder ein <xref:System.IFormatProvider>\-Objekt nicht angegeben wird, hat der Standardwert, der vom überladenen Member bereitgestellt wird, möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt.  Zudem basiert bei [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Membern die Auswahl von Standardkultur und Formatierung auf Annahmen, die möglicherweise nicht auf Ihren Code zutreffen.  Um sicherzustellen, dass der Code in den vorgesehenen Szenarien das erwartete Verhalten zeigt, sollten Sie sich bei der Angabe kulturspezifischer Daten an die folgenden Richtlinien halten:  
  
-   Wenn der Wert dem Benutzer angezeigt wird, verwenden Sie die aktuelle Kultur.  Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Wenn der Wert gespeichert wird und Software auf diesen Wert zugreift \(wenn er in einer Datei oder Datenbank gespeichert wird\), verwenden Sie die nicht variante Kultur.  Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Wenn Sie den Empfänger des Werts nicht kennen, lassen Sie den Datennutzer oder \-anbieter die Kultur angeben.  
  
 Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> nur verwendet wird, um lokalisierte Ressourcen mit einer Instanz der <xref:System.Resources.ResourceManager?displayProperty=fullName>\-Klasse abzurufen.  
  
 Auch wenn das Standardverhalten des überladenen Members für Ihre Zwecke geeignet ist, ist es besser, die kulturspezifische Überladung aufzurufen, damit der Code selbstdokumentierend und einfacher zu pflegen ist.  
  
## Behandeln von Verstößen  
 Um Verstöße gegen diese Regel zu beheben, verwenden Sie die Überladung, die ein <xref:System.Globalization.CultureInfo>\-Objekt oder <xref:System.IFormatProvider>\-Objekt als Parameter übernimmt, und geben das Argument entsprechend der oben angegebenen Richtlinien an.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn sicher ist, dass die Standardkultur\/der Formatanbieter die richtige Wahl darstellt und die Wartbarkeit des Codes keine hohe Entwicklungspriorität darstellt.  
  
## Beispiel  
 Im folgenden Beispiel verursacht `BadMethod` zwei Verstöße gegen diese Regel.  `GoodMethod` korrigiert den ersten Verstoß, indem die invariante Kultur an <xref:System.String.Compare%2A> übergeben wird, und korrigiert den zweiten Verstoß durch Übergeben der aktuellen Kultur an <xref:System.String.ToLower%2A>, da dem Benutzer `string3` angezeigt wird.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht, welche Auswirkung die Standardkultur auf das voreingestellte <xref:System.IFormatProvider>\-Objekt hat, das vom <xref:System.DateTime>\-Typ ausgewählt wird.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **6\/4\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## Verwandte Regeln  
 [CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md)  
  
## Siehe auch  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/de-de/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)