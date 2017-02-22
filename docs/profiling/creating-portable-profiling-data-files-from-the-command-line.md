---
title: "Erstellen portabler Profilerstellungsdatendateien &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erstellen portabler Profilerstellungsdatendateien &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um die Freigabe der Profilerstellungsdaten zu vereinfachen, können Sie die Symbole für eine Profilerstellung mit dem Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) in die VSP\-Datei einbetten.  
  
 Sie können auch eine bereits analysierte Profilerstellungs\-Datendatei \(.vsps\) erstellen, die kleiner ist und schneller in der IDE geladen wird.  
  
> [!NOTE]
>  Stellen Sie sicher, dass die Symboldateien \(.pdb\) **VSPerfReport** zur Verfügung stehen.  Weitere Informationen finden Sie unter [Gewusst wie: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Informationen zum Pfad zu **VSReport** finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Die Profilerstellungsdaten in einer VSPS\-Datei können nicht gefiltert werden.  
  
### So betten Sie die Symbole für eine Profilerstellung in eine Profilerstellungs\-Datendatei \(.vsp\) ein  
  
-   Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein:  
  
     \<Datei\> **\/PackSymbols** Pfad **VSPerfReport \<**\>VSP  
  
     Standardmäßig erhält die VSPS\-Datei den Basisnamen der VSP\-Datei.  Mit der **Output**\-Option können Sie einen alternativen Namen angeben.  
  
### So erstellen Sie eine zusammenfassende Profilerstellungs\-Datendatei  
  
-   Geben Sie an einer Eingabeaufforderung den folgenden Befehl ein:  
  
     \<Datei\> **\/SummaryFile** \[**\/Output:**\<\]**VSPerfReport \<** VSP Dateiname \>Pfad\>  
  
     Standardmäßig erhält die VSPS\-Datei den Basisnamen der VSP\-Datei.  Mit der **Output**\-Option können Sie einen alternativen Namen angeben.