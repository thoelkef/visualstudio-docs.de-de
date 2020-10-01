---
title: 'Profilerstellung über die Befehlszeile: Erstellen von portierbaren Datendateien'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0584cd2a476a7552beec483dd72ad1e957800ec
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808837"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile
Sie können das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) zum Einbetten der Symbole für eine Profilerstellungsausführung in die *VSP*-Datei verwenden, um die Freigabe der Profilerstellungsdaten zu vereinfachen.

 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (*VSPS*) erstellen, die kleiner ist und schneller in der IDE geladen wird.

> [!NOTE]
> Stellen Sie sicher, dass die Symboldateien (*PDB*) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Die Profilerstellungsdaten in einer *VSPS*-Datei können nicht gefiltert werden.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (*VSP*) für die Profilerstellungsausführung

- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   \<Path><strong>VSPerfReport \<</strong>VSP-Datei> **/PackSymbols**

   Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.

### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei

- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   \<Path><strong>VSPerfReport \<</strong>VSP-Datei> **/SummaryFile** [ **/Output:** \<File Name>]

   Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.
