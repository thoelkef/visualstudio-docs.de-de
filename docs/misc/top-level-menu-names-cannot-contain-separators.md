---
title: "Top-level menu names cannot contain separators. | Microsoft Docs"
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
  - "vs.message.VB_E_IDWSELECTIONHASSEPS"
  - "vs.message.0x800A0033"
ms.assetid: 227bd38e-24ec-4a8d-9f12-11cf21a74796
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Top-level menu names cannot contain separators.
Im Allgemeinen tritt dieser Fehler auf, wenn Text in einen Menünamen gezogen wird, der ein Trennzeichen enthält, z. B. einen Bindestrich \(\-\).  Hauptebenenmenüs dürfen dieses Zeichen nicht enthalten, da es für das Trennen von Menüelementgruppen reserviert ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie den Text ohne das Trennzeichen ein.