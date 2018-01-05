---
title: "CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ea4d0adf3573410c9f8a25e6b5d3abf2615c8ad3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Assemblys der Stufe 2 dürfen keine LinkDemands enthalten
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Klasse oder ein Member der Klasse verwendet eine <xref:System.Security.Permissions.SecurityAction> in einer Anwendung, die Sicherheit der Ebene 2 verwendet.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet. Markieren Sie, statt LinkDemands zur Erzwingung von Sicherheit zur Just-in-Time (JIT)-Kompilierungszeit zu erzwingen, die Methoden, Typen und Felder mit den <xref:System.Security.SecurityCriticalAttribute> Attribut.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die <xref:System.Security.Permissions.SecurityAction> und markieren Sie den Typ oder Member mit dem <xref:System.Security.SecurityCriticalAttribute> Attribut.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel die <xref:System.Security.Permissions.SecurityAction> entfernt werden, und die Methode gekennzeichnet wird, mit der <xref:System.Security.SecurityCriticalAttribute> Attribut.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]