---
title: "CA1816: GC.SuppressFinalize korrekt aufrufen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816: GC.SuppressFinalize korrekt aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Kategorie \(Category\)|Microsoft  Verwendung|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
  
-   Eine Methode, die eine Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ist, ruft <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> nicht auf.  
  
-   Eine Methode, die keine Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ist, ruft <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> auf.  
  
-   Eine Methode ruft <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> und gibt etwas anderes als dies aus \(Me in Visual Basic\).  
  
## Regelbeschreibung  
 Mit der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>\-Methode können die Benutzer Ressourcen jederzeit freigeben, bevor das Objekt für die Garbage Collection verfügbar wird.  Wenn die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>\-Methode aufgerufen wird, werden Ressourcen des Objekts freigegeben.  Dies macht einen Abschluss unnötig.  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> sollte <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufrufen, damit der Garbage Collector nicht den Finalizer des Objekts aufruft.  
  
 Um zu verhindern, dass abgeleitete Typen mit Finalizern [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) erneut implementieren und aufrufen müssen, sollten unversiegelte Typen ohne Finalizer dennoch <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufrufen.  
  
## Behandeln von Verstößen  
 So korrigieren Sie einen Verstoß dieser Regel:  
  
 Wenn die Methode eine Implementierung von <xref:System.IDisposable.Dispose%2A> ist, fügen Sie einen Aufruf von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> hinzu.  
  
 Wenn die Methode keine Implementierung von <xref:System.IDisposable.Dispose%2A> ist, entfernen Sie den Aufruf von <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, oder verschieben Sie ihn in die Implementierung von <xref:System.IDisposable.Dispose%2A> des Typs.  
  
 Ändern Sie alle Aufrufe in <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, sodass sie dies \(Me in Visual Basic\) übergeben.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn Sie <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> zur Steuerung der Lebensdauer anderer Objekte verwenden möchten.  Unterdrücken Sie keine Warnung dieser Regel, wenn eine Implementierung von <xref:System.IDisposable.Dispose%2A> nicht <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufruft.  Wird der Abschluss nicht unterdrückt, beeinträchtigt dies die Leistung, sodass sich keine Vorteile ergeben.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode veranschaulicht, die nicht korrekt <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufruft.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode veranschaulicht, die ordnungsgemäß <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> aufruft.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]  
  
## Verwandte Regeln  
 [CA2215: Dispose\-Methoden müssen die Dispose\-Funktion der Basisklasse aufrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## Siehe auch  
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)