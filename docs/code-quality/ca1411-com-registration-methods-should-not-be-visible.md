---
title: "CA1411: Die COM-Registrierungsmethoden d&#252;rfen nicht sichtbar sein | Microsoft Docs"
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
  - "CA1411"
  - "ComRegistrationMethodsShouldNotBeVisible"
helpviewer_keywords: 
  - "ComRegistrationMethodsShouldNotBeVisible"
  - "CA1411"
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1411: Die COM-Registrierungsmethoden d&#252;rfen nicht sichtbar sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>\-Attribut oder dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>\-Attribut markierte Methode ist extern sichtbar.  
  
## Regelbeschreibung  
 Wenn eine Assembly bei COM \(Component Object Model\) registriert wird, werden der Registrierung für jeden für COM sichtbaren Typ in der Assembly Einträge hinzugefügt.  Mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>\-Attribut und dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\-Attribut markierte Methoden werden während der Registrierung und der Aufhebung der Registrierung aufgerufen, um jeweils Benutzercode speziell für die Registrierung bzw. Aufhebung der Registrierung dieser Typen auszuführen.  Dieser Code darf nicht außerhalb dieser Prozesse aufgerufen werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff der Methode auf `private` oder `internal` \(`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Methoden veranschaulicht, die gegen die Regel verstoßen.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## Verwandte Regeln  
 [CA1410: Die COM\-Registrierungsmethoden müssen übereinstimmen](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)