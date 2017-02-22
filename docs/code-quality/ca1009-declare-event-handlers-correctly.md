---
title: "CA1009: Ereignishandler korrekt deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1009: Ereignishandler korrekt deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Delegat, der ein öffentliches oder geschütztes Ereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtigen Parameternamen.  
  
## Regelbeschreibung  
 Ereignishandlermethoden nehmen zwei Parameter an.  Der erste Parameter ist vom Typ <xref:System.Object?displayProperty=fullName> und wird "sender" genannt.  Dies ist das Objekt, durch das das Ereignis ausgelöst wurde.  Der zweite Parameter ist vom Typ <xref:System.EventArgs?displayProperty=fullName> und wird "e" genannt.  Dies sind die Daten, die dem Ereignis zugeordnet sind.  Wenn das Ereignis z. B. beim Öffnen einer Datei ausgelöst wird, enthalten die Ereignisdaten in der Regel den Namen der Datei.  
  
 Ereignishandlermethoden sollten keinen Wert zurückgeben.  In der Programmiersprache C\# wird dies durch den Rückgabetyp `void` angegeben.  Ein Ereignishandler kann mehrere Methoden in mehreren Objekten aufrufen.  Wenn die Methoden einen Wert zurückgeben könnten, gäbe es für jedes Ereignis mehrere Rückgabewerte, allerdings stünde nur der Wert der zuletzt aufgerufenen Methode zur Verfügung.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Parameternamen des Delegaten.  Einzelheiten hierzu finden Sie im folgenden Beispiel.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel zeigt einen Delegaten, der für die Behandlung von Ereignissen geeignet ist.  Die Methoden, die von diesem Ereignishandler aufgerufen werden können, entsprechen der in den Entwurfsrichtlinien angegebenen Signatur.  `AlarmEventHandler` ist der Typname des Delegaten.  `AlarmEventArgs` leitet sich von der Basisklasse für Ereignisdaten ab, <xref:System.EventArgs>, und hält Alarmereignisdaten zurück.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## Verwandte Regeln  
 [CA2109: Sichtbare Ereignishandler überprüfen](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## Siehe auch  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Ereignisse und Delegaten](http://msdn.microsoft.com/de-de/d98fd58b-fa4f-4598-8378-addf4355a115)