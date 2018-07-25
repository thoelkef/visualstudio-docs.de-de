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
ms.openlocfilehash: 25f2faf1be7f2e8ff5c96eca16ef2de9be2514db
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815840"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile
Sie können das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) zum Einbetten der Symbole für eine Profilerstellungsausführung in die *VSP*-Datei verwenden, um die Freigabe der Profilerstellungsdaten zu vereinfachen.  
  
 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (*VSPS*) erstellen, die kleiner ist und schneller in der IDE geladen wird.  
  
> [!NOTE]
>  Stellen Sie sicher, dass die Symboldateien (*PDB*) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Die Profilerstellungsdaten in einer *VSPS*-Datei können nicht gefiltert werden.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (*VSP*) für die Profilerstellungsausführung  
  
-   Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
     \<Pfad> **VSPerfReport \<** VSP-Datei> **/PackSymbols**  
  
     Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei  
  
-   Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
     \<Pfad> **VSPerfReport \<** VSP-Datei> **/SummaryFile** [**/Output:**\<Dateiname>]  
  
     Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.