---
title: "CA2118: &#220;berpr&#252;fen der Verwendung von SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118: &#220;berpr&#252;fen der Verwendung von SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ bzw. Member verfügt über das <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>\-Attribut.  
  
## Regelbeschreibung  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ändert das Standardverhalten des Sicherheitssystems für Member, die nicht verwalteten Code mithilfe eines COM\-Interop\- oder Plattformaufrufs ausführen.  Im Allgemeinen führt das System bei einer Berechtigung für nicht verwalteten Code einen [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) aus.  Diese Anforderung erfolgt zur Laufzeit bei jedem Aufruf des Members, und jeder Aufrufer in der Aufrufliste wird auf die Berechtigung überprüft.  Wenn das Attribut vorhanden ist, führt das System [Link Demands](../Topic/Link%20Demands.md) für die Berechtigung aus: Die Berechtigungen des unmittelbaren Aufrufers werden überprüft, wenn der Aufrufer JIT\-kompiliert ist.  
  
 Dieses Attribut wird hauptsächlich verwendet, um die Leistung zu erhöhen. Der Leistungszuwachs geht jedoch mit beträchtlichen Sicherheitsrisiken einher.  Wenn Sie das Attribut öffentlichen Membern hinzufügen, die systemeigene Methoden aufrufen, benötigen die Aufrufer in der Aufrufliste \(also nicht die unmittelbaren Aufrufer\) keine Berechtigung für nicht verwalteten Code, um unverwalteten Code auszuführen.  Je nach den Aktionen und der Eingabebehandlung des öffentlichen Members wird nicht vertrauenswürdigen Aufrufern unter Umständen der Zugriff auf Funktionen gestattet, die normalerweise nur für vertrauenswürdigen Code verfügbar sind.  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendet Sicherheitsüberprüfungen, um Aufrufern direkten Zugriff auf den Adressbereich des aktuellen Prozesses zu verwehren.  Da dieses Attribut die normalen Sicherheitsvorkehrungen umgeht, stellt Ihr Code eine schwerwiegende Bedrohung dar, wenn er zum Lesen oder Beschreiben des Speichers des Prozesses verwendet werden kann.  Das Risiko ist nicht auf Methoden beschränkt, bei denen der Zugriff auf den Prozessspeicher gewollt ist, sondern in allen Szenarien vorhanden, in denen bösartiger Code Zugriff durch ein beliebiges Mittel erreichen kann, beispielsweise durch unerwartete, fehlerhafte oder ungültige Eingaben.  
  
 Die Standardsicherheitsrichtlinie gewährt einer Assembly nur dann eine Berechtigung für nicht verwalteten Code, wenn sie auf dem lokalen Computer ausgeführt wird oder einer der folgenden Gruppen angehört:  
  
-   Codegruppe Arbeitsplatzzone  
  
-   Codegruppe Starker Microsoft\-Name  
  
-   Codegruppe Starker ECMA\-Name  
  
## Behandeln von Verstößen  
 Überprüfen Sie Ihren Code sorgfältig, um sicherzustellen, dass dieses Attribut absolut notwendig ist.  Wenn Sie mit den Sicherheitsvorkehrungen für verwalteten Code nicht vertraut sind oder Ihnen die Auswirkungen der Verwendung dieses Attributs auf die Sicherheit nicht klar sind, entfernen Sie es aus dem Code.  Wenn das Attribut erforderlich ist, müssen Sie sicherstellen, dass Aufrufer den Code nicht in böswilliger Absicht verwenden können.  Wenn der Code über keine Berechtigung zur Ausführung von nicht verwaltetem Code verfügt, ist dieses Attribut wirkungslos und sollte entfernt werden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Um eine Warnung dieser Regel gefahrlos unterdrücken zu können, müssen Sie sicherstellen, dass der Code Aufrufern keinen Zugriff auf systemeigene Vorgänge oder Ressourcen gewährt, die auf destruktive Weise verwendet werden können.  
  
## Beispiel  
 Das folgende Beispiel verstößt gegen die Regel.  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel gibt die `DoWork`\-Methode einen öffentlich zugänglichen Codepfad zur `FormatHardDisk`\-Plattformaufrufmethode an.  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird ein Verstoß durch die öffentliche `DoDangerousThing`\-Methode verursacht.  Um den Verstoß aufzulösen, sollte `DoDangerousThing` privat sein, und der Zugriff darauf sollte über eine öffentliche Methode erfolgen, die durch eine Sicherheitsanforderung gesichert ist, wie durch die `DoWork`\-Methode veranschaulicht wird.  
  
 [!code-cs[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## Siehe auch  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/de-de/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [Daten und Modellierung](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Link Demands](../Topic/Link%20Demands.md)