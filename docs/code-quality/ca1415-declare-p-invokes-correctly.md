---
title: "CA1415: P/Invokes korrekt deklarieren | Microsoft Docs"
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
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415: P/Invokes korrekt deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn das P\/Invoke, das den Parameter deklariert, außerhalb der Assembly nicht sichtbar ist.  Nicht unterbrechend – Wenn das P\/Invoke, das den Parameter deklariert, außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Eine Plattformaufrufmethode wurde falsch deklariert.  
  
## Regelbeschreibung  
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code zu und wird mit dem `Declare`\-Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> definiert.  Derzeit sucht diese Regel nach Deklarationen für eine Plattformaufrufmethode, die Win32\-Funktionen mit einem Zeiger auf einen OVERLAPPED\-Strukturparameter zum Ziel haben, der zugehörige verwaltete Parameter ist jedoch kein Zeiger auf eine <xref:System.Threading.NativeOverlapped?displayProperty=fullName>\-Struktur.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, deklarieren Sie die Plattformaufrufmethode korrekt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden Plattformaufrufmethoden veranschaulicht, die gegen die Regel verstoßen und die Regel einhalten.  
  
 [!code-cs[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## Siehe auch  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)