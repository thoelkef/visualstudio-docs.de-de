---
title: "Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f222856d16033cba5ae089c19081efeefe744aa5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Erstellen portabler Profilerstellungsdatendateien über die Befehlszeile
Um die Freigabe von Profilerstellungsdaten zu vereinfachen, können Sie das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) verwenden, um Symbole für eine Profilerstellungsausführung in die VSP-Datei einzubetten.  
  
 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (.vsps) erstellen, die kleiner ist und schneller in der IDE geladen wird.  
  
> [!NOTE]
>  Stellen Sie sicher, dass die Symboldateien (.pdb) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Die Profilerstellungsdaten in einer VSPS-Datei können nicht gefiltert werden.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (.vsp) für die Profilerstellungsausführung  
  
-   Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
     \<Pfad> **VSPerfReport \<**VSP-Datei> **/PackSymbols**  
  
     Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei  
  
-   Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
     \<Pfad> **VSPerfReport \<**VSP-Datei> **/SummaryFile** [**/Output:**\<Dateiname>]  
  
     Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.