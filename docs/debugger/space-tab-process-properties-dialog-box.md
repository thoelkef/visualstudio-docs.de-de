---
title: Registerkarte "Speicherplatz", im Dialogfeld "Eigenschaften" Process | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9cc3489cd07576521356a40c9d4abd42507aee9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853254"
---
# <a name="space-tab-process-properties-dialog-box"></a>Registerkarte "Speicherplatz", Dialogfeld "Prozesseigenschaften"
Verwenden der **Speicherplatz** Tab, um den Adressbereich eines Prozesses untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Speicherplatz** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Anzeigen, wenn markiert als**|Verwenden Sie dieses Listenfelds können Sie, um die Kategorie des Speicherplatzes (Image, zugeordnet, reserviert oder Zuweisung) auswählen.|  
|**Ausführbare Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, den dieser Prozess verwendet wird. Ausführbare Speicher ist Speicher, die von Programmen ausgeführt werden können, aber nicht gelesen oder geschrieben werden kann.|  
|**Ausführb. Bytes (schreibgeschützt)**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum mit schreibgeschützten Eigenschaften, die diesen Prozess verwendet wird. EXEC-Read-only-Speicher ist Speicher, die sowohl ausgeführt als auch gelesen werden kann.|  
|**Ausführb. Bytes (lesen/schreiben)**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum mit Lese-/ Schreibzugriff-Eigenschaften, die diesen Prozess verwendet wird. EXEC-Lese-/ Schreibzugriff-Speicher ist Speicher, die Ausführung von Programmen als auch gelesen und geändert werden kann.|  
|**Kopieren – EXEC-geschriebene Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum an, der Ausführung von Programmen als auch gelesen und geschrieben werden kann. Diese Art von Schutz wird verwendet, wenn der Speicher muss zwischen Prozessen gemeinsam genutzt werden. Wenn die Prozesse, die nur den Arbeitsspeicher lesen, wird im gleichen Speicher verwendet werden. Wenn ein Prozess Schreibzugriff wünscht, wird eine Kopie dieser Arbeitsspeicher für den Prozess vorgenommen werden.|  
|**Bytes (kein Zugriff)**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der verhindert, dass einen Prozess verwenden. Eine zugriffsverletzung wird generiert, wenn schreiben oder lesen wird versucht.|  
|**Bytes (schreibgeschützt)**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der sowohl ausgeführt als auch gelesen werden kann.|  
|**Bytes (lesen/schreiben)**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der ermöglicht, lesen und schreiben.|  
|**Bytes (schreiben/kopieren)**|Für die ausgewählte Kategorie die Summe aus den Adressraum, ermöglicht Arbeitsspeicherfreigabe zum Lesen, aber nicht zum Schreiben. Wenn Prozesse diesen Arbeitsspeicher lesen, können sie den gleichen Arbeitsspeicher freigeben. Allerdings möchte, dass ein Prozess Lese-/Schreibzugriff auf diesen freigegebenen Speicher zugreifen, eine Kopie der, dass der Speicher für das Schreiben von erfolgt.|