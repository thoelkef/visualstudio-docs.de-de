---
title: Registerkarte "Allgemein" Thread-Eigenschaften (Dialogfeld) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe6eb87418671b9b070aebaf60d1bb9c84b3623a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-thread-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Threadeigenschaften"
Verwenden Sie dieses Dialogfeld, um weitere Informationen zu einem bestimmten Thread finden. Um dieses Dialogfeld anzuzeigen, verschieben Sie den Fokus auf ein [Threadansicht](../debugger/threads-view.md) Fenster, oder öffnen Sie [Ansicht "Nachrichten"](../debugger/messages-view.md) und erweitern Sie eine Nachricht. Wählen Sie einen beliebigen Threadknoten in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die **Threadeigenschaften** Dialogfeld enthält einen Bereich der **allgemeine** Registerkarte. Die folgenden Einstellungen sind verfügbar:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Modulname**|Der Name des Moduls.|  
|**Thread-ID**|Die eindeutige ID dieses Threads. Beachten Sie, dass der Thread-IDs wiederverwendet werden. einen Thread identifizieren nur für die Lebensdauer des Threads.|  
|**Prozess-ID**|Die eindeutige ID dieses Prozesses. Prozess-ID-Nummern werden wiederverwendet, so dass sie nur für die Lebensdauer des entsprechenden Prozesses bestimmen eines Prozesses zu. Der Prozesstyp für das Objekt wird erstellt, wenn ein Programm ausgeführt wird. Alle Threads in einem Prozess gemeinsam denselben Adressraum nutzen und haben Zugriff auf die gleichen Daten. Wählen Sie diesen Wert zum Anzeigen der Eigenschaften der Prozess-ID.|  
|**Threadzustand**|Der aktuelle Zustand des Threads. Einen Prozessor verwendet ein Thread ausgeführt wird; ein Standby-Thread ist zu verwenden. Ein bereit Thread wartet auf einen Prozessor verwenden, da eine nicht frei ist. Ein Thread im Übergang wartet darauf, dass eine Ressource ausgeführt wie das Warten der Ausführungsstapel in vom Datenträger ausgelagert werden. Ein wartenden Thread ist den Prozessor nicht erforderlich, da sie für einen Peripheriegeräte Vorgang abgeschlossen oder Freiwerden einer Ressource wartet.|  
|**Grund für Warten**|Dies gilt nur, wenn der Thread in den Wartezustand ist. Ereignispaare werden verwendet, um die Kommunikation mit geschützten Subsysteme.|  
|**CPU-Zeit**|CPU-Gesamtzeit für die zu diesem Prozess und seine Threads. Gleich Benutzerzeit + privilegierte Zeit.|  
|**Benutzerzeit**|Die gesamte verstrichene Zeit, dass dieser Thread die Ausführung von Code im Benutzermodus benötigt wurde. Anwendungen werden im Benutzermodus, ausgeführt, ebenso Subsysteme wie die Fenstermanager und das Modul für Grafiken.|  
|**Privilegierte Zeit**|Die gesamte verstrichene Zeit, dass dieser Thread die Ausführung von Code im privilegierten Modus benötigt wurde. Wenn ein Windows-System-Dienst aufgerufen wird, wird der Dienst häufig im privilegierten Modus für den Zugriff auf Private Daten des Systems ausgeführt. Solche Daten aus Access von Threads im Benutzermodus ausgeführt geschützt. Aufrufe an das System können explizit oder implizit, z. B. wenn ein Seitenfehler oder eine Unterbrechung auftritt.|  
|**Verstrichene Zeit**|Die gesamte verstrichene Zeit (in Sekunden), die dieser Thread ausgeführt wurde.|  
|**Aktuelle Priorität**|Die aktuelle dynamische Priorität dieses Threads. Threads innerhalb eines Prozesses können auslösen und senken ihre eigenen Basispriorität relativ zum die Basispriorität des Prozesses.|  
|**Basis-Priorität**|Die aktuelle Basispriorität dieses Threads.|  
|**Startadresse**|Virtuelle Startadresse für diesen Thread.|  
|**PC-Benutzer**|Der Benutzerprogrammzähler für den Thread.|  
|**Kontextwechsel**|Die Anzahl der Wechsel von einem Thread zu einem anderen. Thread-Switches können innerhalb eines einzelnen Prozesses oder prozessübergreifend auftreten. Ein Threadswitch kann verursacht werden, von einem Thread in einem anderen Informationen oder von einem Thread präemptiv unterbrochen wird, wenn ein Thread mit höherer Priorität für die Ausführung bereit ist.|