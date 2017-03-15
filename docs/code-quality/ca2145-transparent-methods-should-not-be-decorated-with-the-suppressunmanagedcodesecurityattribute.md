---
title: "CA2145: Transparente Methoden d&#252;rfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145: Transparente Methoden d&#252;rfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine transparente Methode, eine mit der <xref:System.Security.SecuritySafeCriticalAttribute>\-Methode markierte Methode oder ein Typ, der eine mit dem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>\-Attribut markierte Methode enthält.  
  
## Regelbeschreibung  
 Mit dem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>\-Attribut ergänzte Methoden platzieren einen impliziten LinkDemand nach jeder Methode, die es aufruft.  Dieser LinkDemand erfordert, dass der aufrufende Code sicherheitskritisch ist.  Das Markieren der Methode, die SuppressUnmanagedCodeSecurity mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut verwendet, macht diese Anforderung offensichtlicher für Aufrufer der Methode.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode oder den Typ mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut:  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
### Code  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### Kommentare