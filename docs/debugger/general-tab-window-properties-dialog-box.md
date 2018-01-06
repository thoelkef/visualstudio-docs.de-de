---
title: Registerkarte "Allgemein", Fenstereigenschaften (Dialogfeld) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5aea8d5eb998280d6602f4ea28eb0b52d5f86da3
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2018
---
# <a name="general-tab-window-properties-dialog-box"></a>Registerkarte "Allgemein", Dialogfeld "Fenstereigenschaften"
Verwenden der **allgemeine** Registerkarte ", um Informationen über das ausgewählte Fenster anzuzeigen. Zum Anzeigen der [Fenstereigenschaften (Dialogfeld)](../debugger/window-properties-dialog-box.md), den Fokus auf die [Fensteransicht](../debugger/windows-view.md) Fenster. Wählen Sie einen beliebigen Knoten im Fenster in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **allgemeine** Registerkarte:  
  
|Eingabe|Beschreibung|  
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