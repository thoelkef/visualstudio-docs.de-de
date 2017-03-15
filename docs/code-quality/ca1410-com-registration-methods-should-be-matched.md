---
title: "CA1410: Die COM-Registrierungsmethoden m&#252;ssen &#252;bereinstimmen | Microsoft Docs"
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
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
helpviewer_keywords: 
  - "CA1410"
  - "ComRegistrationMethodsShouldBeMatched"
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1410: Die COM-Registrierungsmethoden m&#252;ssen &#252;bereinstimmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ deklariert eine mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>\-Attribut markierte Methode, jedoch keine mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>\-Attribut markierte Methode oder umgekehrt.  
  
## Regelbeschreibung  
 Damit Component Object Model \(COM\)\-Clients einen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Typ erstellen kann, muss der Typ zuerst registriert werden.  Falls verfügbar, wird während des Registrierungsprozesses eine mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>\-Attribut markierte Methode aufgerufen, um benutzerdefinierten Code auszuführen.  Beim Aufheben der Registrierung wird eine entsprechende, mit dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\-Attribut markierte Methode aufgerufen, um die Operationen der Registrierungsmethode umzukehren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die entsprechende Methode für die Registrierung oder das Aufheben der Registrierung hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  Der kommentierte Code zeigt, wie der Verstoß behoben wird.  
  
 [!code-cs[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## Verwandte Regeln  
 [CA1411: Die COM\-Registrierungsmethoden dürfen nicht sichtbar sein](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Registering Assemblies with COM](../Topic/Registering%20Assemblies%20with%20COM.md)   
 [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md)