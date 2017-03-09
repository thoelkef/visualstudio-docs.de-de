---
title: "Problembehandlung bei Ausnahmen: System.ComponentModel.Win32Exception | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Win32Exception-Ausnahme"
  - "System.ComponentModel.Win32Exception-Ausnahme"
ms.assetid: 6d5facbd-34f0-4f04-a7df-2bf62d676529
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ComponentModel.Win32Exception
Die Ausnahme wird für einen Win32\-Fehlercode ausgelöst.  
  
## Hinweise  
 Win32\-Fehlercodes werden aus ihren numerischen Darstellungen in eine Systemmeldung übersetzt, wenn sie angezeigt werden. Verwenden Sie die <xref:System.ComponentModel.Win32Exception.NativeErrorCode%2A>\-Eigenschaft, um auf die numerische Darstellung des Fehlercodes zuzugreifen.  
  
## Siehe auch  
 <xref:System.ComponentModel.Win32Exception>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Wo sind die Win32\-Fehlercodes zu finden?](../debugger/where-can-i-look-up-win32-error-codes-q.md)