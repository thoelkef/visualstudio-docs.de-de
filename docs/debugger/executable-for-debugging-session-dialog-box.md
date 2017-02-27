---
title: "Dialogfeld &quot;Ausf&#252;hrbare Datei f&#252;r die Debugsitzung&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exefordebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ausführbare Dateien, Angeben beim Debuggen"
  - "DLLs, debuggen"
  - "Debugger, Ausführbare Datei für die Debugsitzung (Dialogfeld)"
  - "Ausführbare Datei für die Debugsitzung (Dialogfeld)"
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Dialogfeld &quot;Ausf&#252;hrbare Datei f&#252;r die Debugsitzung&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn Sie eine DLL debuggen, für die keine ausführbare Datei festgelegt wurde.  In Visual Studio können DLLs nicht direkt gestartet werden.  Stattdessen wird die angegebene ausführbare Datei ausgeführt.  Sie können die DLL debuggen, wenn diese durch die ausführbare Datei aufgerufen wird.  
  
 **Name der ausführbaren Datei**  
 Geben Sie den Pfad zu einer ausführbaren Datei ein, mit der die zu debuggende DLL aufgerufen wird.  
  
 **URL, von der aus auf das Projekt zugegriffen werden kann \(nur ATL\-Server\)**  
 Wenn Sie eine ATL\-Server\-DLL debuggen, geben Sie die URL ein, unter der sich das Projekt befindet.  
  
 Nach der Eingabe werden diese Einstellungen in den Eigenschaftenseiten des Projekts gespeichert, sodass Sie diese bei späteren Debugsitzungen nicht erneut eingeben müssen.  Wenn Sie diese Einstellungen ändern möchten, können Sie die Eigenschaftenseiten öffnen und die Werte ändern.  Weitere Informationen zum Angeben einer ausführbaren Datei für die Debugsitzung finden Sie unter [Debuggen von DLLs](../debugger/how-to-debug-native-dlls.md).  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)