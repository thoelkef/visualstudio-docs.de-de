---
title: "CA2144: Transparenter Code darf keine Assemblys aus Bytearrays laden | Microsoft Docs"
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
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2144: Transparenter Code darf keine Assemblys aus Bytearrays laden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine transparente Methode lädt eine Assembly aus einem Bytearray mit einer der folgenden Methoden:  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## Regelbeschreibung  
 Die Sicherheitsüberprüfung für transparenten Code ist nicht so umfassend wie die Sicherheitsüberprüfung für wichtigen Code, da in transparentem Code keine sicherheitsrelevanten Aktionen ausgeführt werden können.  Aus einem Bytearray geladene Assemblys werden in transparentem Code eventuell nicht erkannt, und dieses Bytearray könnte wichtigen oder sicherheitsgeschützten Code enthalten, der überwacht werden muss.  Daher dürfen mit transparentem Code keine Assemblys aus einem Bytearray geladen werden.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, markieren Sie die Methode, mit der die Assembly geladen wird, mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Die Regel wird für den folgenden Code ausgelöst, da eine transparente Methode eine Assembly aus einem Bytearray lädt:  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]