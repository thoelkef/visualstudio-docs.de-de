---
title: "CA1003: Generische Ereignishandlerinstanzen verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseGenericEventHandlerInstances"
  - "CA1003"
helpviewer_keywords: 
  - "CA1003"
  - "UseGenericEventHandlerInstances"
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1003: Generische Ereignishandlerinstanzen verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericEventHandlerInstances|  
|CheckId|CA1003|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ enthält einen Delegaten, der void zurückgibt. Die zugehörige Signatur enthält zwei Parameter \(der erste ist ein Objekt, der zweite ein Typ, der EventArgs zugewiesen werden kann\), und die enthaltende Assembly hat [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] zum Ziel.  
  
## Regelbeschreibung  
 Vor [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] musste ein neuer Delegat deklariert werden, der eine von der <xref:System.EventArgs?displayProperty=fullName>\-Klasse abgeleitete Klasse angab, damit an den Ereignishandler benutzerdefinierte Informationen übergeben werden konnten.  Dies ist in [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] nicht mehr erforderlich, da der <xref:System.EventHandler%601?displayProperty=fullName>\-Delegat eingeführt wurde.  Dieser generische Delegat lässt zu, dass jede von <xref:System.EventArgs> abgeleitet Klasse mit dem Ereignishandler verwendet werden kann.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Delegaten und ersetzen die zugehörige Instanz durch den <xref:System.EventHandler%601?displayProperty=fullName>\-Delegaten.  Wenn der Delegat automatisch durch den [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler generiert wird, ändern Sie die Syntax der Ereignisdeklaration so, dass der <xref:System.EventHandler%601?displayProperty=fullName>\-Delegat verwendet wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Delegat veranschaulicht, der gegen die Regel verstößt.  Im [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Beispiel beschreiben Kommentare, wie das Beispiel geändert wird, damit die Regel eingehalten wird.  Für C\# wird ein Beispiel mit geändertem Code angezeigt.  
  
 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-cs[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird die Delegatendeklaration aus dem vorherigen Beispiel entfernt, wodurch die Regel eingehalten wird, und die zugehörige Instanz in der `ClassThatRaisesEvent`\-Methode und der `ClassThatHandlesEvent`\-Methode wird durch den <xref:System.EventHandler%601?displayProperty=fullName>\-Delegaten ersetzt.  
  
 [!code-cs[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)