---
title: Registerkarte "Allgemein", Fenstereigenschaften (Dialogfeld) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f762d935edab5720ccd9add155dac3d0e5f2f186
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="general-tab-window-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Fenstereigenschaften"
Verwenden der **allgemeine** Registerkarte ", um Informationen über das ausgewählte Fenster anzuzeigen. Zum Anzeigen der [Fenstereigenschaften (Dialogfeld)](../debugger/window-properties-dialog-box.md), den Fokus auf die [Fensteransicht](../debugger/windows-view.md) Fenster. Wählen Sie einen beliebigen Knoten im Fenster in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **allgemeine** Registerkarte:  
  
|Eintrag|Beschreibung|  
|-----------|-----------------|  
|**Fenstertitel**|Der Text in die fensterbeschriftung, oder in einem Fenster enthalten sind, wenn es sich um ein Steuerelement handelt.|  
|**Das Fensterhandle**|Die eindeutige ID dieses Fensters. Fenster Nummern werden wiederverwendet. Identifizieren ein Fensters nur für die Lebensdauer des Fensters.|  
|**Fensterprozedur**|Die virtuelle Adresse der Fensterprozedurfunktion für dieses Fenster. Dieses Feld zeigt auch an, ob dieses Fenster ein Unicode-Fenster ist, und gibt an, ob es als Unterklasse definiert ist.|  
|**Rechteck**|Das umschließende Rechteck für das Fenster. Die Größe des Rechtecks wird ebenfalls angezeigt. Einheiten werden Pixel in Bildschirmkoordinaten.|  
|**Wiederhergestellte Rect**|Das umschließende Rechteck für das wiederhergestellte Fenster. Die Größe des Rechtecks wird ebenfalls angezeigt. Wiederhergestellte Rect datenträgeren Rechteck aus, nur, wenn das Fenster maximiert oder minimiert wird. Einheiten werden Pixel in Bildschirmkoordinaten.|  
|**Clientrechteck**|Das umschließende Rechteck für den Clientbereich des Fensters. Die Größe des Rechtecks wird ebenfalls angezeigt. Zeiten werden in Pixel relativ zur oberen linken Ecke des Fensterclientbereichs.|  
|**Instanzhandle**|Der Instanzhandle der Anwendung. Instanzenhandles sind nicht eindeutig.|  
|**Steuerelement-ID oder im Menü-Handle**|Wenn das angezeigte Fenster ein untergeordnetes Fenster ist, wird die Steuerelement-ID-Bezeichnung angezeigt. Steuerelement-ID ist eine ganze Zahl, die identifiziert dieses untergeordneten Fenster Steuerelement-ID. Wenn das angezeigte Fenster nicht um ein untergeordnetes Fenster ist, wird die Bezeichnung verarbeiten im Menü angezeigt. Menü-Handle ist eine ganze Zahl, die das Handle des Menüs, die diesem Fenster zugeordneten identifiziert.|  
|**Benutzerdaten**|Anwendungsspezifische Daten, die diese Fensterstruktur angefügt ist.|  
|**Fenster Bytes**|Die Anzahl der in diesem Fenster zugeordneten zusätzlichen Bytes. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie im Listenfeld aus, um die Bytewerte im DWORD-Format anzuzeigen.|