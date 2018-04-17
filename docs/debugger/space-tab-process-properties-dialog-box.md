---
title: Registerkarte "Speicherplatz", Prozess-Eigenschaftendialogfeld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81d5329a694ba032a4dda280cac3a3200081aa77
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="space-tab-process-properties-dialog-box"></a>Registerkarte "Speicherplatz", Dialogfeld "Prozesseigenschaften"
Verwenden der **Speicherplatz** Tab, um den Adressbereich eines Prozesses zu untersuchen. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), Verschieben des Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **Speicherplatz** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Für als markierte Speicherplatz anzeigen**|Verwenden Sie im Listenfeld, um die Kategorie des Speicherplatzes (Image, zugeordnet, reserviert oder nicht zugewiesen) auszuwählen.|  
|**Ausführbare Bytes**|Für die ausgewählte Kategorie der alle Adressräume, den diesen Prozess verwendet wird. Ausführbare Speicher ist Speicher, die von Programmen ausgeführt werden können, aber nicht gelesen oder geschrieben werden kann.|  
|**EXEC-Read-Only-Bytes**|Für die ausgewählte Kategorie des Adressraums mit schreibgeschützten Eigenschaften, die diesen Prozess verwendet wird. EXEC-Read-only-Speicher ist Speicher, der sowohl ausgeführt als auch gelesen werden kann.|  
|**EXEC-Lese-/ Schreibzugriff Bytes**|Für die ausgewählte Kategorie des Adressraums mit Lese-/ Schreibzugriff-Eigenschaften, die diesen Prozess verwendet wird. EXEC-Lese-/ Schreibzugriff Speicher ist Speicher, die von Programmen ausgeführt sowie gelesen und geändert werden kann.|  
|**EXEC-geschriebene Kopie Bytes**|Für die ausgewählte Kategorie der alle Adressräume, der von Programmen ausgeführt sowie gelesen und geschrieben werden kann. Dieser Typ des Schutzes wird verwendet, wenn Arbeitsspeicher zwischen Prozessen gemeinsam genutzt werden muss. Wenn die Prozesse, die nur den Arbeitsspeicher lesen, wird den gleichen Speicher verwendet werden. Wenn ein Prozess Schreibzugriff wünscht, wird eine Kopie dieser Arbeitsspeicher für den Prozess vorgenommen werden.|  
|**Kein Zugriff Bytes**|Für die ausgewählte Kategorie der alle Adressräume, der verhindert, dass einen Prozess verwendet wird. Eine zugriffsverletzung wird generiert, wenn beim Schreiben oder lesen wird versucht.|  
|**Nur-Lese Bytes**|Für die ausgewählte Kategorie, die Summe der gesamten Adressraum, der sowohl ausgeführt als auch gelesen werden kann.|  
|**Lese-/ Schreibzugriff Bytes**|Für die ausgewählte Kategorie der alle Adressräume, der Lese- und Schreibzugriff zulässt.|  
|**Schreibkopie Bytes**|Für die ausgewählte Kategorie die Summe aus der Adressraum, können Arbeitsspeicher freigeben, zum Lesen, aber nicht zum Schreiben. Wenn Prozesse diesen Arbeitsspeicher lesen, können sie den gleichen Speicher gemeinsam verwenden. Allerdings möchte, dass ein Prozess Lese-/Schreibzugriff auf den freigegebenen Speicher haben, eine Kopie der, dass der Arbeitsspeicher für das Schreiben von erfolgt.|