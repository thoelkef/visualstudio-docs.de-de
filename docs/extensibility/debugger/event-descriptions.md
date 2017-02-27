---
title: "Sicherheitsereignisse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugereignisse [Debugging-SDK]"
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Sicherheitsereignisse
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Jeder Typ Ereignis verfügt über einen bestimmten Zweck.  
  
## Ereignisse und die Gründe für deren Verwendung  
  
|Ereignis|Beschreibung|  
|--------------|------------------|  
|Aktivieren Sie Dokumentereignisse|Wenden Sie sich ein, wenn das Debugmodul \(DE die IDE\) geöffnet oder ein Dokument in den Vordergrund bringen möchte.|  
|fehlerereignisse Haltepunkt oder gebundene Haltepunkt|Gesendet, wenn ein Haltepunkt gebunden ist, oder wenn ein Haltepunkt nicht gebunden werden kann und ein Fehler wird zurückgegeben.|  
|Ungebundene Ereignisse des Haltepunkts|Wenden Sie sich ein, wenn ein gebundener Haltepunkt im Code hebt.|  
|Kann Ereignissen beenden|Gesendet zur IDE, um zu bestimmen, ob der Benutzer an einem angegebenen Punkt im Code beendet werden soll.|  
|Haltepunkt Events|Wenden Sie sich ein, wenn ein Code oder ein Datenhaltepunkt erreicht wird.|  
|Dokumenttext Events|Wenden Sie sich auf, wenn Text in einem Dokument geändert wird.  Diese Ereignisse werden nicht durch die `IDebugEventCallBack2::Event`\-Methode gesendet.|  
|Erstellen von Modulen Ereignisse|Gesendet, wenn ein Modul zum ersten Mal erstellt wird.|  
|Einstiegspunkt Events|Gesendet, wenn das Programm, das gedebuggt wird, den Initialisierungscode ausgeführt und seinen ersten Einstiegspunkt für Benutzer erreicht hat.|  
|Ausnahmeereignisse|Gesendet, wenn ein Ausführen programm eine Ausnahme trifft.|  
|Vollständige Ereignisse der Ausdrucksauswertung|Gesendet, wenn die asynchrone Ausdrucksauswertung abgeschlossen ist.|  
|Ereignisse Symbol suchen|Gesendet, sobald der Benutzer DE angefordert werden müssen, Symbole für ein Modul zu suchen.|  
|Vollständige Ereignisse des Ladevorgangs|Gesendet nur dann, wenn die Initialladen abgeschlossen sind und der erste Code im Begriff, in das Programm ausgeführt wird.|  
|Ereignisse Nachrichten|Gesendet, wenn Nachrichten an den Benutzer gesendet werden.|  
|Modulladeereignisse|Gesendet, wenn ein neues Modul geladen oder entladen wird.|  
|Ausgabe von Zeichenfolgen|Gesendet, wenn das Programm Debugausgabe schreibt.|  
|Erstellen und zerstören Sie Ereignisse|Gesendet, um die Erstellung oder Zerstörung von Prozessen, Programme, Eigenschaften, Sitzungen und Threads sodass Visual Studio\-IDE kann anzukündigen den Zustand der Programme verfolgen, die gedebuggt werden.|  
|Vollständige Ereignisse des Schritts|Gesendet, wenn ein Schritt abgeschlossen ist.|  
|Name des Threads von Änderungen|Gesendet, wenn der Benutzer den Namen eines Threads ändert.|  
|Programmnamen von Änderungen|Gesendet, wenn der Benutzer den Namen eines Programms geändert wird.|  
  
## Siehe auch  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)