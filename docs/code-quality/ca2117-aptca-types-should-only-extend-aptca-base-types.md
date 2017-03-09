---
title: "CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern | Microsoft Docs"
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
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ in einer Assembly mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>\-Attribut erbt von einem Typ, der in einer Assembly deklariert ist, die nicht über dieses Attribut verfügt.  
  
## Regelbeschreibung  
 Standardmäßig werden öffentliche oder geschützte Typen in Assemblys mit starken Namen implizit durch [Inheritance Demands](http://msdn.microsoft.com/de-de/28b9adbb-8f08-4f10-b856-dbf59eb932d9) geschützt, damit die volle Vertrauenswürdigkeit gewahrt bleibt.  Mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute>\- \(APTCA\-\)Attribut markierte Assemblys mit starkem Namen verfügen nicht über diesen Schutz.  Das Attribut deaktiviert die Vererbungsanforderung.  Dadurch können in der Assembly deklarierte Typen, die verfügbar gemacht werden, an Typen vererbt werden, die keine volle Vertrauenswürdigkeit besitzen.  
  
 Wenn das APTCA\-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und ein in der Assembly enthaltener Typ von einem Typ erbt, der keine nicht voll vertrauenswürdigen Aufrufer zulässt, dann können Sicherheitslücken entstehen, die sich für Angriffe ausnutzen lassen.  Wenn zwei Typen `T1` und `T2` die folgenden Bedingungen erfüllen, dann können böswillige Aufrufer den Typ `T1` verwenden, um die implizite Vererbungsanforderung nach voller Vertrauenswürdigkeit zu umgehen, durch die `T2` geschützt ist.  
  
-   `T1` ist ein öffentlicher Typ, der in einer voll vertrauenswürdigen Assembly deklariert wird, die über das APTCA\-Attribut verfügt.  
  
-   `T1` erbt von einem Typ `T2`, der außerhalb dieser Assembly deklariert ist.  
  
-   Bei der Assembly von `T2` ist das APTCA\-Attribut nicht vorhanden, und daher sollte er nicht an Typen vererbt werden können, die in nicht voll vertrauenswürdigen Assemblys deklariert sind.  
  
 Ein nicht voll vertrauenswürdiger Typ `X` kann von `T1` erben, wodurch er Zugriff auf geerbte Member erhält, die in `T2` deklariert sind.  Da `T2` nicht über das APTCA\-Attribut verfügt, muss der direkt von ihm abgeleitete Typ \(`T1`\) eine Vererbungsanforderung nach voller Vertrauenswürdigkeit erfüllen. `T1` ist voll vertrauenswürdig und erfüllt daher diese Bedingung.  Das Sicherheitsrisiko liegt darin, dass `X` nicht der Vererbungsanforderung unterliegt, die `T2` davor schützt, dass nicht vertrauenswürdige Subklassen erstellt werden.  Aus diesem Grund dürfen Typen, die über das APTCA\-Attribut verfügen, Typen nicht erweitern, die nicht über das Attribut verfügen.  
  
 Ein anderes, vielleicht häufigeres Sicherheitsproblem besteht darin, dass der abgeleitete Typ \(`T1`\) wegen eines Programmierfehlers geschützte Member des Typs, der vollständige Vertrauenswürdigkeit erfordert \(`T2`\), verfügbar machen kann.  Wenn dies der Fall ist, können nicht vertrauenswürdige Aufrufer auf Informationen zugreifen, die nur für voll vertrauenswürdige Typen verfügbar sein sollten.  
  
## Behandeln von Verstößen  
 Wenn es sich bei dem Typ, der gegen die Regel verstößt, um eine Assembly handelt, die das APTCA\-Attribut nicht erfordert, dann entfernen Sie es.  
  
 Wenn das APTCA\-Attribut erforderlich ist, fügen Sie dem Typ eine Vererbungsanforderung nach voller Vertrauenswürdigkeit hinzu.  Dies schützt vor Vererbung durch nicht vertrauenswürdige Typen.  
  
 Es ist möglich, einen Verstoß durch Hinzufügen des APTCA\-Attributs zu den Assemblys der Basistypen zu beheben, die in diesem Regelverstoß genannt sind.  Tun Sie dies aber nur, nachdem Sie den gesamten Code der Assemblys und den gesamten Code, der von diesen Assemblys abhängt, eingehend auf seine Sicherheit hin überprüft haben.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Um eine Warnung dieser Regel gefahrlos zu unterdrücken, müssen Sie sicherstellen, dass geschützte Member, die von diesem Typ verfügbar gemacht werden, weder direkt noch indirekt zulassen, dass nicht vertrauenswürdige Aufrufer auf sicherheitsrelevante Informationen, Operationen oder Ressourcen zugreifen, die sich auf destruktive Weise verwenden lassen.  
  
## Beispiel  
 Im folgenden Beispiel wird anhand von zwei Assemblys und einer Testanwendung die Sicherheitslücke veranschaulicht, die durch diese Regel erkannt wurde.  Die erste Assembly verfügt nicht über das APTCA\-Attribut und sollte nicht an nicht voll vertrauenswürdige Typen \(die in den obigen Erläuterungen durch `T2` dargestellt wurden\) vererbt werden können.  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## Beispiel  
 Die zweite Assembly, die in den obigen Erläuterungen durch `T1` dargestellt wurde, ist voll vertrauenswürdig und lässt nicht voll vertrauenswürdige Aufrufer zu.  
  
 [!code-cs[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## Beispiel  
 Der in den vorherigen Erläuterungen durch `X` dargestellte Testtyp befindet sich in einer teilweise vertrauenswürdigen Assembly.  
  
 [!code-cs[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Treffen am 22.02.2003 12:00:00 im schattigen Tal\!**  
**Von Test: sonnige Wiese**  
**Treffen am 22.02.2003 12:00:00 auf der sonnigen Wiese\!**   
## Verwandte Regeln  
 [CA2116: APTCA\-Methoden sollten nur APTCA\-Methoden aufrufen](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/de-de/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Using Libraries from Partially Trusted Code](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/de-de/28b9adbb-8f08-4f10-b856-dbf59eb932d9)