---
title: "Die Codierung kann nicht auf &#39;Nothing&#39; festgelegt werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Codierung kann nicht auf &#39;Nothing&#39; festgelegt werden
Fehler bei einem Lese\- oder Schreibversuch aus einer bzw. in eine Datei, da der Parameter `encoding` auf `Nothing` festgelegt wurde; es ist jedoch ein gültiger Wert erforderlich.  
  
 <xref:System.Text.Encoding> wird verwendet, um zu bestimmen, welche Codierung beim Schreiben in eine Datei verwendet werden soll.  Der Standardwert ist UTF\-8.  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie einen gültigen Wert für den `encoding`\-Parameter an.  
  
## Siehe auch  
 [File Encodings](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-encodings)   
 [Reading from Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/reading-from-files)   
 [Writing to Files](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/writing-to-files)   
 [My.Computer.FileSystem.ReadAllText\-Methode](http://msdn.microsoft.com/de-de/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [My.Computer.FileSystem.WriteAllText\-Methode](http://msdn.microsoft.com/de-de/f507460c-87d9-4504-b74f-3ff825c7d5c4)