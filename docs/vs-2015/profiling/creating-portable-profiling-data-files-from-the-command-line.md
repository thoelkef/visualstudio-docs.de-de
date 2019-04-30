---
title: Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5d343392c9e554c5e51325964949cd3ea13237b8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434291"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Erstellen portabler Profilerstellungsdatendateien über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die Freigabe von Profilerstellungsdaten zu vereinfachen, können Sie das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) verwenden, um Symbole für eine Profilerstellungsausführung in die VSP-Datei einzubetten.  
  
 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (.vsps) erstellen, die kleiner ist und schneller in der IDE geladen wird.  
  
> [!NOTE]
> Stellen Sie sicher, dass die Symboldateien (.pdb) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Die Profilerstellungsdaten in einer VSPS-Datei können nicht gefiltert werden.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (.vsp) für die Profilerstellungsausführung  
  
- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
   \<Pfad> <strong>VSPerfReport \<</strong>VSP-Datei> **/PackSymbols**  
  
   Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei  
  
- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
   \<Pfad> <strong>VSPerfReport \<</strong>VSP-Datei> **/SummaryFile** [**/Output:**\<Dateiname>]  
  
   Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.
