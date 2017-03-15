---
title: "Der Friend-Assemblyverweis &lt;verweis&gt; ist ung&#252;ltig F&#252;r InternalsVisibleTo-Deklarationen kann keine Version, keine Kultur, kein &#246;ffentliches Schl&#252;sseltoken und keine Prozessorarchitektur angegeben werden. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Friend-Assemblyverweis &lt;verweis&gt; ist ung&#252;ltig F&#252;r InternalsVisibleTo-Deklarationen kann keine Version, keine Kultur, kein &#246;ffentliches Schl&#252;sseltoken und keine Prozessorarchitektur angegeben werden.
Der Name, der an den <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>\-Attributkonstruktor übergeben wurde, enthält ein Attribut `Version`, `Culture`, `PublicKeyToken` oder `processorArchitecture`.  
  
 **Fehler\-ID:** BC31534  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das Attribut `Version`, `Culture`, `PublicKeyToken` oder `processorArchitecture` aus dem an den <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>\-Attributkonstruktor übergebenen Assemblynamen.  
  
## Siehe auch  
 <xref:System.Reflection.AssemblyName>   
 [NICHT IM BUILD: Friend\-Assemblys \(Visual Basic\)](http://msdn.microsoft.com/de-de/80e7a33a-ca91-450b-a00e-c5a7986e228c)