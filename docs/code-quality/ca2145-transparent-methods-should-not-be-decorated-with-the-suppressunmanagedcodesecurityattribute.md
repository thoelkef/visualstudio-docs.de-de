---
title: "CA2145: Transparente Methoden sollten nicht mit dem SuppressUnmanagedCodeSecurityAttribute ergänzt werden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c6fcfc32dc8ab8a90ea555f43c253a5d93e72a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Transparente Methoden dürfen nicht mit dem SuppressUnmanagedCodeSecurity-Attribut versehen werden
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine transparente Methode, eine Methode, die mit der <xref:System.Security.SecuritySafeCriticalAttribute> -Methode oder ein Typ, der eine Methode enthält ist mit markiert die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Methoden mit ergänzt die <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Attribut haben einen impliziten LinkDemand nach jeder Methode, die ihn aufruft. Dieser LinkDemand erfordert, dass der aufrufende Code sicherheitskritisch ist. Das Markieren der Methode, die SuppressUnmanagedCodeSecurity mit dem <xref:System.Security.SecurityCriticalAttribute> Attribut wird diese Anforderung für Aufrufer der Methode leichter ersichtlich.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode aus, oder geben Sie mit der <xref:System.Security.SecurityCriticalAttribute> Attribut.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>Kommentare