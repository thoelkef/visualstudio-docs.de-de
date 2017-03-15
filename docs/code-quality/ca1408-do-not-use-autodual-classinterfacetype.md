---
title: "CA1408: AutoDual ClassInterfaceType nicht verwenden | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408: AutoDual ClassInterfaceType nicht verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein sichtbarer Component Object Model \(COM\)\-Typ wird mit dem auf den `AutoDual`\-Wert von <xref:System.Runtime.InteropServices.ClassInterfaceType> festgelegten <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>\-Attribut markiert.  
  
## Regelbeschreibung  
 Typen, die eine duale Schnittstelle verwenden, ermöglichen Clients die Bindung an ein bestimmtes Schnittstellenlayout.  Änderungen an einer zukünftigen Version des Layouts des Typs oder eines Basistyps führen zur Aufhebung der Verbindung zu COM\-Clients, die eine Bindung zu der Schnittstelle haben.  Standardmäßig wird eine auf Dispatch beschränkte Schnittstelle verwendet, wenn das <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>\-Attribut nicht angegeben wird.  
  
 Sofern nicht anders markiert, sind alle öffentlichen, nicht generischen Typen für COM sichtbar; alle nicht öffentlichen, generischen Typen sind für COM nicht sichtbar.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert des <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>\-Attributs in den `None`\-Wert von <xref:System.Runtime.InteropServices.ClassInterfaceType>, und definieren Sie die Schnittstelle explizit.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, es steht fest, dass das Layout des Typs und der zugehörigen Basistypen in einer zukünftigen Version nicht geändert werden.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Klasse veranschaulicht, die gegen die Regel verstößt. Diese Klasse wird neu deklariert, sodass eine explizite Schnittstelle verwendet wird.  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## Verwandte Regeln  
 [CA1403: Typen mit automatischem Layout sollten nicht für COM sichtbar sein](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: ComSource\-Schnittstellen als IDispatch markieren](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## Siehe auch  
 [Introducing the Class Interface](http://msdn.microsoft.com/de-de/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)