---
title: "CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 880f48a3fc6f9ae09191d8d63120e7d71091118b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: Transparente Methoden dürfen keine LinkDemands erfüllen
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine sicherheitstransparente Methode ruft eine Methode in einer Assembly, die nicht mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) oder eine sicherheitstransparente Methode erfüllt einen <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` für einen Typ oder eine Methode.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 LinkDemand erfüllen ist einen sicherheitsrelevanten Vorgang, der unbeabsichtigten Ausweitung von Berechtigungen verursachen kann. Sicherheitstransparenter Code muss LinkDemands, nicht erfüllen, da sie nicht gelten die gleichen sicherheitsanforderungen für die Überwachung als sicherheitsrelevanten Code ist. Transparente Methoden in Security Regel Satz Assemblys der Ebene 1 verursachen alle LinkDemands erfüllen, um vollständige Anforderungen zur Laufzeit konvertiert werden, die zu Leistungsproblemen führen kann. In Assemblys mit Sicherheit Regel Satz Ebene 2 werden transparente Methoden nicht in der Just-in-Time (JIT)-Compiler kompiliert werden soll, wenn sie versuchen, einen LinkDemand zu erfüllen.  
  
 In Assemblys, mit Level 2-Sicherheit, Versuche durch eine sicherheitstransparente Methode erfüllt einen LinkDemand oder eine Methode in einer nicht-APTCA-Assembly aufrufen löst eine <xref:System.MethodAccessException>; in Assemblys der Ebene 1 LinkDemand wird zu einer vollständigen Anforderung.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Zugriffsmethode mit der <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, oder entfernen Sie die LinkDemand aus der Methode zugegriffen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird versucht, eine transparente Methode zum Aufrufen einer Methode, die über einen LinkDemand verfügt. Mit dieser Regel wird für diesen Code ausgelöst werden.  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]