---
title: "CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen | Microsoft Docs"
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
  - "AptcaMethodsShouldOnlyCallAptcaMethods"
  - "CA2116"
helpviewer_keywords: 
  - "AptcaMethodsShouldOnlyCallAptcaMethods"
  - "CA2116"
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|  
|CheckId|CA2116|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode in einer Assembly mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>\-Attribut ruft eine Methode in einer Assembly auf, die nicht über das Attribut verfügt.  
  
## Regelbeschreibung  
 Standardmäßig sind öffentliche oder geschützte Methoden in Assemblys mit starken Namen implizit durch [Link Demands](../Topic/Link%20Demands.md) geschützt, sodass sie voll vertrauenswürdig sind. Nur voll vertrauenswürdige Aufrufer können auf eine Assembly mit starkem Namen zugreifen.  Mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute>\- \(APTCA\-\)Attribut markierte Assemblys mit starkem Namen verfügen nicht über diesen Schutz.  Das Attribut deaktiviert den Linkaufruf, sodass nicht voll vertrauenswürdige Aufrufer auf die Assembly zugreifen können, beispielsweise Code, der in einem Intranet oder im Internet ausgeführt wird.  
  
 Wenn eine voll vertrauenswürdige Assembly über das APTCA\-Attribut verfügt und die Assembly Code in einer anderen Assembly ausführt, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt werden.  Wenn die beiden Methoden `M1` und `M2` die folgenden Bedingungen erfüllen, können böswillige Aufrufer mithilfe der `M1`\-Methode den impliziten voll vertrauenswürdigen Linkaufruf umgehen, durch den `M2` geschützt wird.  
  
-   `M1` ist eine öffentliche Methode. Sie wird in einer voll vertrauenswürdigen Assembly deklariert, die über das APTCA\-Attribut verfügt.  
  
-   `M1` ruft die `M2`\-Methode außerhalb der Assembly von `M1` auf.  
  
-   Die Assembly von `M2` verfügt nicht über das APTCA\-Attribut und sollte daher nicht durch oder für teilweise vertrauenswürdige Aufrufer ausgeführt werden.  
  
 Ein teilweise vertrauenswürdiger Aufrufer `X` kann die `M1`\-Methode aufrufen und damit bewirken, dass `M2` von `M1` aufgerufen wird.  Da `M2` nicht über das APTCA\-Attribut verfügt, muss der unmittelbare Aufrufer \(`M1`\) einen Linkaufruf erfüllen, um voll vertrauenswürdig zu sein. `M1` ist voll vertrauenswürdig und erfüllt daher diese Bedingung.  Das Sicherheitsrisiko entsteht dadurch, dass `X` nicht an der Erfüllung des Linkaufrufs beteiligt ist, durch den `M2` gegenüber nicht vertrauenswürdigen Aufrufern geschützt wird.  Deshalb dürfen Methoden mit dem APTCA\-Attribut keine Methoden aufrufen, die nicht über das Attribut verfügen.  
  
## Behandeln von Verstößen  
 Wenn das APTCA\-Attribut benötigt wird, verwenden Sie eine Anforderung, um die Methode zu schützen, die die voll vertrauenswürdige Assembly aufruft.  Je nachdem, welche Funktionen durch die Methode zur Verfügung gestellt werden, erhalten Sie unterschiedliche Berechtigungen.  Schützen Sie die Methode nach Möglichkeit mit einer Forderung nach voller Vertrauenswürdigkeit, um sicherzustellen, dass die zugrunde liegenden Funktionen nicht teilweise vertrauenswürdigen Aufrufern zur Verfügung gestellt werden.  Wenn dies nicht möglich ist, wählen Sie einen Satz von Berechtigungen aus, durch den die zur Verfügung gestellten Funktionen wirksam geschützt werden.  Weitere Informationen zu Anforderungen finden Sie unter [Demands](http://msdn.microsoft.com/de-de/e5283e28-2366-4519-b27d-ef5c1ddc1f48).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Um eine Warnung dieser Regel gefahrlos unterdrücken zu können, müssen Sie sicherstellen, dass die durch die Methode zur Verfügung gestellten Funktionen Aufrufern keinen direkten oder indirekten Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen gewähren, die auf destruktive Weise verwendet werden können.  
  
## Beispiel  
 Im folgenden Beispiel wird anhand von zwei Assemblys und einer Testanwendung die Sicherheitslücke veranschaulicht, die durch diese Regel erkannt wurde.  Die erste Assembly weist das APTCA\-Attribut nicht auf und sollte teilweise vertrauenswürdigen Aufrufern nicht zugänglich sein \(in den obigen Erläuterungen dargestellt durch `M2`\).  
  
 [!code-cs[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]  
  
## Beispiel  
 Die zweite Assembly ist voll vertrauenswürdig und lässt teilweise vertrauenswürdige Aufrufer zu \(in den obigen Erläuterungen dargestellt durch `M1`\).  
  
 [!code-cs[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]  
  
## Beispiel  
 Die Testanwendung \(in den obigen Erläuterungen dargestellt durch `X`\) ist teilweise vertrauenswürdig.  
  
 [!code-cs[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Forderung nach vollständiger Vertrauensstellung:Fehler bei Anforderung.**  
**ClassRequiringFullTrust.DoWork wurde aufgerufen.**   
## Verwandte Regeln  
 [CA2117: APTCA\-Typen sollten nur APTCA\-Basistypen erweitern](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)  
  
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/de-de/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Demands](http://msdn.microsoft.com/de-de/e5283e28-2366-4519-b27d-ef5c1ddc1f48)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)