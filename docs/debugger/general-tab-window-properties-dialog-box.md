---
title: "Registerkarte &quot;Allgemein&quot;, Dialogfeld &quot;Fenstereigenschaften&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fenstereigenschaften (Dialogfeld), Registerkarte „Allgemein“"
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Registerkarte &quot;Allgemein&quot;, Dialogfeld &quot;Fenstereigenschaften&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Allgemein**, um Informationen zum ausgewählten Fenster anzuzeigen.  Um das Dialogfeld [Fenstereigenschaften](../debugger/window-properties-dialog-box.md) anzuzeigen, verschieben Sie den Fokus auf das [Fensteransichtsfenster](../debugger/windows-view.md).  Wählen Sie in der Struktur einen Fensterknoten und dann **Eigenschaften** im Menü **Ansicht** aus.  
  
 Auf der Registerkarte **Allgemein** sind die folgenden Einstellungen verfügbar:  
  
|Eintrag|Beschreibung|  
|-------------|------------------|  
|**Fensterbeschriftung**|Der Text der Fensterbeschriftung oder Text in einem Fenster, wenn es sich um ein Steuerelement handelt.|  
|**Fensterhandle**|Die eindeutige ID des Fensters.  Fensterhandlenummern werden wiederverwendet. Sie identifizieren ein Fenster nur während dessen Lebensdauer.|  
|**Fensterprozedur**|Die virtuelle Adresse der Fensterprozedurfunktion für dieses Fenster.  Dieses Feld gibt auch an, ob das Fenster ein Unicode\-Fenster ist und ob es als Unterklasse definiert ist.|  
|**Rechteck**|Das umschließende Rechteck für das Fenster.  Die Größe des Rechtecks wird ebenfalls angezeigt.  Die Einheiten sind Pixel in Bildschirmkoordinaten.|  
|**Wiederherg. Rechteck**|Das umschließende Rechteck für das wiederhergestellte Fenster.  Die Größe des Rechtecks wird ebenfalls angezeigt.  "Wiederherg. Rechteck" unterscheidet sich nur von "Rechteck", wenn das Fenster maximiert oder minimiert wurde.  Die Einheiten sind Pixel in Bildschirmkoordinaten.|  
|**Clientrechteck**|Das umschließende Rechteck für den Fensterclientbereich.  Die Größe des Rechtecks wird ebenfalls angezeigt.  Die Einheiten sind Pixel relativ zur linken oberen Ecke des Fensterclientbereichs.|  
|**Instanzenhandle**|Das Instanzenhandle der Anwendung.  Instanzenhandles sind nicht eindeutig.|  
|**"Steuerelement\-ID" oder "Menühandle"**|Wenn das angezeigte Fenster ein untergeordnetes Fenster ist, wird die Bezeichnung "Steuerelement\-ID" angezeigt.  "Steuerelement\-ID" ist eine ganze Zahl, die die Steuerelement\-ID des untergeordneten Fensters angibt.  Wenn das angezeigte Fenster kein untergeordnetes Fenster ist, wird die Bezeichnung "Menühandle" angezeigt.  "Menühandle" ist eine ganze Zahl, die das Handle des diesem Fenster zugeordneten Menüs angibt.|  
|**Benutzerdaten**|Anwendungsspezifische Daten, die dieser Fensterstruktur zugeordnet sind.|  
|**Fensterbytes**|Die Anzahl von zusätzlichen Bytes, die diesem Fenster zugeordnet sind.  Die Bedeutung dieser Bytes hängt von der Anwendung ab.  Erweitern Sie das Listenfeld, um die Bytewerte im DWORD\-Format anzuzeigen.|