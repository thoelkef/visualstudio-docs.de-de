---
title: "CA1065: Keine Ausnahmen an unerwarteten Speicherorten ausl&#246;sen | Microsoft Docs"
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
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1065: Keine Ausnahmen an unerwarteten Speicherorten ausl&#246;sen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode, von der das Auslösen von Ausnahmen nicht erwartet wird, löst eine Ausnahme aus.  
  
## Regelbeschreibung  
 Methoden, von denen das Auslösen von Ausnahmen nicht erwartet wird, können in folgende Kategorien unterteilt werden:  
  
-   Property Get\-Methoden  
  
-   Ereignisaccessormethoden  
  
-   Equals\-Methoden  
  
-   GetHashCode\-Methoden  
  
-   ToString\-Methoden  
  
-   Statische Konstruktoren  
  
-   Finalizer  
  
-   Dispose\-Methoden  
  
-   Gleichheitsoperatoren  
  
-   Implizite Umwandlungsoperatoren  
  
 In den folgenden Abschnitten werden diese Methodentypen erläutert.  
  
### Property Get\-Methoden  
 Eigenschaften sind im Grunde intelligente Felder.  Daher sollten sie so weit wie möglich das Verhalten eines Feldes aufweisen.  Genausowenig wie Felder sollten Eigenschaften Ausnahmen auslösen.  Wenn Sie über eine Eigenschaft verfügen, die eine Ausnahme auslöst, sollten Sie in Erwägung ziehen, sie in eine Methode umzuwandeln.  
  
 Die folgenden Ausnahmen dürfen von einer Property Get\-Methode ausgelöst werden:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> und alle Ableitungen \(einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> und alle Ableitungen  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(nur von Get\-Methoden\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(nur von Get\-Methoden\)  
  
### Ereignisaccessormethoden  
 Ereignisaccessoren sollten einfache Operationen sein, die keine Ausnahmen auslösen.  Ein Ereignis sollte beim Versuch, einen Ereignishandler hinzuzufügen oder zu entfernen, keine Ausnahme auslösen.  
  
 Die folgenden Ausnahmen dürfen von einem Ereignisaccessor ausgelöst werden:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> und alle Ableitungen \(einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> und alle Ableitungen  
  
-   <xref:System.ArgumentException> und Ableitungen  
  
### Equals\-Methoden  
 Die folgenden **Equals**\-Methoden sollten keine Ausnahmen auslösen:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 Eine **Equals**\-Methode sollte `true` oder `false` zurückgeben, statt eine Ausnahme auszulösen.  Wenn an Equals beispielsweise zwei Typen übergeben werden, die einen Konflikt verursachen, sollte die Methode einfach `false` zurückgeben und keine <xref:System.ArgumentException> auslösen.  
  
### GetHashCode\-Methoden  
 Die folgenden **GetHashCode**\-Methoden sollten normalerweise keine Ausnahmen auslösen:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode \(T\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** sollte immer einen Wert zurückgeben.  Andernfalls können Elemente in der Hashtabelle verloren gehen.  
  
 Die Versionen von **GetHashCode**, die ein Argument akzeptieren, können eine <xref:System.ArgumentException> auslösen.  **Object.GetHashCode** sollte jedoch niemals eine Ausnahme auslösen.  
  
### ToString\-Methoden  
 Der Debugger verwendet <xref:System.Object.ToString%2A?displayProperty=fullName>, um die Anzeige von Objektinformationen im Zeichenfolgenformat zu unterstützen.  Deshalb sollte **ToString** weder den Zustand eines Objekts ändern noch eine Ausnahme auslösen.  
  
### Statische Konstruktoren  
 Wenn ein statischer Konstruktor eine Ausnahme auslöst, wird der Typ in der aktuellen Anwendungsdomäne unbrauchbar.  Ausnahmen sollten nur, falls unbedingt erforderlich, von einem statischen Konstruktor ausgelöst werden \(beispielsweise bei einem Sicherheitsproblem\).  
  
### Finalizer  
 Das Auslösen einer Ausnahme durch einen Finalizer bewirkt, dass die CLR unverzüglich einen Fehler verursacht und der Prozess beendet wird.  Daher sollte stets vermieden werden, dass ein Finalizer Ausnahmen auslöst.  
  
### Dispose\-Methoden  
 Eine <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>\-Methode sollte keine Ausnahme auslösen.  Dispose wird häufig als Teil der Bereinigungslogik in einer `finally`\-Klausel aufgerufen.  Daher wird der Benutzer durch das explizite Auslösen einer Ausnahme von Dispose gezwungen, eine Ausnahmebehandlung innerhalb der `finally`\-Klausel hinzuzufügen.  
  
 Der **Dispose\(false\)**\-Codepfad sollte nie eine Ausnahme auslösen, da er fast immer von einem Finalizer aufgerufen wird.  
  
### Gleichheitsoperatoren \(\=\=, \!\=\)  
 Gleichheitsoperatoren sollten genauso wie Equals\-Methoden entweder `true` oder `false` zurückgeben und keine Ausnahmen auslösen.  
  
### Implizite Umwandlungsoperatoren  
 Da dem Benutzer häufig nicht bewusst ist, dass ein impliziter Umwandlungsoperator aufgerufen wurde, tritt eine durch den impliziten Umwandlungsoperator ausgelöste Ausnahme völlig unerwartet auf.  Deshalb sollten keine Ausnahmen von impliziten Umwandlungsoperatoren ausgelöst werden.  
  
## Behandeln von Verstößen  
 Bearbeiten Sie bei Eigenschaftengettern entweder die Logik, damit keine Ausnahme mehr ausgelöst werden muss, oder ändern Sie die Eigenschaft in eine Methode.  
  
 Ändern Sie bei allen anderen oben aufgeführten Methodentypen die Logik, damit keine Ausnahme mehr ausgelöst werden muss.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Verstoß durch eine Ausnahmedeklaration anstelle einer ausgelösten Ausnahme verursacht wurde.  
  
## Verwandte Regeln  
 [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## Siehe auch  
 [Entwurfswarnungen](../code-quality/design-warnings.md)