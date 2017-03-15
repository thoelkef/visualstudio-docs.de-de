---
title: "CA2149: Transparente Methoden d&#252;rfen keine Aufrufe in systemeigenen Code durchf&#252;hren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2149: Transparente Methoden d&#252;rfen keine Aufrufe in systemeigenen Code durchf&#252;hren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode ruft durch einen Methodenstub, z. B. P\/Invoke, eine systemeigene Funktion auf.  
  
## Regelbeschreibung  
 Diese Regel wird für jede transparente Methode ausgelöst, die einen direkten Aufruf in systemeigenem Code ausführt, z. B. mit P\/Invoke.  Verstöße gegen diese Regel führen im Sicherheitstransparenzmodell der Ebene 2 zu einer <xref:System.MethodAccessException> und einer vollständige Anforderung für <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenzmodell der Ebene 1.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, markieren Sie die Methode, mit der der systemeigene Code aufgerufen wird, mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 [!code-cs[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]