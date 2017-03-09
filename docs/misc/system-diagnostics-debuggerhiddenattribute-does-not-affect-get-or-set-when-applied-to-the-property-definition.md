---
title: "System.Diagnostics.DebuggerHiddenAttribute hat bei Anwendung auf die Eigenschaftsdefinition keine Auswirkungen auf &quot;Get&quot; oder &quot;Set&quot;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40051"
  - "vbc40051"
helpviewer_keywords: 
  - "BC40051"
ms.assetid: 623d5e48-7fb2-48a9-bbbb-92914b08c01c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Diagnostics.DebuggerHiddenAttribute hat bei Anwendung auf die Eigenschaftsdefinition keine Auswirkungen auf &quot;Get&quot; oder &quot;Set&quot;.
System.Diagnostics.DebuggerHiddenAttribute hat bei Anwendung auf die Eigenschaftsdefinition keine Auswirkungen auf 'Get' oder 'Set'. Wenden Sie das Attribut direkt auf die „Get“\- und "Set"\-Verfahren an.  
  
 Das <xref:System.Diagnostics.DebuggerHiddenAttribute> wird auf eine Eigenschaftsdeklaration angewendet.  
  
 Der Quellcode kann das <xref:System.Diagnostics.DebuggerHiddenAttribute> auf eine Prozedur anwenden. Dies signalisiert dem Visual Studio\-Debugger, dass innerhalb der Prozedur kein Beenden möglich ist und es zudem nicht gestattet ist, Haltepunkte in der Prozedur festzulegen.  
  
 Obwohl Sie <xref:System.Diagnostics.DebuggerHiddenAttribute> auf eine Eigenschaft anwenden können, hat dies keine Auswirkung. Es hat nur den gewünschten Effekt, wenn Sie es auf die `Get`\- oder `Set`\-Prozedur der Eigenschaft anwenden.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40051  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das <xref:System.Diagnostics.DebuggerHiddenAttribute> aus der Eigenschaftendeklaration, und wenden Sie es entsprechend auf die `Get`\- oder `Set`\-Prozeduren der Eigenschaft an.  
  
## Siehe auch  
 <xref:System.Diagnostics.DebuggerHiddenAttribute>   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)