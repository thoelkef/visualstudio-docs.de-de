---
title: Registerkarte ", Dialogfeld" Fenstereigenschaften "-Klasse | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaa02f87a0bb9737112121343226c2dc0e45937a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015471"
---
# <a name="class-tab-window-properties-dialog-box"></a>Registerkarte "Klasse", Dialogfeld "Fenstereigenschaften"
Verwenden der **Klasse** Tab, um Informationen für die Klasse des ausgewählten Fensters angezeigt. Zum Anzeigen der [Dialogfeld "Fenstereigenschaften"](../debugger/window-properties-dialog-box.md), Verschieben des Fokus auf die [Windows-Ansicht](../debugger/windows-view.md) Fenster. Wählen Sie einen beliebigen Knoten im Fenster in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Klasse** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Klassenname**|Der Name (oder die Ordnungszahl) der Fensterklasse.|  
|**Klassenstile**|Eine Kombination von Klasse-Stil-Codes.|  
|**Klassenbytes**|Anwendungsspezifische Daten, die dieser Fensterklasse zugeordnet.|  
|**Klassenatom**|Das Atom für die Klasse, die vom der **"registerClass"** aufrufen.|  
|**Instanzhandle**|Der Instanzhandle des Moduls, das die Klasse registriert. Instanzenhandles sind nicht eindeutig.|  
|**Fensterbytes**|Die Anzahl der zusätzlichen Bytes jedes Fenster dieser Klasse zugeordnet. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie im Listenfeld aus, um die Bytewerte in DWORD-Format anzuzeigen.|  
|**Fensterprozedur**|Die aktuelle Adresse des der **WndProc** -Funktion für Windows, die von dieser Klasse. Dies unterscheidet sich von **Fensterprozedur** auf die **allgemeine** Registerkarte, wenn das Fenster als Unterklasse definiert ist.|  
|**Menüname**|Der Name des im Hauptmenü, der mit Windows dieser Klasse ("none", wenn kein Menü vorhanden ist) zugeordnet ist.|  
|**Symbolhandle**|Das Handle für das Symbol, das Windows dieser Klasse ("none", wenn es kein Symbol angezeigt wird) zugeordnet ist.|  
|**Cursorhandle**|Das Handle für den Cursor, der mit Windows dieser Klasse ("none", wenn kein Cursor vorhanden ist) zugeordnet ist.|  
|**Hintergrundpinsel**|Das Handle für den Hintergrundpinsel an, der mit Windows, die von dieser Klasse oder eine der vordefinierten COLOR_ * Farben für das Zeichnen des Fensterhintergrunds ("none", wenn kein Pinsel) zugeordnet ist.|