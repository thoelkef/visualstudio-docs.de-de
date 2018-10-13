---
title: Registerkarte "Speicherplatz", im Dialogfeld "Eigenschaften" Process | Microsoft-Dokumentation
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
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03b73263f6db5e702a44b8854517ec5ee132b561
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259921"
---
# <a name="space-tab-process-properties-dialog-box"></a>Registerkarte "Speicherplatz", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **Speicherplatz** Tab, um den Adressbereich eines Prozesses untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Speicherplatz** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Anzeigen als gekennzeichnet Speicherplatz**|Verwenden Sie dieses Listenfelds können Sie, um die Kategorie des Speicherplatzes (Image, zugeordnet, reserviert oder Zuweisung) auswählen.|  
|**Ausführbare Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, den dieser Prozess verwendet wird. Ausführbare Speicher ist Speicher, die von Programmen ausgeführt werden können, aber nicht gelesen oder geschrieben werden kann.|  
|**EXEC-Read-Only-Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum mit schreibgeschützten Eigenschaften, die diesen Prozess verwendet wird. EXEC-Read-only-Speicher ist Speicher, die sowohl ausgeführt als auch gelesen werden kann.|  
|**EXEC-Lese-/ Schreibzugriff Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum mit Lese-/ Schreibzugriff-Eigenschaften, die diesen Prozess verwendet wird. EXEC-Lese-/ Schreibzugriff-Speicher ist Speicher, die Ausführung von Programmen als auch gelesen und geändert werden kann.|  
|**Kopieren – EXEC-geschriebene Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum an, der Ausführung von Programmen als auch gelesen und geschrieben werden kann. Diese Art von Schutz wird verwendet, wenn der Speicher muss zwischen Prozessen gemeinsam genutzt werden. Wenn die Prozesse, die nur den Arbeitsspeicher lesen, wird im gleichen Speicher verwendet werden. Wenn ein Prozess Schreibzugriff wünscht, wird eine Kopie dieser Arbeitsspeicher für den Prozess vorgenommen werden.|  
|**Kein Zugriff Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der verhindert, dass einen Prozess verwenden. Eine zugriffsverletzung wird generiert, wenn schreiben oder lesen wird versucht.|  
|**Nur-Lese Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der sowohl ausgeführt als auch gelesen werden kann.|  
|**Lese-/ Schreibzugriff Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der ermöglicht, lesen und schreiben.|  
|**Schreiben / kopieren-Bytes**|Für die ausgewählte Kategorie die Summe aus den Adressraum, ermöglicht Arbeitsspeicherfreigabe zum Lesen, aber nicht zum Schreiben. Wenn Prozesse diesen Arbeitsspeicher lesen, können sie den gleichen Arbeitsspeicher freigeben. Allerdings möchte, dass ein Prozess Lese-/Schreibzugriff auf diesen freigegebenen Speicher zugreifen, eine Kopie der, dass der Speicher für das Schreiben von erfolgt.|



