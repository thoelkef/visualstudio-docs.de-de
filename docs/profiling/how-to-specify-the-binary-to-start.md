---
title: "Vorgehensweise: Angeben der zu startenden Binärdatei | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5d17c59c44dc64b2e3fa3e53553a65ee9998b7ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-binary-to-start"></a>Gewusst wie: Angeben der zu startenden Binärdatei
Um ein Profil für Binärdateien zu erstellen, wie z.B. DLLs, müssen Sie Informationen im Dialogfeld  **\<Ziel> Eigenschaftenseiten** eingeben. Diese Informationen geben an, wo das DLL-Projekt die aufrufende Anwendung finden kann.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>So geben Sie die zu startende ausführbare Datei an  
  
1.  Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Zielbinärdatei und anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf die **Start**-Eigenschaften.  
  
3.  Wählen Sie das Kontrollkästchen **Projekteigenschaften überschreiben** aus.  
  
4.  Geben Sie m Textfeld **Zu startende ausführbare Datei** den Dateispeicherort an.  
  
5.  Geben Sie im **Argumente**-Textfeld Argumente an, die zum Starten der Anwendung erforderlich sind.  
  
6.  Geben Sie im **Arbeitsverzeichnis** den Speicherort für das Verzeichnis an.  
  
7.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)