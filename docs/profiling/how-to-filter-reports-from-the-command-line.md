---
title: "Vorgehensweise: Filtern von Berichten über die Befehlszeile | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 27309a459128e6ed9ebb17d295bc39c6c621dcd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Gewusst wie: Filtern von Berichten über die Befehlszeile
Mithilfe von Optionen für den Befehl **VSPerfReport** können Sie Berichte nach einem bestimmten Zeitsegment der Profilerstellungsdatei filtern oder die Daten auf einen oder mehr Prozesse oder Threads beschränken. Weitere Informationen zu diesem Befehl finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
|Optionen|description|  
|-------------|-----------------|  
|**StartTime:**[*Wert*]|Zeigt nur Daten an, die nach dem Wert erfasst werden (in Millisekunden)|  
|**EndTime:**[*Wert*]|Zeigt nur Daten an, die vor dem Wert erfasst werden (in Millisekunden)|  
|**FilterFile:** `VSPFFile`|Gibt den Speicherort einer Filterdatei an, die aus dem Visual Studio-Fenster **Leistungsbericht** generiert wurde|  
|**MsFilter:**[*Startzeit, Dauer*]|Zeigt nur Daten ab `StartTime` bis zur Länge von `Duration` (in Millisekunden) an|  
|**Process:**[*PID*]|Zeigt nur Daten aus dem angegebenen Prozess an|  
|**Thread:**[*Thread-ID*]|Zeigt nur Daten aus dem angegebenen Thread an|  
|**Thread:**[*Thread-ID, Prozess-ID*]|Zeigt nur Daten aus dem angegebenen Thread an, der dem angegebenen Prozess zugeordnet ist|