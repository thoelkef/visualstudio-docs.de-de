---
title: Registerkarte „Auslagerungsdatei“ und Dialogfeld „Prozesseigenschaften“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192718"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Registerkarte "Auslagerungsdatei", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Auslagerungsdatei**, um die Auslagerungsdatei eines Prozesses zu untersuchen. Verschieben Sie den Fokus der Ansicht auf das Fenster [Prozessansicht](../debugger/processes-view.md), um das [Dialogfeld „Prozesseigenschaften“](../debugger/process-properties-dialog-box.md) anzuzeigen. Klicken Sie zunächst auf einen beliebigen Prozessknoten in der Struktur und anschließend im Menü **Ansicht** auf **Eigenschaften**.  
  
 Auf der Registerkarte **Auslagerungsdatei** sind folgende Einstellungen verfügbar:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Bytes für Auslagerungsdatei**|Dies ist die aktuelle Anzahl der Seiten, die von diesem Prozess in der Auslagerungsdatei verwendet werden. In der Auslagerungsdatei werden Datenseiten gespeichert, die vom Prozess verwendet werden, aber nicht in anderen Dateien enthalten sind. Die Auslagerungsdatei wird von allen Prozessen verwendet, und der Mangel an Speicherplatz in der Auslagerungsdatei kann zu Fehlern führen, während andere Prozesse ausgeführt werden.|  
|**Max. Bytes für Auslagerungsdatei**|Dies ist die maximale Anzahl der Seiten, die von diesem Prozess in der Auslagerungsdatei verwendet wurden.|  
|**Seitenfehler**|Dies ist die Anzahl der Seitenfehler durch die in diesem Prozess ausgeführten Threads. Ein Seitenfehler tritt auf, wenn von einem Thread auf eine virtuelle Speicherseite verwiesen wird, die nicht auf dessen Arbeitsseite im Hauptspeicher enthalten ist. Die Seite wird daher nicht vom Datenträger abgerufen, wenn sie sich auf der Standbyliste und somit bereits im Hauptspeicher befindet oder wenn sie von einem anderen Prozess verwendet wird, für den die Seite freigegeben ist.|
