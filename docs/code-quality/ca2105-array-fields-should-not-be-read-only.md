---
title: "CA2105: Arrayfelder d&#252;rfen nicht schreibgesch&#252;tzt sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2105"
  - "ArrayFieldsShouldNotBeReadOnly"
helpviewer_keywords: 
  - "ArrayFieldsShouldNotBeReadOnly"
  - "CA2105"
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2105: Arrayfelder d&#252;rfen nicht schreibgesch&#252;tzt sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentliches oder geschütztes Feld, das ein Array enthält, ist als schreibgeschützt deklariert.  
  
## Regelbeschreibung  
 Wenn Sie den `readonly`\-Modifizierer \(`ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) auf ein Feld anwenden, das ein Array enthält, kann das Feld nicht dahingehend geändert werden, dass es auf ein anderes Array verweist.  Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden.  Code, von dem auf der Grundlage der Elemente eines öffentlichen schreibgeschützten Arrays Entscheidungen getroffen oder Vorgänge ausgeführt werden, enthält unter Umständen eine Sicherheitslücke.  
  
 Das Vorhandensein eines öffentlichen Felds verstößt außerdem gegen die Entwurfsregel [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
## Behandeln von Verstößen  
 Verlassen Sie sich zum Beheben der durch diese Regel ermittelten Sicherheitslücke nicht auf den Inhalt eines öffentlich zugänglichen schreibgeschützten Arrays.  Es wird dringend empfohlen, eines der folgenden Verfahren zu verwenden:  
  
-   Ersetzen Sie das Array durch eine stark typisierte Auflistung, die nicht geändert werden kann.  Weitere Informationen finden Sie unter <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.  
  
-   Ersetzen Sie das öffentliche Feld durch eine Methode, die einen Klon eines privaten Arrays zurückgibt.  Da der Code nicht auf den Klon angewiesen ist, besteht keine Gefahr, wenn die Elemente geändert werden.  
  
 Wenn Sie den zweiten Ansatz wählen, ersetzen Sie das Feld nicht durch eine Eigenschaft, da die Leistung durch Eigenschaften, die Arrays zurückgeben, beeinträchtigt wird.  Weitere Informationen finden Sie unter [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Es wird dringend davon abgeraten, eine Warnung dieser Regel auszuschließen.  Es gibt praktisch keine Szenarien, bei denen der Inhalt eines schreibgeschützten Felds unwichtig ist.  Wenn dies auf Ihr Szenario zutrifft, entfernen Sie den `readonly`\-Modifizierer, anstatt die Meldung auszuschließen.  
  
## Beispiel  
 In diesem Beispiel werden die Gefahren bei einem Verstoß gegen diese Regel veranschaulicht.  Im ersten Teil wird eine Beispielbibliothek mit einem Typ `MyClassWithReadOnlyArrayField` dargestellt, die zwei Felder \(`grades` und `privateGrades`\) enthält, die nicht sicher sind.  Das `grades`\-Feld ist öffentlich und kann daher von jedem Aufrufer angegriffen werden.  Das `privateGrades`\-Feld ist privat, aber dennoch gefährdet, da es durch die `GetPrivateGrades`\-Methode an Aufrufer zurückgegeben wird.  Das `securePrivateGrades`\-Feld wird auf sichere Weise durch die `GetSecurePrivateGrades`\-Methode verfügbar gemacht.  Es ist im Einklang mit empfohlenen Entwurfsvorgehensweisen als privat deklariert.  Der zweite Teil enthält Code, der im `grades`\-Member und im `privateGrades`\-Member gespeicherte Werte ändert.  
  
 Die Beispielklassenbibliothek wird im folgenden Beispiel angezeigt.  
  
 [!code-cs[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## Beispiel  
 Im folgenden Code werden anhand der Beispielklassenbibliothek Sicherheitsprobleme schreibgeschützter Arrays veranschaulicht.  
  
 [!code-cs[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 Ausgabe dieses Beispiels:  
  
  **Vor Manipulation: Grade: 90, 90, 90 Private Grade: 90, 90, 90 Sichere Grade, 90, 90, 90**  
**Nach Manipulation: Grade: 90, 555, 90 Private Grade: 90, 555, 90 Sichere Grade, 90, 90, 90**   
## Siehe auch  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>