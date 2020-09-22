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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840924"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Erstellen portabler Profilerstellungsdatendateien über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die Freigabe von Profil Erstellungs Daten zu vereinfachen, können Sie das Befehlszeilen Tool [VSPerfReport](../profiling/vsperfreport.md) verwenden, um die Symbole für eine Profil Erstellungs Laufzeit in die VSP-Datei einzubetten.  
  
 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (.vsps) erstellen, die kleiner ist und schneller in der IDE geladen wird.  
  
> [!NOTE]
> Stellen Sie sicher, dass die Symbol Dateien (PDB-Dateien) für **VSPerfReport**verfügbar sind. Weitere Informationen finden Sie unter Gewusst [wie: Angeben von Symbol Dateispeicher Orten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
> Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu Befehlszeilentools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Die Profilerstellungsdaten in einer VSPS-Datei können nicht gefiltert werden.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (.vsp) für die Profilerstellungsausführung  
  
- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
   \<Path><strong>VSPerfReport \<</strong>VSP-Datei> **/PackSymbols**  
  
   Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei  
  
- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:  
  
   \<Path><strong>VSPerfReport \<</strong>VSP-Datei> **/SummaryFile** [ **/Output:** \<File Name>]  
  
   Standardmäßig ist der Name der Basisname der VSPS-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.
