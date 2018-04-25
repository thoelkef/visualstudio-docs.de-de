---
title: Fenstereigenschaften (Dialogfeld) Registerkarte "-Klasse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4afce149a2124ba8caa827b73b258fb421792c13
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="class-tab-window-properties-dialog-box"></a>Registerkarte "Klasse", Dialogfeld "Fenstereigenschaften"
Verwenden der **Klasse** Registerkarte ", um Informationen für die Klasse für das ausgewählte Fenster anzuzeigen. Zum Anzeigen der [Fenstereigenschaften (Dialogfeld)](../debugger/window-properties-dialog-box.md), den Fokus auf die [Fensteransicht](../debugger/windows-view.md) Fenster. Wählen Sie einen beliebigen Knoten im Fenster in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **Klasse** Registerkarte:  
  
|Eintrag|Beschreibung|  
|-----------|-----------------|  
|**Klassenname**|Der Name (oder die Ordnungszahl) der Fensterklasse.|  
|**Klasse Stile**|Eine Kombination von Klassencodes-Stil.|  
|**Klasse Bytes**|Anwendungsspezifische Daten dieser Fensterklasse zugeordnet.|  
|**Klasse Atom**|Das Atom für die Klasse zurückgegebenes der **RegisterClass** aufrufen.|  
|**Instanzhandle**|Der Instanzhandle des Moduls, das die Klasse registriert. Instanzenhandles sind nicht eindeutig.|  
|**Fenster Bytes**|Die Anzahl der zusätzlichen Bytes jedes Fenster dieser Klasse zugeordnet. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie im Listenfeld aus, um die Bytewerte im DWORD-Format anzuzeigen.|  
|**Fensterprozedur**|Die aktuelle Adresse des dem **WndProc** Funktion für Windows von dieser Klasse. Dies unterscheidet sich von **Fensterprozedur** auf die **allgemeine** Registerkarte, wenn das Fenster als Unterklasse definiert ist.|  
|**Menünamen**|Der Name des Hauptmenüs, das Windows dieser Klasse ("none", wenn kein Menü vorhanden ist) zugeordnet ist.|  
|**Symbol "-Handle**|Das Handle für das Symbol, das Windows dieser Klasse ("none", wenn kein Symbol) zugeordnet ist.|  
|**Cursorhandle**|Das Handle für den Cursor, der mit Windows dieser Klasse ("none", wenn kein Cursor vorhanden ist) zugeordnet ist.|  
|**Hintergrund Pinsel**|Das Handle für den Hintergrundpinsel, der mit Windows für diese Klasse oder eine der vordefinierten COLOR_ * Farben für der Fenster Hintergrund ("none", wenn kein Pinsel vorhanden ist) zugeordnet ist.|