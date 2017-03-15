---
title: "Miscellaneous Files projects can contain &lt;number&gt; items. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0062"
  - "vs.message.VB_E_INVALIDMISCLISTRANGE"
ms.assetid: 40bcce2a-3ff5-482a-a188-79b143080138
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Miscellaneous Files projects can contain &lt;number&gt; items.
Im Projekt **Verschiedene Dateien** können bis zu 256 Elemente gespeichert werden.  Im Allgemeinen tritt dieser Fehler auf, wenn im Dialogfeld **Optionen** unter **Umgebung** im Bereich **Dokumente** im Feld **Projekt für verschiedene Dateien speichert die letzten \<Anzahl\> Elemente** eine Zahl eingegeben wurde, die kleiner als 1 oder größer als 256 ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie im Feld eine Zahl zwischen 1 und 256 ein.  
  
## Siehe auch  
 [Dokumente, Umgebung, Dialogfeld "Optionen"](../ide/reference/documents-environment-options-dialog-box.md)