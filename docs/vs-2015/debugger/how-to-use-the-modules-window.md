---
title: 'Gewusst wie: Verwenden des Fensters "Module" | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696124"
---
# <a name="how-to-use-the-modules-window"></a>Gewusst wie: Verwenden des Fensters Module
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Diese Funktion ist für das SQL-Debuggen nicht verfügbar.  
  
 Im Fenster **Module** werden die DLLs und die exe-Datei aufgelistet, die von Ihrem Programm verwendet werden, und die jeweils relevanten Informationen werden angezeigt.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>So zeigen Sie das Fenster Module im Unterbrechungsmodus oder Ausführungsmodus an  
  
- Wählen Sie im Menü **Debuggen** die Option **Fenster**aus, und klicken Sie dann auf **Module**.  
  
     Module werden im Fenster **Module** standardmäßig nach der Ladereihenfolge sortiert. Sie können sie jedoch nach einer beliebigen Spalte sortieren.  
  
### <a name="to-sort-by-any-column"></a>So sortieren Sie nach einer beliebigen Spalte  
  
- Klicken Sie auf die Schaltfläche am oberen Rand der Spalte.  
  
     Mithilfe des Kontextmenüs können Sie Symbole laden oder im Fenster **Module** einen Symbol Pfad angeben.  
  
## <a name="loading-symbols"></a>Laden von Symbolen  
 Im Fenster **Module** können Sie sehen, welche Module Debugsymbole geladen haben. Diese Informationen werden in der Spalte **Symbol Status** angezeigt. Wenn der Status "übersprungen" besagt, dass **die PDB-Datei nicht gefunden oder geöffnet werden kann**oder das **Laden durch die Einstellung "einschließen/ausschließen" deaktiviert**ist, können Sie den Debugger anweisen, Symbole von den öffentlichen Microsoft-Symbol Servern herunterzuladen oder Symbole aus einem Symbol Verzeichnis auf dem Computer zu laden. Weitere Informationen finden Sie unter [Angeben von Symbol-(PDB-) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
#### <a name="to-load-symbols-manually"></a>So laden Sie Symbole manuell  
  
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein Modul, für das keine Symbole geladen wurden.  
  
2. Zeigen Sie auf **Symbole laden aus** , und klicken Sie dann auf **Microsoft-Symbol Server** oder **Symbol Pfad**.  
  
#### <a name="to-change-symbol-load-settings"></a>So ändern Sie Einstellungen zum Laden von Symbolen  
  
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf ein beliebiges Modul.  
  
2. Klicken Sie auf **Symbol Einstellungen**.  
  
     Sie können nun die Symbol Ladeeinstellungen ändern, wie unter [Angeben von Symbol Positionen und laden Verhalten](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)beschrieben. Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>So ändern Sie das Symbolladeverhalten für ein bestimmtes Modul  
  
1. Klicken Sie im Fenster **Module** mit der rechten Maustaste auf das Modul.  
  
2. Zeigen Sie auf **Automatische Symbol Ladeeinstellungen** , und klicken Sie dann auf **immer manuell** oder **standardmäßig**laden. Änderungen werden erst wirksam, wenn die Debugsitzung neu gestartet wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abbrechen der Ausführung](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
