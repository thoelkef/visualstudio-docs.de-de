---
title: Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77251c14cfdfb5829b16137f28148a0f0c8b9d8e
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268030"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile
Um die Freigabe von Profilerstellungsdaten zu vereinfachen, können Sie das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) verwenden, um Symbole für eine Profilerstellungsausführung in die VSP-Datei einzubetten.  
  
 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (.vsps) erstellen, die kleiner ist und schneller in der IDE geladen wird.  
  
> [!NOTE]
>  Stellen Sie sicher, dass die Symboldateien (.pdb) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Die Profilerstellungsdaten in einer VSPS-Datei können nicht gefiltert werden.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (.vsp) für die Profilerstellungsausführung  
  
-   Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
     \<Pfad> **VSPerfReport \<** VSP-Datei> **/PackSymbols**  
  
     Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei  
  
-   Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
     \<Pfad> **VSPerfReport \<** VSP-Datei> **/SummaryFile** [**/Output:**\<Dateiname>]  
  
     Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.