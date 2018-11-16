---
title: Anweisungszeigeransicht – Konfliktdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8945e405304d8080c9c4c53ccb0ac48d38d4c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737056"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Anweisungszeigeransicht – Konfliktdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Anweisungszeigeransicht (IPs-Ansicht) der Konfliktdaten führt Daten für die Assemblyanweisungen auf, die nicht während der Profilerstellung ausgeführt werden durften.  
  
 In der nachstehenden Tabelle werden die Werte der Spalten in der Anweisungszeigeransicht erklärt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Exklusive blockierte Zeit %**|Die blockierte Zeit in dieser Funktion|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der blockierten Zeit, während die Anweisung ausgeführt wurde|  
|**Exklusive Konflikte**|Die Anzahl der Konflikte, die aufgetreten sind, während die Anweisung ausgeführt wurde|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte bei der Profilerstellung, die aufgetreten sind, während die Anweisung ausgeführt wurde|  
|**Funktionsadresse**|Die Startspeicheradresse der Funktion in der geladenen Binärdatei|  
|**Funktionsname**|Der Name der Funktion, die die Anweisung enthält|  
|**Anweisungsadresse**|Die Speicheradresse der Anweisung in der geladenen Binärdatei|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält|  
|**Prozess-ID**|Die Prozess-ID (PID) des Profilerstellungsprozesses.|  
|**Prozessname**|Der Prozessname.|  
|**Quellanfangszeichen**|Der Offset des Zeichens der Quelldateizeile, an dem diese Anweisung beginnt|  
|**Quellendzeichen**|Der Offset des Zeichens der Quelldateizeile, an dem diese Anweisung endet|  
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält|  
|**Quellanfangszeile**|Die Zeilennummer in der Quelldatei, bei der diese Anweisung beginnt|  
|**Quellendzeile**|Die Zeilennummer in der Quelldatei, bei der diese Anweisung endet|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Anweisungszeigeransicht - Profiler-Konfliktdaten](../profiling/instruction-pointers-ips-view.md)   
 [Anweisungszeigeransicht - .NET-Speichersamplingdaten im Profiler](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view-sampling-data.md)



