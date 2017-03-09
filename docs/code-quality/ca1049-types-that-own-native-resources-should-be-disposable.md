---
title: "CA1049: Typen, die systemeigene Ressourcen besitzen, m&#252;ssen gel&#246;scht werden k&#246;nnen | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049: Typen, die systemeigene Ressourcen besitzen, m&#252;ssen gel&#246;scht werden k&#246;nnen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ verweist auf ein <xref:System.IntPtr?displayProperty=fullName>\-Feld, ein <xref:System.UIntPtr?displayProperty=fullName>\-Feld oder ein <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>\-Feld, implementiert jedoch nicht <xref:System.IDisposable?displayProperty=fullName>.  
  
## Regelbeschreibung  
 Diese Regel setzt voraus, dass in den Feldern <xref:System.IntPtr>, <xref:System.UIntPtr> und <xref:System.Runtime.InteropServices.HandleRef> Zeiger auf nicht verwaltete Ressourcen gespeichert werden.  Typen, die nicht verwaltete Ressourcen zuordnen, müssen <xref:System.IDisposable> implementieren, damit Aufrufer diese Ressourcen bei Bedarf freigeben und die Lebensdauer der Objekte verkürzen können, die diese Ressourcen enthalten.  
  
 Aufgabe des empfohlenen Entwurfsmusters zum Bereinigen nicht verwalteter Ressourcen ist, sowohl ein implizites als auch ein explizites Mittel zum Freigeben dieser Ressourcen bereitzustellen. Dazu dient die <xref:System.Object.Finalize%2A?displayProperty=fullName>\-Methode bzw. die <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>\-Methode.  Der Garbage Collector ruft die <xref:System.Object.Finalize%2A>\-Methode eines Objekts zu einem nicht genau festgelegten Zeitpunkt auf, nachdem festgestellt wurde, dass das Objekt nicht mehr erreichbar ist.  Nach dem Aufruf von <xref:System.Object.Finalize%2A> wird zur Freigabe des Objekts eine zusätzliche Garbage Collection benötigt.  Die <xref:System.IDisposable.Dispose%2A>\-Methode ermöglicht dem Aufrufer, Ressourcen bei Bedarf explizit freizugeben. Die Ressourcen werden dabei früher freigegeben als unter dem Garbage Collector.  Nach dem Bereinigen der nicht verwalteten Ressourcen muss <xref:System.IDisposable.Dispose%2A> die <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>\-Methode aufrufen, um dem Garbage Collector mitzuteilen, dass <xref:System.Object.Finalize%2A> nicht mehr aufgerufen werden muss. Damit entfällt die zusätzliche Garbage Collection, und die Lebensdauer des Objekts wird verkürzt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, implementieren Sie <xref:System.IDisposable>.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Typ nicht auf eine nicht verwaltete Ressource verweist.  Andernfalls sollten Sie keine Warnung dieser Regel unterdrücken, denn wenn <xref:System.IDisposable> nicht implementiert wird, kann dies dazu führen, dass nicht verwaltete Ressourcen nicht verfügbar sind oder nicht verwendet werden.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ gezeigt, der <xref:System.IDisposable> implementiert, um eine nicht verwaltete Ressource zu bereinigen.  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## Verwandte Regeln  
 [CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: GC.SuppressFinalize korrekt aufrufen](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: Typen, die löschbare Felder besitzen, müssen gelöscht werden können](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  
  
## Siehe auch  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)