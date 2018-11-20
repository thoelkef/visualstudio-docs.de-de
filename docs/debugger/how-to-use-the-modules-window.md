---
title: Anzeigen von DLLs und ausführbare Dateien in das Fenster "Module" | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2018
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
ms.openlocfilehash: 4604932084289919a86ba09516b8d2c237f44cd9
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296267"
---
# <a name="view-dlls-and-executables-in-the-modules-window"></a>DLLs und ausführbare Dateien in das Fenster "Module" anzeigen
 
Während des Debuggens Visual Studio die **Module** Fenster listet auf und zeigt Informationen zu den DLLs und ausführbare Dateien (*.exe* Dateien) Ihrer app verwendet. 

> [!NOTE]
> Das Fenster "Module" ist nicht verfügbar, für das SQL-zu Skriptdebuggen. 
  
## <a name="use-the-modules-window"></a>Verwenden des Modulfensters

Wählen Sie zum Öffnen des Modulfensters während des Debuggens **Debuggen** > **Windows** > **Module**. 
  
In der Standardeinstellung die **Module** Fenster nach Modulen Ladereihenfolge sortiert. Wählen Sie den Header am oberen Rand der Spalte, um nach einer beliebigen Spalte im Fenster zu sortieren.  
  
## <a name="load-symbols"></a>Laden von Symbolen  

Die **Symbolstatus** -Spalte in der **Module** Fenster zeigt, welche Module Debugsymbole geladen. Wenn der Status **Laden von Symbolen wurde übersprungen,**, **nicht gefunden, oder öffnen Sie die PDB-Datei**, oder **laden, die von der Einstellung zum Einschließen/Ausschließen deaktiviert**, können Sie Symbole manuell laden. Weitere Informationen zum Laden und Verwenden der Symbole finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**So laden Sie Symbole manuell:**  

1. In der **Module** der rechten Maustaste auf das Modul für die Symbole noch nicht geladen. 
   
   - Wählen Sie **Symbolinformationen laden** Weitere Informationen dazu, warum die Symbole nicht geladen. 
   
   - Wählen Sie **Symbole laden** Symbole manuell geladen.  
   
1. Wenn die Symbole nicht geladen werden, wählen Sie **Symboleinstellungen** zu öffnen der **Optionen** Dialogfeld angeben, und das Laden der Speicherorte der Symbole zu ändern. 
   
   Sie können Symbole von den öffentlichen Microsoft-Symbolservern oder anderen Servern herunterladen, oder Laden von Symbolen aus einem Ordner auf Ihrem Computer. Weitere Informationen finden Sie unter [angeben der symboldateispeicherorte und des Ladeverhaltens](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).   

**So ändern Sie das Laden der Einstellungen für das Verhalten der Symbole auf:**  

1. In der **Module** Fenster mit der rechten Maustaste ein Modul.  
   
1. Wählen Sie **Symboleinstellungen**.  
  
1. Wählen Sie **alle Symbole laden**, oder wählen Sie die Module zum ein- oder ausschließen.  
  
1. Klicken Sie auf **OK**. Änderungen werden in der nächsten Debugsitzung wirksam.  
  
**So ändern Sie das Verhalten für ein bestimmtes Modul Laden der Symbole auf:**  

1.  In der **Module** Fenster mit der rechten Maustaste in des Moduls.  

1.  Klicken Sie im Kontextmenü, aktivieren oder deaktivieren Sie **immer laden automatisch**. Änderungen werden in der nächsten Debugsitzung wirksam.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterbrechen der Ausführung](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Anzeigen von Daten im debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)