---
title: 'Vorgehensweise: Angeben der zu startenden Binärdatei | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45b5e3ba98c526ffea1ab63f58ef9193a3eaae75
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759892"
---
# <a name="how-to-specify-the-binary-to-start"></a>Gewusst wie: Angeben der zu startenden Binärdatei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um ein Profil für Binärdateien zu erstellen, wie z.B. DLLs, müssen Sie Informationen im Dialogfeld  **\<Ziel> Eigenschaftenseiten** eingeben. Diese Informationen geben an, wo das DLL-Projekt die aufrufende Anwendung finden kann.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
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
