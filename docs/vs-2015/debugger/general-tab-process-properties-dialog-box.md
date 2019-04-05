---
title: Registerkarte "Allgemein", verarbeiten Sie im Dialogfeld Eigenschaften von | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9256ca4141e9e4ec9e5ae218f1e5a11bf2fa5362
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960405"
---
# <a name="general-tab-process-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Prozesseigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **allgemeine** Tab, um weitere Informationen zu einem bestimmten Prozess. Zum Anzeigen der [verarbeiten Eigenschaften (Dialogfeld)](../debugger/process-properties-dialog-box.md), verschieben Sie den Fokus auf ein [Prozessansicht](../debugger/processes-view.md) Fenster. Wählen Sie in der Struktur einen Prozessknoten aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **allgemeine** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Modulname**|Der Name des Moduls.|  
|**Prozess-ID**|Die eindeutige ID dieses Prozesses. Prozess-ID-Nummern werden wiederverwendet, damit sie einen Prozess nur für die Lebensdauer des Prozesses identifizieren. Der Prozess-Objekttyp wird erstellt, wenn ein Programm ausgeführt wird. Alle Threads in einem Prozess gemeinsam nutzen denselben Adressraum und haben Zugriff auf die gleichen Daten.|  
|**Basispriorität**|Die aktuelle Basispriorität dieses Prozesses. Threads innerhalb eines Prozesses können ausgelöst und senken ihre eigenen Basispriorität Bezug auf die Basispriorität des Prozesses.|  
|**Threads**|Die Anzahl der Threads, die derzeit in diesem Prozess aktiv.|  
|**CPU-Zeit**|CPU-Gesamtzeit für diesen Prozess und seine Threads. Gleich Benutzerzeit plus privilegierte Zeit.|  
|**Benutzerzeit**|Die kumulierte verstrichene Zeit, die die Threads dieses Prozesses nicht im Leerlauf in Threads Ausführung von Code im Benutzermodus benötigt haben. Anwendungen werden im Benutzermodus ausgeführt, wie Subsysteme wie z. B. der Fenster-Manager und der Grafik-Engine.|  
|**Privilegierte Zeit**|Die insgesamt verstrichene Zeit wurde im privilegierten Modus nicht im Leerlauf in Threads dieses Prozesses ausgeführt wurde. Führen Sie die Dienstebene, die Führungskräfte-Routinen und auch der Kernel im privilegierten Modus. Gerätetreiber für die meisten Geräte als Grafikkarten und Drucker werden auch im privilegierten Modus ausgeführt. Einige Aufgaben, die Windows für Ihre Anwendung möglicherweise in anderen Prozessen Subsystems neben privilegierte Zeit angezeigt.|  
|**Verstrichene Zeit**|Die insgesamt verstrichene Zeit, die diesen Prozess ausgeführt wurde.|
