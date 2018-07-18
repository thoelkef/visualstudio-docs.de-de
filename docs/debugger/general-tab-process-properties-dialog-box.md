---
title: Registerkarte "Allgemein", verarbeiten, im Dialogfeld Eigenschaften | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dcefc8be643c74349102261725c4879c0e161cd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471699"
---
# <a name="general-tab-process-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Prozesseigenschaften"
Verwenden der **allgemeine** Tab, um weitere Informationen über einen bestimmten Prozess zu erhalten. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), Verschieben des Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **allgemeine** Registerkarte:  
  
|Eintrag|Beschreibung|  
|-----------|-----------------|  
|**Modulname**|Der Name des Moduls.|  
|**Prozess-ID**|Die eindeutige ID dieses Prozesses. Prozess-ID-Nummern werden wiederverwendet, so dass sie nur für die Lebensdauer des entsprechenden Prozesses bestimmen eines Prozesses zu. Der Prozesstyp für das Objekt wird erstellt, wenn ein Programm ausgeführt wird. Alle Threads in einem Prozess gemeinsam denselben Adressraum nutzen und haben Zugriff auf die gleichen Daten.|  
|**Basispriorität**|Die aktuelle Basispriorität dieses Prozesses. Threads innerhalb eines Prozesses können auslösen und senken ihre eigenen Basispriorität relativ zur Basispriorität des Prozesses.|  
|**Threads**|Die Anzahl der Threads, die in diesem Prozess aktiv sind.|  
|**CPU-Zeit**|CPU-Gesamtzeit für die zu diesem Prozess und seine Threads. Gleich Benutzerzeit plus privilegierte Zeit.|  
|**Benutzerzeit**|Die kumulierte verstrichene Zeit, die die Threads dieses Prozesses Ausführungscode in nicht im Leerlauf befindlichen Threads im Benutzermodus benötigt haben. Anwendungen werden im Benutzermodus, ausgeführt, ebenso Subsysteme, z. B. der Fenstermanager und das Modul für Grafiken.|  
|**Privilegierte Zeit**|Die insgesamt verstrichene Zeit hat im privilegierten Modus in nicht im Leerlauf befindliche Threads dieser Prozess ausgeführt wurde. Die Dienstebene, die Executive-Routinen und der Kernel werden im privilegierten Modus ausgeführt. Gerätetreiber für die meisten Geräte als Grafikkarten und Drucker werden auch im privilegierten Modus ausgeführt. In anderen Vorgängen Subsystem neben privilegierte Zeit möglicherweise einige Arbeit, die Windows für Ihre Anwendung nicht angezeigt.|  
|**Verstrichene Zeit**|Die gesamte Zeitdauer, die dieser Prozess ausgeführt wurde.|