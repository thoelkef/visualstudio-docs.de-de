---
title: "Registerkarte &quot;Klasse&quot;, Dialogfeld &quot;Fenstereigenschaften&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenstereigenschaften (Dialogfeld), Registerkarte „Klasse“"
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Registerkarte &quot;Klasse&quot;, Dialogfeld &quot;Fenstereigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Klasse**, um Informationen zur Klasse des ausgewählten Fensters anzuzeigen.  Um das Dialogfeld [Fenstereigenschaften](../debugger/window-properties-dialog-box.md) anzuzeigen, verschieben Sie den Fokus auf das [Fensteransichtsfenster](../debugger/windows-view.md).  Wählen Sie in der Struktur einen Fensterknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Auf der Registerkarte **Klasse** sind die folgenden Einstellungen verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Klassenname**|Der Name \(oder die Ordnungszahl\) der Fensterklasse.|  
|**Klassenstile**|Eine Kombination von Klassenstilcodes.|  
|**Klassenbytes**|Anwendungsspezifische Daten, die dieser Fensterklasse zugeordnet sind.|  
|**Klassenatom**|Das Atom für die vom **RegisterClass**\-Aufruf zurückgegebene Klasse.|  
|**Instanzenhandle**|Das Instanzenhandle des Moduls, das die Klasse registriert hat.  Instanzenhandles sind nicht eindeutig.|  
|**Fensterbytes**|Die Anzahl von zusätzlichen Bytes, die den einzelnen Fenstern der Klasse zugeordnet sind.  Die Bedeutung dieser Bytes hängt von der Anwendung ab.  Erweitern Sie das Listenfeld, um die Bytewerte im DWORD\-Format anzuzeigen.|  
|**Fensterprozedur**|Die aktuelle Adresse der **WndProc**\-Funktion für Fenster dieser Klasse.  Diese unterscheidet sich von den Angaben in **Fensterprozedur** auf der Registerkarte **Allgemein**, wenn das Fenster als Unterklasse definiert ist.|  
|**Menüname**|Der Name des Hauptmenüs, das Fenstern der Klasse zugeordnet ist \("Keine", wenn kein Menü vorhanden ist\).|  
|**Symbolhandle**|Das Handle für das Symbol, das Fenstern der Klasse zugeordnet ist \("Keine", wenn kein Symbol vorhanden ist\).|  
|**Cursorhandle**|Das Handle für den Cursor, der Fenstern der Klasse zugeordnet ist \("Keine", wenn kein Cursor vorhanden ist\).|  
|**Hintergrundpinsel**|Das Handle für den Hintergrundpinsel, der Fenstern dieser Klasse zugeordnet ist, oder eine der vordefinierten COLOR\_\*\-Farben zum Zeichnen des Fensterhintergrunds \("Keine", wenn kein Pinsel vorhanden ist\).|