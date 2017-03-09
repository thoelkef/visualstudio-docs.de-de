---
title: "Overflow. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_OVERFLOW"
  - "vs.message.0x800A0097"
ms.assetid: 632387b9-be9c-4744-bcc5-842c45582347
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Overflow.
Eine Zuweisung hat die Einschränkungen des Zuweisungsziels überschritten.  Im Allgemeinen tritt dieser Fehler auf, wenn eine der folgenden Situationen vorliegt:  
  
-   Das Ergebnis einer Zuweisung, Berechnung oder Datentypkonvertierung ist zu groß, um innerhalb des Wertebereichs dargestellt zu werden, der für diesen Variablentyp zulässig ist.  
  
-   Eine Zuweisung zu einer Eigenschaft überschreitet den Höchstwert, den die Eigenschaft annehmen kann.  
  
-   Es wird versucht, eine Zahl in einer Berechnung zu verwenden. Diese Zahl wird in eine ganze Zahl konvertiert, das Ergebnis ist jedoch größer als eine ganze Zahl.  
  
### So beheben Sie diesen Fehler  
  
1.  Weisen Sie den Wert einer Variablen eines Typs zu, der einen größeren Wertebereich enthalten kann.  
  
     \- oder \-  
  
     Stellen Sie sicher, dass die Zuweisung dem Bereich der Eigenschaft entspricht, der sie zugewiesen wird.