---
title: "File name &lt;name&gt; cannot contain character device names. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0077"
  - "vs.message.VB_E_TERRFILECHARDEVINVALID"
ms.assetid: bb6e2e7a-1387-49be-927e-1dbbcafb65b1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# File name &lt;name&gt; cannot contain character device names.
Im Allgemeinen tritt dieser Fehler auf, wenn ein Dateiname eingegeben wird, bei dem es sich eigentlich um den Namen eines zeichenorientierten Geräts handelt.  Dies sind u. a. CON, PRN, AUX, CLOCK$, NUL, LPT1, LPT2, COM1, COM2, COM3 und COM4.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie einen anderen Dateinamen ein.  
  
## Siehe auch  
 [NIB: Save File As Dialog Box](http://msdn.microsoft.com/de-de/22380a20-2858-4391-b2f2-80c6bce64f14)   
 [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)