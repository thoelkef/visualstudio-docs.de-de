---
title: "Keine Quelle verf&#252;gbar | Microsoft Docs"
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
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Für die aktuelle Position ist kein Quellcode verfügbar (Dialogfeld)"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Keine Quelle verf&#252;gbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Projekt enthält keinen Quellcode für den Code, den Sie anzeigen möchten.  Grund hierfür ist meist, dass Sie durch Doppelklicken ein Modul ausgewählt haben, für das im **Aufruflistenfenster** oder im **Threadfenster** kein Quellcode vorhanden ist.  Sie können das Debuggen fortsetzen, jedoch das Quellcodefenster nicht zum Festlegen von Haltepunkten und zum Durchführen anderer Aktionen an dieser Position verwenden.  Wenn Sie einen Haltepunkt setzen müssen, verwenden Sie stattdessen das **Disassemblyfenster**.  
  
 Auf den Eigenschaftenseiten für Projektmappen können Sie die Verzeichnisse ändern, in denen der Debugger nach Quelldateien sucht, und den Debugger anweisen, die ausgewählten Quelldateien zu ignorieren.  Siehe [Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten \(Dialogfeld\)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 Link für **Zum Quellcode navigieren**  
 Klicken Sie auf diesen Link, um ein Dialogfeld zu öffnen, in dem Sie nach dem Quellcode suchen können.  
  
 **Disassembly anzeigen**  
 Öffnet das **Disassemblyfenster**.  
  
 **Disassembly für fehlende Quelldateien immer anzeigen**  
 Wählen Sie diese Option aus, um das **Disassemblyfenster** automatisch anzuzeigen, wenn kein Quellcode verfügbar ist.  Diese Einstellung kann auch im Dialogfeld **Optionen** in der Kategorie **Debuggen** auf der Seite **Allgemein** geändert werden, indem das Kontrollkästchen **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist** aktiviert oder deaktiviert wird.  
  
## Siehe auch  
 [Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten \(Dialogfeld\)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)