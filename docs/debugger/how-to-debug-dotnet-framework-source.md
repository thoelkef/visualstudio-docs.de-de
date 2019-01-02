---
title: 'Vorgehensweise: Debuggen von .NET Framework-Quelle | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a627c2f0880aee9906e3478b268d688c59b7d090
ms.sourcegitcommit: 6efb9378a82924cb133912d207c6da4bd5a0b9c2
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53443911"
---
# <a name="how-to-debug-net-framework-source"></a>Vorgehensweise: Debuggen einer .NET Framework-Quelle

Zum Debuggen von .NET Framework-Quellcodes ist Folgendes erforderlich:

- Aktivieren Sie .NET Framework-Quelle schrittweise.  
  
- Haben Sie Zugriff auf Debugsymbole für den Code ein. 
  
  Sie können auch sofort Debugsymbole herunterladen, oder legen Sie Optionen für das Herunterladen später noch mal. Wenn Sie keine Symbole sofort herunterladen, werden sie beim nächsten herunterladen, die Sie das Debuggen Ihrer app starten. Während des Debuggens können Sie auch die **Module** oder **Aufrufliste** Windows zu laden, und Laden von Symbolen.  
  
### <a name="to-enable-stepping-into-net-framework-source"></a>.NET Framework-Quellcodes-Quellcodes aktivieren 
  
1. Klicken Sie unter **Tools** (oder **Debuggen**) > **Optionen** > **Debuggen** > **Allgemein**Option **aktivieren Sie .NET Framework-Quelle schrittweise**.  
   
   - Wenn Sie Nur Mein Code aktiviert haben, wird Ihnen in einem Warndialogfeld mitgeteilt, dass Nur mein Code jetzt deaktiviert wird. Klicken Sie auf **OK**.  
   
   - Wenn Sie einen lokalen Symbolcache legen Sie keinen, besagt ein Warndialogfeld angezeigt, dass ein Symbol Standardcache festgelegt wurde. Klicken Sie auf **OK**.  
   
1. Wählen Sie **OK** schließen die **Optionen** Dialogfeld.
  
### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Festlegen oder Ändern der Speicherorte für Symboldateien-Quelle und des Ladeverhaltens

1. Wählen Sie die **Symbole** unter Kategorie **Tools** (oder **Debuggen**) > **Optionen** > **Debuggen**.  
  
1. Auf der **Symbole** Seite **Symboldateien (.pdb) Orte für Symboldateien**Option **Microsoft-Symbolserver** auf Access Symbole von den öffentlichen Microsoft-Symbolservern. Wählen Sie die Symbolleisten-Schaltflächen an andere Orte für Symboldateien hinzufügen und Ändern der Reihenfolge geladen. 
   
1. Um Ihre lokalen Symbolcache zu ändern, bearbeiten, oder navigieren Sie zu einem anderen Speicherort unter **Symbole in diesem Verzeichnis zwischenspeichern**.  
   
1. Wählen Sie zum Symbole sofort herunterladen **alle Symbole laden**. Diese Schaltfläche ist nur während des Debuggens verfügbar.  
   
   Wenn Sie keine Symbole jetzt herunterladen, müssen sie das nächste Mal heruntergeladen werden, die, das Sie das Debuggen starten.  
   
1. Wählen Sie **OK** schließen die **Optionen** Dialogfeld.  
  
### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>So laden Sie Symbole aus den Modulen oder die Aufrufliste Windows  
  
1. Öffnen Sie das Fenster während des Debuggens dazu **Debuggen** > **Windows** > **Module** (oder drücken Sie **Strg + Alt + U**) oder **Debuggen** > **Windows** > **Aufrufliste** (**Strg + Alt + C**). 
   
1. Mit der rechten Maustaste in ein Modul für die Symbole geladen wurden nicht. In der **Module** Fenster, Symbol Status geladen ist der **Symbolstatus** Spalte. In der **Aufrufliste** Fenster, Status ist der **Framestatus** Spalte und der Rahmen wird abgeblendet. 
   
   - Wählen Sie **Symbole laden** aus dem Menü zu suchen und Laden von Symboldateien aus einem Ordner auf Ihrem Computer. 
   
   - Wählen Sie **Symbolladeinformationen** den Speicherorten angezeigt, der Debugger nach Symbolen durchsucht.  
   
   - Wählen Sie **Symboleinstellungen** zum Öffnen der **Symbole** Seite. Auf der **Symbole** Seite **Symboldateien (.pdb) Orte für Symboldateien**Option **Microsoft-Symbolserver** auf Access Symbole von den öffentlichen Microsoft-Symbolservern. Wählen Sie die Symbolleisten-Schaltflächen an andere Orte für Symboldateien hinzufügen und Ändern der Reihenfolge geladen. Wählen Sie **OK** um das Dialogfeld zu schließen. 
  
### <a name="see-also"></a>Siehe auch  
 [Debugging managed code (Debuggen von verwaltetem Code)](../debugger/debugging-managed-code.md)   
 [Specify symbol (.pdb) and source files (Angeben von Symboldateien (PDB) und Quelldateien)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)