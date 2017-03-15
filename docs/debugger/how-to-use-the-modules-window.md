---
title: "Gewusst wie: Verwenden des Fensters Module | Microsoft Docs"
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
  - "vs.debug.modules"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Module (Fenster)"
  - "Module (Fenster)"
  - "Ausführbare Dateien, Anzeigen beim Debuggen"
  - "Debuggen [Visual Studio], Anzeigen von Modulen"
  - "DLLs, Anzeigen beim Debuggen"
  - "Module, anzeigen"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden des Fensters Module
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Dieses Feature ist für das SQL\-Debuggen nicht verfügbar.  
  
 Im Fenster **Module** werden die vom Programm verwendeten DLLs und die EXE aufgelistet, und die jeweils dafür relevanten Informationen werden angezeigt.  
  
### So zeigen Sie das Fenster Module im Unterbrechungsmodus oder Ausführungsmodus an  
  
-   Wählen Sie im Menü **Debuggen** die Option **Fenster** aus, und klicken Sie dann auf **Module**.  
  
     Module werden im Fenster **Module** standardmäßig nach der Ladereihenfolge sortiert.  Sie können sie jedoch nach einer beliebigen Spalte sortieren.  
  
### So sortieren Sie nach einer beliebigen Spalte  
  
-   Klicken Sie auf die Schaltfläche am oberen Rand der Spalte.  
  
     Sie können über das Kontextmenü im Fenster **Module** Symbole laden oder einen Symbolpfad angeben.  
  
## Laden von Symbolen  
 Im Fenster **Module** können Sie feststellen, für welche Module Debugsymbole geladen sind.  Diese Informationen werden in der Spalte **Symbolstatus** angezeigt.  Lautet der Status **Das Laden von Symbolen wurde übersprungen**, **PDB\-Datei wurde nicht gefunden oder konnte nicht geöffnet werden** oder **Der Ladevorgang wurde durch die Einstellung zum Einschließen\/Ausschließen deaktiviert**, können Sie den Debugger anweisen, Symbole von den öffentlichen Microsoft\-Symbolservern herunterzuladen oder Symbole aus einem Symbolverzeichnis auf dem Computer zu laden.  Weitere Informationen finden Sie unter [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### So laden Sie Symbole manuell  
  
1.  Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein Modul, für das keine Symbole geladen wurden.  
  
2.  Zeigen Sie auf **Symbole laden aus**, und klicken Sie dann auf **Microsoft\-Symbolserver** oder **Symbolpfad**.  
  
#### So ändern Sie Einstellungen zum Laden von Symbolen  
  
1.  Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein beliebiges Modul.  
  
2.  Klicken Sie auf **Symboleinstellungen**.  
  
     Sie können nun die Einstellungen zum Laden von Symbolen ändern, wie unter [Angeben der Symboldateispeicherorte und des Ladeverhaltens](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior) beschrieben.  Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
#### So ändern Sie das Symbolladeverhalten für ein bestimmtes Modul  
  
1.  Klicken Sie im Fenster **Module** mit der rechten Maustaste auf das Modul.  
  
2.  Zeigen Sie auf **Einstellungen zum automatischen Laden von Symbolen**, und klicken Sie dann auf **Immer manuell laden** oder **Standard**.  Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
## Siehe auch  
 [Breaking Execution](http://msdn.microsoft.com/de-de/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)