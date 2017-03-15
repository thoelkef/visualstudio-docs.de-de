---
title: "CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen | Microsoft Docs"
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
  - "CallGCKeepAliveWhenUsingNativeResources"
  - "CA2115"
helpviewer_keywords: 
  - "CA2115"
  - "CallGCKeepAliveWhenUsingNativeResources"
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCKeepAliveWhenUsingNativeResources|  
|CheckId|CA2115|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 In einer Methode, die in einem Typ mit einem Finalizer deklariert wird, wird auf ein <xref:System.IntPtr?displayProperty=fullName>\-Feld oder ein <xref:System.UIntPtr?displayProperty=fullName>\-Feld verwiesen, <xref:System.GC.KeepAlive%2A?displayProperty=fullName> wird aber nicht aufgerufen.  
  
## Regelbeschreibung  
 Garbage Collection gibt ein Objekt frei, wenn im verwalteten Code keine Verweise mehr darauf vorhanden sind.  Nicht verwaltete Verweise auf Objekte verhindern die Garbage Collection nicht.  Diese Regel erkennt Fehler, die auftreten können, wenn eine nicht verwaltete Ressource freigegeben wird, während sie in nicht verwaltetem Code noch verwendet wird.  
  
 Diese Regel geht davon aus, dass in <xref:System.IntPtr>\-Feldern und <xref:System.UIntPtr>\-Feldern Zeiger auf nicht verwaltete Ressourcen gespeichert werden.  Weil ein Finalizer dem Zweck dient, nicht verwaltete Ressourcen freizugeben, geht die Regel davon aus, dass der Finalizer die nicht verwaltete Ressource freigibt, auf die die Zeigerfelder zeigen.  Diese Regel setzt auch voraus, dass die Methode auf das Zeigerfeld verweist, um die nicht verwaltete Ressource an nicht verwalteten Code zu übergeben.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Methode einen Aufruf von <xref:System.GC.KeepAlive%2A> hinzu und übergeben die aktuelle Instanz \(`this` in C\# und C\+\+\) als Argument.  Fügen Sie den Aufruf nach der letzten Codezeile ein, in der das Objekt vor der Garbage Collection geschützt werden muss.  Unmittelbar nach dem Aufruf von <xref:System.GC.KeepAlive%2A> wird das Objekt wieder als für die Garbage Collection bereit betrachtet, weil davon ausgegangen wird, dass keine verwalteten Verweise auf das Objekt mehr vorhanden sind.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Regel geht von einigen Annahmen aus, die zu unbegründeten Warnungen führen können.  Sie können eine Warnung dieser Regel gefahrlos unterdrücken, wenn folgende Bedingungen erfüllt sind:  
  
-   Der Finalizer gibt den Inhalt des <xref:System.IntPtr>\-Felds oder des <xref:System.UIntPtr>\-Felds nicht frei, auf das die Methode verweist.  
  
-   Die Methode übergibt das <xref:System.IntPtr>\-Feld oder das <xref:System.UIntPtr>\-Feld nicht an nicht verwalteten Code.  
  
 Überprüfen Sie vorher sorgfältig andere Meldungen, bevor Sie sie ausschließen.  Diese Regel erkennt Fehler, die schwierig zu reproduzieren und zu debuggen sind.  
  
## Beispiel  
 Im folgenden Beispiel enthält `BadMethod` keinen Aufruf `GC.KeepAlive` und verstößt daher die Regel.  `GoodMethod` enthält den korrigierten Code.  
  
> [!NOTE]
>  Dieses Beispiel ist Pseudocode, der Code kompiliert und ausgeführt, die Warnung wird nicht ausgelöst, da eine nicht verwaltete Ressource nicht erstellt oder freigegeben wird.  
  
 [!code-cs[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]  
  
## Siehe auch  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)