---
title: "Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified. | Microsoft Docs"
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
  - "vs.message.0x800A00CD"
  - "vs.message.VS_E_NOTVALIDWITHSTOP"
ms.assetid: 1dea2450-034e-4a7f-b959-2060811329b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command does not accept additional switches or arguments if the switch &quot;/stop&quot; has been specified.
Im Allgemeinen tritt dieser Fehler auf, wenn der Schalter `/stop` mit weiteren Schaltern für die Befehle **Suche in Dateien** oder **In Dateien ersetzen** eingegeben wurde.  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie die aktuelle Operation **Suche in Dateien** beenden möchten, geben Sie Folgendes ein:  
  
    ```  
    Edit.FindinFiles /stop.  
    ```  
  
2.  Wenn Sie die aktuelle Operation **In Dateien ersetzen** beenden möchten, geben Sie Folgendes ein:  
  
    ```  
    Edit.ReplaceinFiles /stop  
    ```  
  
3.  Wenn Sie eine neue Operation **Suche in Dateien** oder **In Dateien ersetzen** starten möchten, geben Sie den Befehl ohne `/stop` erneut ein.  
  
## Siehe auch  
 [Befehl "In Dateien ersetzen"](../ide/reference/replace-in-files-command.md)   
 [Befehl "In Dateien suchen"](../ide/reference/find-in-files-command.md)   
 [Visual Studio\-Befehle](../ide/reference/visual-studio-commands.md)