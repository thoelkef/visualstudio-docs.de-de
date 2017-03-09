---
title: "CA1412: ComSource-Schnittstellen als IDispatch markieren | Microsoft Docs"
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
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412: ComSource-Schnittstellen als IDispatch markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ ist mit dem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>\-Attribut markiert, und mindestens eine der angegebenen Schnittstellen ist nicht mit dem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>\-Attribut markiert, das auf den `InterfaceIsDispatch`\-Wert festgelegt ist.  
  
## Regelbeschreibung  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> wird verwendet, um die Ereignisschnittstellen zu identifizieren, die eine Klasse für COM\-Clients \(Component Object Model \) verfügbar macht.  Diese Schnittstellen müssen als `InterfaceIsIDispatch` verfügbar gemacht werden, damit Visual Basic 6\-COM\-Clients Ereignisbenachrichtigungen empfangen können.  Standardmäßig wird eine Schnittstelle, die nicht mit dem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>\-Attribut markiert ist, als duale Schnittstelle verfügbar gemacht.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>\-Attribut hinzu bzw. ändern dieses, sodass der zugehörige Wert für alle Schnittstellen, die mit dem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>\-Attribut angegeben werden, auf InterfaceIsIDispatch festgelegt wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Klasse dargestellt, in der eine der Schnittstellen gegen die Regel verstößt.  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## Verwandte Regeln  
 [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Siehe auch  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/de-de/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)