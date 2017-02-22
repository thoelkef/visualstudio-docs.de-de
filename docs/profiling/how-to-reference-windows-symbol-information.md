---
title: "Gewusst wie: Verweisen auf Windows-Symbolinformationen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Symbolserver"
  - "Server, Symbolserver"
  - "Profilerstellungstools, Symbolserver"
  - "Symbolserver"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verweisen auf Windows-Symbolinformationen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Visual Studio\-Profilerstellungstools verwenden Symboldateien \(.pdb\), um symbolische Namen wie Funktionsnamen in den B aufzulösen.  Sie können diese Schritte ausführen, um die korrekten PDB\-Dateien für die Windows\-Version auf dem lokalen Computer automatisch herunterzuladen und zu aktualisieren.  
  
> [!NOTE]
>  Diese Einstellung wirkt sich nicht auf vorhandene Berichte aus.  Nur Berichte, die nach Angabe des Symbolservers erstellt werden, weisen Symbolinformationen auf.  
  
 Weitere Informationen finden Sie unter [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### So verwenden Sie den Symbolserver von Microsoft  
  
1.  Erstellen Sie einen Ordner für die Symboldateiinformationen, z. B. C:\\SymbolCache.  
  
2.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
3.  Erweitern Sie die Struktur **Debuggen**, und klicken Sie dann auf **Symbole**.  
  
4.  Wählen Sie im **Orte für Symboldateien \(.pdb\)Microsoft\-Symbolserver** aus  
  
5.  Geben Sie unter **Symbole vom Symbolserver in diesem Verzeichnis zwischenspeichern** den Pfad des in Schritt 1 erstellten Ordners ein, z. B.:  
  
     C:\\SymbolCache  
  
     Sie können auf die Schaltfläche mit den Auslassungspunkten \(**...**\) klicken und ein Verzeichnis aus dem Dialogfeld **Ordner suchen** auswählen.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Gewusst wie: Serialisieren von Symbolinformationen](../profiling/how-to-serialize-symbol-information.md)