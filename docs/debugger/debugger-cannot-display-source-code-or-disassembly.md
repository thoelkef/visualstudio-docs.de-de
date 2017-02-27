---
title: "Debugger kann keinen Quellcode oder Disassembly anzeigen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Disassemblierungscode, Fehler"
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Debugger kann keinen Quellcode oder Disassembly anzeigen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inhalt dieses Fehlers:  
  
 Der Debugger kann keinen Quellcode oder Disassembly für die aktuelle Position anzeigen.  
  
 Diese Fehlermeldung kann mehrere Ursachen haben:  
  
-   Während des Debuggens einer Sprache, die die Disassembly nicht unterstützt, wurde ein Haltepunkt an einer Position erreicht, für die kein Quellcode vorhanden ist.  Öffnen Sie das Fenster **Haltepunkte**, suchen Sie den Haltepunkt, und löschen Sie ihn.  
  
-   Beim Debuggen von Skripts wurde ein Haltepunkt erreicht, während das Programm keine Threads enthielt.  Wählen Sie im Menü **Debuggen** die Option **Schritt** oder **Weiter** aus, um das Debuggen fortzusetzen.  
  
-   Der Debugger konnte aus Sicherheitsgründen keine Stapel\-, Register\- und andere Kontextinformationen aus dem zu debuggenden Programm lesen.  Dies passiert meistens, wenn Sie eine Webanwendung debuggen und nicht die erforderlichen Berechtigungen für den Zugriff auf das virtuelle Verzeichnis haben.  Setzen Sie die Berechtigung für das virtuelle Verzeichnis auf **Anonym**, und führen Sie den Vorgang erneut aus.  
  
## Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)