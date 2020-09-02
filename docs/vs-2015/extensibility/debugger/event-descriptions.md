---
title: Ereignis Beschreibungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5aff88047d6b1f79544af927751d7a053eeda218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152821"
---
# <a name="event-descriptions"></a>Ereignisbeschreibungen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jeder Ereignistyp hat einen bestimmten Zweck.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Ereignisse und die Gründe für deren Verwendung  
  
|Ereignis|Beschreibung|  
|-----------|-----------------|  
|Dokument Ereignisse aktivieren|Tritt auf, wenn das Debug-Modul (de) möchte, dass die IDE öffnet oder ein Dokument in den Vordergrund bringt.|  
|Haltepunkt-oder breakpointfehlerereignisse|Wird gesendet, wenn ein Breakpoint gebunden ist oder wenn ein Haltepunkt nicht gebunden werden kann und ein Fehler zurückgegeben wird.|  
|Nicht gebundene Haltepunkt Ereignisse|Tritt auf, wenn ein gebundener Breakpoint die Bindung an Code aufhebt.|  
|Ereignisse können beendet werden.|Wird an die IDE gesendet, um zu bestimmen, ob der Benutzer an einem bestimmten Punkt im Code angehalten werden soll.|  
|Haltepunkt Ereignisse|Tritt auf, wenn ein Code-oder Daten Haltepunkt getroffen wird.|  
|Dokument Text Ereignisse|Tritt auf, wenn Text in einem Dokument geändert wird. Diese Ereignisse werden nicht durch die- `IDebugEventCallBack2::Event` Methode gesendet.|  
|Engine-Erstellungs Ereignisse|Wird gesendet, wenn eine Engine erstmalig erstellt wird.|  
|Einstiegspunkt Ereignisse|Wird gesendet, wenn das decodierende Programm seinen Initialisierungs Code ausgeführt hat und den ersten Benutzer Einstiegspunkt erreicht hat.|  
|Ausnahme Ereignisse|Wird gesendet, wenn ein ausgelaufendes Programm auf eine Ausnahme trifft.|  
|Ereignisse beim Abschluss der Ausdrucks Auswertung|Wird gesendet, wenn die asynchrone Ausdrucks Auswertung beendet ist.|  
|Symbol Ereignisse suchen|Wird gesendet, wenn der Benutzer den Benutzer zum Suchen von Symbolen für ein Modul auffordern muss.|  
|Ereignisse beim Laden vervollständigen|Wird nur gesendet, wenn die anfängliche Programm Last fertiggestellt ist und der erste Code im Programm ausgeführt wird.|  
|Nachrichtenereignisse|Wird gesendet, wenn Nachrichten an Benutzer gesendet werden.|  
|Modul Lade Ereignisse|Wird gesendet, wenn ein neues Modul geladen oder entladen wird.|  
|Ausgabe Zeichen folgen Ereignisse|Wird gesendet, wenn das Programm die Debugausgabe schreibt.|  
|Erstellen und zerstören von Ereignissen|Wird gesendet, um die Erstellung oder Zerstörung von Prozessen, Programmen, Eigenschaften, Sitzungen und Threads zu ankündigen, damit die Visual Studio-IDE den Zustand der Programme, die gedebuggt werden, nachverfolgen kann.|  
|Abgeschlossene Schritt Ereignisse|Wird gesendet, wenn ein Schritt beendet ist.|  
|Änderungs Ereignisse für Thread Name|Wird gesendet, wenn der Benutzer den Namen eines Threads ändert.|  
|Programmnamen-Änderungs Ereignisse|Wird gesendet, wenn der Benutzer den Namen eines Programms ändert.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
