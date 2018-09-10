---
title: Anzeigen von DLLs und ausführbare Dateien in den Debugger | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f582c435239c83503b179d6bb5e142936a41cb4b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279010"
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Anzeigen von DLLs und ausführbare Dateien mithilfe der Fenster "Module" im Visual Studio-Debugger
 
Die **Module** DLLs und ausführbare Dateien (EXE), die von Ihrem Programm verwendet werden, und zeigt relevante Informationen für die einzelnen Fenster aufgelistet. 

> [!NOTE]
>  Diese Funktion ist für das SQL-Debuggen nicht verfügbar. 
  
### <a name="to-display-the-modules-window"></a>Um das Fenster "Module" anzuzeigen.  
  
-   Wählen Sie während des Debuggens, **Debuggen > Windows** , und klicken Sie dann auf **Module**.  
  
     In der Standardeinstellung die **Module** Fenster nach Modulen Ladereihenfolge sortiert. Sie können sie jedoch nach einer beliebigen Spalte sortieren.  
  
### <a name="to-sort-by-any-column"></a>So sortieren Sie nach einer beliebigen Spalte  
  
-   Klicken Sie auf die Schaltfläche am oberen Rand der Spalte.  
  
     Sie können Symbole laden oder einen Symbolpfad angeben der **Module** Fenster über das Kontextmenü.  
  
## <a name="loading-symbols"></a>Laden von Symbolen  
 In der **Module** Fenster können Sie sehen, welche Module Debugsymbole geladen. Diese Informationen angezeigt, der **Symbolstatus** Spalte. Lautet der Status **übersprungen LoadingCannot finden oder öffnen Sie die PDB-Datei**, oder **laden, die von der Einstellung zum Einschließen/Ausschließen deaktiviert**, können Sie den Debugger, um Symbole von den öffentlichen Microsoft-Symboldateien herunterzuladen leiten Server oder zum Laden der Symbole aus einem Symbolverzeichnis auf Ihrem Computer. Weitere Informationen finden Sie unter [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>So laden Sie Symbole manuell  
  
1.  In der **Module** Fenster mit der rechten Maustaste ein Modul, die für den keine Symbole geladen wurden.  
  
2.  Zeigen Sie auf **Symbole laden aus** , und klicken Sie dann auf **Microsoft-Symbolserver** oder **Symbolpfad**.  
  
#### <a name="to-change-symbol-load-settings"></a>So ändern Sie Einstellungen zum Laden von Symbolen  
  
1.  In der **Module** Fenster mit der rechten Maustaste ein Modul.  
  
2.  Klicken Sie auf **Symboleinstellungen**.  
  
     Sie können jetzt die Symbol-laden-Einstellungen ändern, wie in beschrieben [angeben der symboldateispeicherorte und des Ladeverhaltens](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>So ändern Sie das Symbolladeverhalten für ein bestimmtes Modul  
  
1.  In der **Module** Fenster mit der rechten Maustaste in des Moduls.  
  
2.  Zeigen Sie auf **automatische Symboleinstellungen laden** , und klicken Sie dann auf **immer manuell laden** oder **Standard**. Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterbrechen der Ausführung](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)