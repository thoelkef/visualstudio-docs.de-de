---
title: "&#39;&lt;Typname&gt;&#39; in Assembly &#39;&lt;Assemblyname&gt;&#39; wurde an sich selbst weitergeleitet und ist daher ein nicht unterst&#252;tzter Typ. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31425"
  - "vbc31425"
helpviewer_keywords: 
  - "BC31425"
  - "Typweiterleitung"
ms.assetid: e3275d55-3f4c-4bbc-9c8f-f55c4e973063
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Typname&gt;&#39; in Assembly &#39;&lt;Assemblyname&gt;&#39; wurde an sich selbst weitergeleitet und ist daher ein nicht unterst&#252;tzter Typ.
Eine Assembly verwendet das <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, um einen ihrer Typen an eine andere Assembly weiterzuleiten. Sie gibt jedoch in derselben Assembly denselben Typ an.  
  
 *Typweiterleitung* bedeutet, die Definition einer Klasse, Struktur, Schnittstelle, eines Delegaten oder einer Enumeration einer anderen als der ursprünglich definierten Assembly zuzuweisen. Sie wird häufig in Verbindung mit der *Umgestaltung von Code* verwendet, durch die Sie eine Assembly in zwei oder mehrere Assemblys aufteilen oder Code aus einer Assembly in eine andere verschieben können.  
  
 Das Weiterleiten eines Typs an sich selbst führt zur zirkulären Weiterleitung. Wenn eine andere Assembly versucht, auf den weitergeleiteten Typ zuzugreifen, würde dies zu einer endlosen Weiterleitung führen, ohne je einen Typ zu erreichen, der nicht weitergeleitet wurde.  
  
 **Fehler\-ID:** BC31425  
  
### So beheben Sie diesen Fehler  
  
-   Leiten Sie den Typ an einen Typ in einer anderen Assembly weiter, oder unterlassen Sie die Weiterleitung.  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)