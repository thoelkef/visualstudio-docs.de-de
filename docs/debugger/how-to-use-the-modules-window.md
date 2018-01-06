---
title: "Anzeigen von DLLs und ausführbaren Dateien im Debugger | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 772c252265e15c3c928fbcc47c756ceafd9e1362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Anzeigen von DLLs und ausführbare Dateien mithilfe des Fensters Module in der Visual Studio-Debugger
 
Die **Module** Fenster DLLs und ausführbare Dateien (EXE), die verwendet werden, durch das Programm und relevante Informationen für jeden aufgelistet. 

> [!NOTE]
>  Diese Funktion ist für das SQL-Debuggen nicht verfügbar. 
  
### <a name="to-display-the-modules-window"></a>Zum Anzeigen des Fensters Module  
  
-   Wählen Sie während des Debuggens, **Debuggen > Windows** , und klicken Sie dann auf **Module**.  
  
     Wird standardmäßig die **Module** Fenster wird Module nach der Ladereihenfolge sortiert. Sie können sie jedoch nach einer beliebigen Spalte sortieren.  
  
### <a name="to-sort-by-any-column"></a>So sortieren Sie nach einer beliebigen Spalte  
  
-   Klicken Sie auf die Schaltfläche am oberen Rand der Spalte.  
  
     Sie können Symbole laden oder einen Symbolpfad angeben der **Module** Fenster über das Kontextmenü.  
  
## <a name="loading-symbols"></a>Laden von Symbolen  
 In der **Module** Fenster können Sie sehen, welche Module Debugsymbole geladen. Diese Informationen angezeigt, der **Symbolstatus** Spalte. Lautet der Status **übersprungen LoadingCannot suchen oder öffnen Sie die PDB-Datei**, oder **laden, die durch die Einstellung zum Einschließen/Ausschließen deaktiviert**, Sie können den Debugger zum Herunterladen der Symbole von den öffentlichen Microsoft-Symboldateien weiterleiten Server oder um Symbole aus einem Symbolverzeichnis auf Ihrem Computer zu laden. Weitere Informationen finden Sie unter [geben Symboldateien (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>So laden Sie Symbole manuell  
  
1.  In der **Module** Fenster, mit der rechten Maustaste ein Modul, die für den keine Symbole geladen wurden.  
  
2.  Zeigen Sie auf **Symbole laden aus** , und klicken Sie dann auf **Microsoft-Symbolserver** oder **Symbolpfad**.  
  
#### <a name="to-change-symbol-load-settings"></a>So ändern Sie Einstellungen zum Laden von Symbolen  
  
1.  In der **Module** Fenster mit der rechten Maustaste ein Modul.  
  
2.  Klicken Sie auf **Symbol Settings**.  
  
     Sie können jetzt die ladeeinstellungen Symbol ändern, wie in beschrieben [angeben der symboldateispeicherorte und des Ladeverhaltens](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>So ändern Sie das Symbolladeverhalten für ein bestimmtes Modul  
  
1.  In der **Module** Fenster mit der rechten Maustaste in des Moduls.  
  
2.  Zeigen Sie auf **automatische Symbol Ladeeinstellungen** , und klicken Sie dann auf **immer manuell laden** oder **Standard**. Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterbrechen der Ausführung](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)