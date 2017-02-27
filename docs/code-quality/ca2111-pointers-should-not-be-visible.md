---
title: "CA2111: Zeiger sollten nicht sichtbar sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2111: Zeiger sollten nicht sichtbar sein.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentliches oder geschütztes <xref:System.IntPtr?displayProperty=fullName>\-Feld oder <xref:System.UIntPtr?displayProperty=fullName>\-Feld ist nicht schreibgeschützt.  
  
## Regelbeschreibung  
 <xref:System.IntPtr> und <xref:System.UIntPtr> sind Zeigertypen, die verwendet werden, um auf nicht verwalteten Arbeitsspeicher zuzugreifen.  Wenn ein Zeiger nicht privat, intern oder schreibgeschützt ist, kann bösartiger Code den Wert des Zeigers ändern und damit Zugriffe auf beliebige Speicherbereiche ermöglichen oder Anwendungs\- bzw. Systemfehler verursachen.  
  
 Wenn Sie Zugriff auf den Typ, der das Zeigerfeld enthält, schützen möchten, lesen Sie [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Behandeln von Verstößen  
 Schützen Sie den Zeiger, indem Sie ihn als schreibgeschützt, intern oder privat deklarieren.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn der Wert des Zeigers nicht von maßgeblicher Bedeutung ist.  
  
## Beispiel  
 Im folgenden Code werden Zeiger veranschaulicht, die gegen die Regel verstoßen, und Zeiger, die der Regel entsprechen.  Beachten Sie, dass auch nicht\-private Zeiger gegen die Regel [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) verstoßen.  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## Verwandte Regeln  
 [CA2112: Gesicherte Typen sollten keine Felder verfügbar machen.](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: Sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Siehe auch  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>