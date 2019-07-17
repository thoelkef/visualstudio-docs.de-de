---
title: Registerkarte "Allgemein", Dialogfeld "Fenstereigenschaften" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8733ef63a60baa1b268c42c8780cdf80f2674b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159959"
---
# <a name="general-tab-window-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Fenstereigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **allgemeine** Tab, um Informationen über das ausgewählte Fenster anzuzeigen. Zum Anzeigen der [Dialogfeld "Fenstereigenschaften"](../debugger/window-properties-dialog-box.md), Verschieben des Fokus auf die [Windows-Ansicht](../debugger/windows-view.md) Fenster. Wählen Sie einen beliebigen Knoten im Fenster in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **allgemeine** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Fensterbeschriftung**|Der Text in die fensterbeschriftung oder Text in einem Fenster enthalten sind, wenn es sich um ein Steuerelement ist.|  
|**Fensterhandle**|Die eindeutige ID dieses Fensters. Die Nummern der Ziehpunkte Fenster werden wiederverwendet. Identifizieren sie ein Fenster, nur für die Lebensdauer dieses Fensters.|  
|**Fensterprozedur**|Die virtuelle Adresse der Fensterprozedurfunktion für dieses Fenster. Dieses Feld zeigt auch, ob dieses Fenster ein Unicode-Fenster ist, und gibt an, ob sie als Unterklasse definiert ist.|  
|**Rechteck**|Das umschließende Rechteck für das Fenster. Die Größe des Rechtecks wird ebenfalls angezeigt. Einheiten sind Pixel in Bildschirmkoordinaten.|  
|**Wiederherg. Rechteck**|Das umschließende Rechteck für das wiederhergestellte Fenster. Die Größe des Rechtecks wird ebenfalls angezeigt. Wiederhergestellte Rect variiert zwischen Rechteck nur, wenn das Fenster maximiert oder minimiert wird. Einheiten sind Pixel in Bildschirmkoordinaten.|  
|**Clientrechteck**|Das umschließende Rechteck für den Clientbereich des Fensters. Die Größe des Rechtecks wird ebenfalls angezeigt. Einheiten sind relativ zur linken oberen Ecke des Fensterclientbereichs Pixel.|  
|**Instanzhandle**|Der Instanzhandle, der Anwendung. Instanzenhandles sind nicht eindeutig.|  
|**Steuerelement-ID oder Menühandle**|Wenn das angezeigte Fenster ein untergeordnetes Fenster ist, wird die Steuerelement-ID-Bezeichnung angezeigt. Steuerelement-ID ist eine ganze Zahl, die diesem untergeordneten Fenster des Steuerelement-ID identifiziert. Wenn das angezeigte Fenster nicht über ein untergeordnetes Fenster ist, ist die Menühandle Bezeichnung angezeigt. Menühandle ist eine ganze Zahl, die das Handle des Menüs, die diesem Fenster zugeordnete identifiziert.|  
|**Benutzerdaten**|Anwendungsspezifische Daten, die auf diese Fensterstruktur verbunden ist.|  
|**Fensterbytes**|Die Anzahl der in diesem Fenster zugeordneten zusätzlichen Bytes. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie im Listenfeld aus, um die Bytewerte in DWORD-Format anzuzeigen.|
