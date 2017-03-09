---
title: "Verweis auf Datei &#39;&lt;Dateiname&gt;&#39; konnte nicht generiert werden. Verwenden Sie das TLBIMP-Dienstprogramm, um auf COM-DLLs zu verweisen: &lt;Fehlermeldung&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30142"
  - "bc30142"
helpviewer_keywords: 
  - "BC30142"
ms.assetid: ee0f2c77-3714-4ec2-bddf-d098ab77722f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Verweis auf Datei &#39;&lt;Dateiname&gt;&#39; konnte nicht generiert werden. Verwenden Sie das TLBIMP-Dienstprogramm, um auf COM-DLLs zu verweisen: &lt;Fehlermeldung&gt;
Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler ruft den Assemblylinker \(Al.exe, auch bekannt als Alink\) auf, um eine Assembly mit einem Manifest zu erstellen. Der Linker hat beim Suchen oder Validieren einer COM\+\-DLL\-Datei einen Fehler gemeldet.  
  
 **Fehler\-ID:** BC30142  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die angegebene Fehlermeldung, und gehen Sie zum Thema [Fehler und Warnungen des Al.exe\-Tools](http://msdn.microsoft.com/de-de/7f125d49-0a03-47a6-9ba9-d61a679a7d4b), um weitere Erläuterungen und Hinweise zu erhalten.  
  
2.  Wenn der gewünschte Verweis auf eine COM\-DLL anstatt auf eine COM\+\-DLL gerichtet ist, verwenden Sie den [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) um den Verweis zu generieren.  
  
3.  Wenn der Fehler weiterhin besteht, tragen Sie Informationen zu den Umständen zusammen, und benachrichtigen Sie den Produktsupport von Microsoft.  
  
## Siehe auch  
 [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Fehler und Warnungen des Al.exe\-Tools](http://msdn.microsoft.com/de-de/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [PAVEOVER Produktsupport und Barrierefreiheit](http://msdn.microsoft.com/de-de/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)