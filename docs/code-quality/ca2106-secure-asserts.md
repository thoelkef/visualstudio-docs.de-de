---
title: "CA2106: Sichere Best&#228;tigungen | Microsoft Docs"
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
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106: Sichere Best&#228;tigungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode bestätigt eine Berechtigung, und es werden keine Sicherheitsüberprüfungen für den Aufrufer durchgeführt.  
  
## Regelbeschreibung  
 Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen.  Ein Sicherheitsstackwalk wird beendet, wenn eine Sicherheitsberechtigung gewährt wird.  Wenn Sie eine Berechtigung ohne jegliche Überprüfung des Aufrufers gewähren, kann der Aufrufer möglicherweise indirekt mithilfe Ihrer Berechtigungen Code ausführen.  Assertions ohne Sicherheitsüberprüfungen sind nur zulässig, wenn Sie sicher sind, dass die Assertion nicht auf schädliche Weise verwendet werden kann.  Eine Assertion ist harmlos, wenn der Code, den Sie aufrufen, harmlos ist oder Benutzer keine beliebigen Informationen an Code übergeben können, den Sie aufrufen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Methode oder dem deklarierenden Typ eine Sicherheitsanforderung hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur nach einer sorgfältigen Sicherheitsüberprüfung.  
  
## Siehe auch  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)