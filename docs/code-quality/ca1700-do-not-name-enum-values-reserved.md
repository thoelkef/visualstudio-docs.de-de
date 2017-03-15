---
title: "CA1700: Enumerationswerte nicht mit &quot;Reserviert&quot; benennen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1700: Enumerationswerte nicht mit &quot;Reserviert&quot; benennen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines Enumerationsmembers enthält das Wort "reserved".  
  
## Regelbeschreibung  
 Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen.  Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung.  Sie sollten nicht erwarten, dass die Benutzer einen Member ignorieren, nur weil sein Name "reserved" enthält, und Sie können auch nicht davon ausgehen, dass die Benutzer die Dokumentation lesen oder sich danach richten.  Da reservierte Member in Objektkatalogen und in intelligenten integrierten Entwicklungsumgebungen angezeigt werden, können sie zudem Unklarheiten in Bezug darauf hervorrufen, welche Member tatsächlich verwendet werden.  
  
 Statt einen reserved\-Member zu verwenden, fügen Sie der Enumeration in der künftigen Version einen neuen Member hinzu.  In den meisten Fällen stellt das Hinzufügen des neuen Members keine unterbrechende Änderung dar, solange hierdurch die Werte der ursprünglichen Member nicht geändert werden.  
  
 In bestimmten Fällen stellt das Hinzufügen eines Members eine unterbrechende Änderung dar, auch wenn die ursprünglichen Werte der ursprünglichen Member erhalten bleiben.  Vor allem kann der neue Member von vorhandenen Codepfaden nicht ohne unterbrechende Aufrufer zurückgegeben werden, die eine `switch`\-Anweisung \(`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) für den Rückgabewert verwenden, der die gesamte Memberliste umfasst, und die im Standardfall eine Ausnahme auslösen.  Ein weiteres Problem ist, dass der Clientcode die Änderung im Verhalten von Reflektionsmethoden wie <xref:System.Enum.IsDefined%2A?displayProperty=fullName> eventuell nicht behandeln kann.  Entsprechend, wenn der neue Member von vorhandenen Methoden zurückgegeben werden muss oder eine bekannte Anwendungsinkompatibilität wegen schlechter Reflektionsverwendung auftritt, ist die einzige Lösung ohne Unterbrechung:  
  
1.  Hinzufügen einer neuen Enumeration, die die ursprünglichen und neuen Member enthält.  
  
2.  Markieren Sie die ursprüngliche Enumeration mit dem <xref:System.ObsoleteAttribute?displayProperty=fullName>\-Attribut.  
  
 Gehen Sie bei extern sichtbaren Typen oder Membern, die die ursprüngliche Enumeration verfügbar machen, auf die gleiche Weise vor.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie den Member entfernen oder umbenennen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos für einen Member unterdrückt werden, der derzeit für zuvor veröffentlichte Bibliotheken verwendet wird.  
  
## Verwandte Regeln  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Enumerationen müssen einen Wert von 0 \(null\) aufweisen](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)