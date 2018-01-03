---
title: 'Vorgehensweise: Verweisen auf Windows-Symbolinformationen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6578a6fe623afe8ceb20f9db32e7fa005f06618c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-reference-windows-symbol-information"></a>Gewusst wie: Verweisen auf Windows-Symbolinformationen
Der Visual Studio-Profilerstellungstools verwenden Symboldateien (.pdb), um symbolische Namen wie Funktionsnamen in Programmbinärdateien aufzulösen. Sie können diese Schritte befolgen, um automatisch die richtigen PDB-Dateien für die Windows-Version auf dem lokalen Computer herunterzuladen und zu aktualisieren.  
  
> [!NOTE]
>  Diese Einstellung wirkt sich nicht auf vorhandene Berichte aus. Nur Berichte, die nach Angabe des Symbolservers erstellt wurden, werden die Symbolinformationen haben.  
  
 Weitere Informationen finden Sie unter [Angeben von Symbol (.pdb)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>So verwenden Sie den Microsoft-Symbolserver  
  
1.  Erstellen Sie einen Ordner, um die Symboldateiinformationen aufzubewahren, wie z.B. C:\SymbolCache.  
  
2.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
3.  Erweitern Sie die Struktur **Debuggen**, und klicken Sie anschließend auf **Symbole**.  
  
4.  Wählen Sie in **Speicherort für Symboldateien (.pdb)** **Microsoft-Symbolserver** aus  
  
5.  Geben Sie in **Symbole vom Symbolserver zwischenspeichern** den Ordnerpfad ein, der in Schritt 1 erstellt wurde. Beispiel:  
  
     **C:\SymbolCache**  
  
     Sie können auch die Schaltfläche mit den Auslassungszeichen (**...**) anklicken und anschließend ein Verzeichnis vom Dialogfeld **Nach Ordner suchen** auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Vorgehensweise: Serialisieren von Symbolinformationen](../profiling/how-to-serialize-symbol-information.md)