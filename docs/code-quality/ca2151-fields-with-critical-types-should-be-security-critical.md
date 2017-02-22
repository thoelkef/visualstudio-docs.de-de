---
title: "CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2151: Felder mit kritischen Typen sollten sicherheitskritisch sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein sicherheitstransparentes Feld oder ein sicherungskritisches Feld wird deklariert.  Sein Typ wird als sicherheitskritisch angegeben.  Beispiel:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 In diesem Beispiel ist `m_field` ein sicherheitstransparentes Feld eines Typs, der sicherheitskritisch ist.  
  
## Regelbeschreibung  
 Um sicherheitskritische Typen zu verwenden, muss der Code, der auf den Typ verweist, entweder sicherheitskritisch oder sicherungskritisch sein.  Dies gilt auch, wenn der Verweis indirekt ist.  Wenn Sie beispielsweise auf ein transparentes Feld verweisen, das über einen kritischen Typ verfügt, muss der Code entweder sicherheitskritisch oder sicherungskritisch sein.  Daher kann ein sicherheitstransparentes oder sicherungskritisches Feld irreführend sein, denn transparenter Code kann trotzdem nicht auf das Feld zugreifen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie das Feld mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut, oder ändern Sie den Typ, auf den durch das Feld verwiesen wird, in sicherheitstransparent oder sicherungskritisch.  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
### Code  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### Kommentare