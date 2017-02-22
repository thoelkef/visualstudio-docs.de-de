---
title: "Wie k&#246;nnen Zugriffsverletzungen, die beim Ausf&#252;hren des Programms au&#223;erhalb des Debuggers auftreten, gedebuggt werden? | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Zugriffsverletzungsdebuggen"
  - "Debuggen [Visual Studio], Zugriffsverletzungen"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie k&#246;nnen Zugriffsverletzungen, die beim Ausf&#252;hren des Programms au&#223;erhalb des Debuggers auftreten, gedebuggt werden?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Problembeschreibung  
 Das Programm läuft in der Visual Studio\-Umgebung einwandfrei. Wird es jedoch eigenständig unter dem Windows\-Betriebssystem ausgeführt, generiert es eine Zugriffsverletzung.  Wie kann dieses Problem behoben werden?  
  
## Lösung  
 Legen Sie die Option für das [Just\-In\-Time\-Debuggen](../debugger/just-in-time-debugging-in-visual-studio.md) fest, und führen Sie das Programm im eigenständigen Modus aus, bis eine Zugriffsverletzung auftritt.  Dann können Sie im Dialogfeld **Zugriffsverletzung** auf **Abbrechen** klicken, um den Debugger zu starten.  
  
 Weitere Informationen finden Sie im Knowledge Base\-Artikel Q133174, "How to Locate Where a General Protection \(GP\) Fault Occurs" \(nur auf Englisch verfügbar\). Sie finden Knowledge Base\-Artikel in MSDN Library\-Medien oder unter [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)