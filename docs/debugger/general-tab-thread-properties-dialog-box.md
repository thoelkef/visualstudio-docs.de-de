---
title: Registerkarte "Allgemein", Thread-Eigenschaftendialogfeld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df711f61500d241d9f5ec0234d4f9b29f525c4f5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013941"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Threadeigenschaften"
Verwenden Sie das Dialogfeld zu öffnen, um weitere Informationen zu einem bestimmten Thread. Um das Dialogfeld anzuzeigen, den Fokus auf ein [Ansicht "Threads"](../debugger/threads-view.md) Fenster, oder Sie öffnen [Meldungsansicht](../debugger/messages-view.md) und erweitern Sie eine Nachricht. Wählen Sie einen beliebigen Threadknoten in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die **Threadeigenschaften** Dialogfeld enthält einen einzigen Bereich, der **allgemeine** Registerkarte. Die folgenden Einstellungen sind verfügbar:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Modulname**|Der Name des Moduls.|  
|**Thread-ID**|Die eindeutige ID dieses Threads. Beachten Sie, dass Thread-ID-Nummern wiederverwendet werden. Identifizieren sie einen Thread, nur für die Lebensdauer des Threads.|  
|**Prozess-ID**|Die eindeutige ID dieses Prozesses. Prozess-ID-Nummern werden wiederverwendet, damit sie einen Prozess nur für die Lebensdauer des Prozesses identifizieren. Der Prozess-Objekttyp wird erstellt, wenn ein Programm ausgeführt wird. Alle Threads in einem Prozess gemeinsam nutzen denselben Adressraum und haben Zugriff auf die gleichen Daten. Wählen Sie diesen Wert zum Anzeigen der Eigenschaften die Prozess-ID.|  
|**Threadzustand**|Der aktuelle Zustand des Threads. Ein Thread ausgeführt wird, ist einen Prozessor verwenden; ein Standby-Thread ist zu verwenden. Ein bereit-Thread wartet auf einen Prozessor verwenden, da diese nicht kostenlos ist. Ein Thread im Übergang wartet darauf, dass eine Ressource ausgeführt wie z.B. das Warten der Ausführungsstapel von der Festplatte gelesen werden. Ein wartenden Thread ist den Prozessor nicht erforderlich, da sie eine Operation in der Peripherie oder Freiwerden einer Ressource wartet.|  
|**Warteursache**|Dies gilt nur, wenn der Thread im Wartezustand befindet. Ereignispaare werden verwendet, für die Kommunikation mit geschützten Subsystemen.|  
|**CPU-Zeit**|CPU-Gesamtzeit für diesen Prozess und seine Threads. Gleich Benutzerzeit + privilegierte Zeit.|  
|**Benutzerzeit**|Die insgesamt verstrichene Zeit, dass dieser Thread Code im Benutzermodus ausgeführt hat, hat. Anwendungen werden im Benutzermodus ausgeführt, wie Subsysteme wie die Fenstermanager und der Grafik-Engine.|  
|**Privilegierte Zeit**|Die insgesamt verstrichene Zeit, dass dieser Thread die Ausführung von Code im privilegierten Modus beansprucht hat. Wenn ein Windows-System-Dienst aufgerufen wird, wird der Dienst im privilegierten Modus für den Zugriff auf Systemdaten oft ausgeführt. Solche Daten werden von Threads im Benutzermodus ausgeführt vor Zugriff geschützt. Aufrufe an das System können explizit oder implizit, wie z. B. wenn ein Seitenfehler oder eine Unterbrechung auftritt.|  
|**Verstrichene Zeit**|Die gesamte verstrichene Zeit (in Sekunden) hat dieser Thread ausgeführt wurde.|  
|**Aktuelle Priorität**|Die aktuelle dynamische Priorität dieses Threads. Threads innerhalb eines Prozesses können ausgelöst und senken ihre eigenen Basispriorität Bezug auf die Basispriorität des Prozesses.|  
|**Basispriorität**|Die aktuelle Basispriorität des Threads.|  
|**Startadresse**|Virtuelle Startadresse für diesen Thread.|  
|**Benutzer-PC**|Der Benutzerprogrammzähler für den Thread.|  
|**Kontextwechsel**|Die Anzahl der Wechsel von einem Thread in einen anderen. Threadänderungen können entweder in einem einzelnen Prozess oder zwischen Prozessen auftreten. Ein Threadswitch kann verursacht werden, von einem Thread, der Informationen in einer anderen oder von einem Thread präemptiv unterbrochen wird, wenn ein Thread höherer Priorität ausgeführt wird.|