---
title: "Gewusst wie: Angeben der zu startenden Bin&#228;rdatei | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.itemlaunch"
helpviewer_keywords: 
  - "Profilerstellungstools, Starten"
  - "Leistungstools, Starten"
  - "Leistungssitzungen, Starten"
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Angeben der zu startenden Bin&#228;rdatei
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um Binärdateien, z DLLs ein Profil zu erstellen, müssen Sie Informationen im Dialogfeld **\<Ziel\>\-Eigenschaftenseiten** eingeben.  Diese Informationen geben dem DLL\-Projekt an, wo die aufrufende Anwendung zu finden ist.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### So geben Sie die zu startende ausführbare Datei an  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Zielbinärdatei, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf die Eigenschaften unter **Starten**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Projekteigenschaften überschreiben**.  
  
4.  Geben Sie im Textfeld **Zu startende ausführbare Datei** den Dateispeicherort an.  
  
5.  Geben Sie im Textfeld **Argumente** die Argumente an, die zum Starten der Anwendung erforderlich sind.  
  
6.  Geben Sie im Textfeld **Arbeitsverzeichnis** den Verzeichnisspeicherort an.  
  
7.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)