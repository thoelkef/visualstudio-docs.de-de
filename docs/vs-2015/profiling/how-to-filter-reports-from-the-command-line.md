---
title: 'Vorgehensweise: Filtern von Berichten über die Befehlszeile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146005"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Gewusst wie: Filtern von Berichten über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe von Optionen für den Befehl **VSPerfReport** können Sie Berichte nach einem bestimmten Zeitsegment der Profilerstellungsdatei filtern oder die Daten auf einen oder mehr Prozesse oder Threads beschränken. Weitere Informationen zu diesem Befehl finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
|Optionen|Beschreibung|  
|-------------|-----------------|  
|**StartTime:** [*Wert*]|Zeigt nur Daten an, die nach dem Wert erfasst werden (in Millisekunden)|  
|**EndTime:** [*Wert*]|Zeigt nur Daten an, die vor dem Wert erfasst werden (in Millisekunden)|  
|**FilterFile:** `VSPFFile`|Gibt den Speicherort einer Filterdatei an, die aus dem Visual Studio-Fenster **Leistungsbericht** generiert wurde|  
|**MsFilter:** [*Startzeit, Dauer*]|Zeigt nur Daten ab `StartTime` bis zur Länge von `Duration` (in Millisekunden) an|  
|**Process:** [*PID*]|Zeigt nur Daten aus dem angegebenen Prozess an|  
|**Thread:** [*Thread-ID*]|Zeigt nur Daten aus dem angegebenen Thread an|  
|**Thread:** [*Thread-ID, Prozess-ID*]|Zeigt nur Daten aus dem angegebenen Thread an, der dem angegebenen Prozess zugeordnet ist|
