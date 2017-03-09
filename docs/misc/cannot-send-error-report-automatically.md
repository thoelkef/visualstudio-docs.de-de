---
title: "Fehlerbericht kann nicht automatisch gesendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehlerbericht kann nicht automatisch gesendet werden
Der Fehlerbericht kann nicht automatisch gesendet werden. Informationen zum Konfigurieren von Einstellungen für das Senden von Fehlerberichten finden Sie unter „http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039“.  
  
 Sie haben die `/errorreport:send`\-Compileroption angegeben, aber der Computer ist nicht für das automatische Senden von Fehlerberichten konfiguriert. Es werden keine Informationen zu internen Fehlern im Visual Basic\-Compiler gesendet.  
  
 **Fehler\-ID:** BC2027  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `/errorreport:send`\-Compileroption, oder ersetzen Sie diese durch `/errorreport:queue`, `/errorreport:prompt` oder `/errorreport:none`.  
  
     Oder  
  
-   Aktivieren Sie die automatische Fehlerberichterstattung, indem Sie die Anweisungen unter [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039) ausführen.  
  
## Siehe auch  
 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)   
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)