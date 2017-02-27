---
title: "CA1024: Nach M&#246;glichkeit Eigenschaften verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1024: Nach M&#246;glichkeit Eigenschaften verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode hat einen Namen, der mit `Get` beginnt, sie nimmt keine Parameter an und gibt einen Wert zurück, bei dem es sich nicht um ein Array handelt.  
  
## Regelbeschreibung  
 In den meisten Fällen stellen Eigenschaften Daten dar, während Methoden überwiegend Aktionen ausführen.  Da der Zugriff auf Eigenschaften wie der Zugriff auf Felder erfolgt, vereinfacht sich ihre Verwendung.  Eine Methode eignet sich gut als Eigenschaft, wenn eine dieser Bedingungen zutrifft:  
  
-   Akzeptiert keine Argumente und gibt die Zustandsinformationen eines Objekts zurück.  
  
-   Akzeptiert ein einzelnes Argument, um den Zustand eines Objekts teilweise festzulegen.  
  
 Eigenschaften sollten sich wie Felder verhalten. Wenn die Methode sich nicht so verhalten kann, sollte sie nicht in eine Eigenschaft geändert werden.  Methoden sind in den folgenden Situationen besser geeignet als Eigenschaften:  
  
-   Die Methode führt einen zeitaufwändigen Vorgang aus.  Die Methode ist deutlich langsamer als die Zeit, die benötigt wird, um ein Feld festzulegen oder abzurufen.  
  
-   Die Methode führt eine Konvertierung aus.  Beim Zugriff auf ein Feld wird keine konvertierte Version der Daten zurückgegeben, die im Feld gespeichert sind.  
  
-   Die Get\-Methode zeigt eine wahrnehmbare Nebenwirkung.  Das Abrufen des Werts eines Felds erzeugt keine Nebenwirkungen.  
  
-   Die Reihenfolge der Ausführung ist wichtig.  Das Festlegen des Werts eines Felds setzt nicht das Stattfinden anderer Vorgänge voraus.  
  
-   Das Aufrufen der Methode zweimal hintereinander führt zu unterschiedlichen Ergebnissen.  
  
-   Die Methode ist statisch, gibt jedoch ein Objekt zurück, das vom Aufrufer geändert werden kann.  Beim Abrufen eines Feldwerts kann der Aufrufer die vom Feld gespeicherten Daten nicht ändern.  
  
-   Die Methode gibt ein Array zurück.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Methode in eine Eigenschaft.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Methode mindestens eines der zuvor aufgeführten Kriterien erfüllt.  
  
## Steuern der Erweiterung von Eigenschaften im Debugger  
 Ein Grund, warum Programmierer die Verwendung einer Eigenschaft vermeiden, liegt darin, dass diese vom Debugger nicht automatisch erweitert werden soll.  Die Eigenschaft kann z. B. die Reservierung eines umfangreichen Objekts oder den Aufruf von P\/Invoke beinhalten, ohne dass sie erkennbare Nebeneffekte hat.  
  
 Sie können verhindern, dass der Debugger Eigenschaften automatisch erweitert, indem Sie <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> anwenden.  Das folgende Beispiel zeigt, wie dieses Attribut auf eine Instanzeneigenschaft angewendet wird.  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## Beispiel  
 Das folgende Beispiel enthält mehrere Methoden, die in Eigenschaften konvertiert werden sollten, und mehrere Methoden, die nicht in Eigenschaften geändert werden sollten, da sie sich nicht wie Felder verhalten.  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]