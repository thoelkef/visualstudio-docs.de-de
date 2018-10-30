---
title: 'Testbereich 6: Löschen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ce67ded280fd87fbcabd72d7ca45f1af8568336
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888215"
---
# <a name="test-area-6-delete"></a>Testbereich 6: Löschen
Quellcodeverwaltung Hierunter-Plug-in Test löschen-Aktionen.  
  
 Löschen von Aktionen im Datenquellen-Steuerelement reagiert **Projektmappen-Explorer**.  
  
 Es folgt eine Liste von Elementen, die gelöscht werden können:  
  
- Dateien  
  
- Ordner  
  
- Projekt  
  
  Je nach Projekttyp, haben Sie möglicherweise die Möglichkeit, **entfernen** des Projekts (verlassen die Dateien auf Datenträger) oder **löschen** des Projekts (entfernt die Dateien auf dem Datenträger). Beide Aktionen entfernt, das Projekt oder Projektelement aus **Projektmappen-Explorer**.  
  
## <a name="expected-behavior"></a>Es wird erwartet  
 Das erwartete Verhalten für die Testfälle im Testbereich löschen ist:  
  
-   Gelöschtes Element wird nicht mehr angezeigt, in **Projektmappen-Explorer**.  
  
-   Das gelöschte Projekt oder Element das übergeordnete Element ist ausgecheckt, nach Bedarf (möglicherweise mit einer Eingabeaufforderung.)  
  
-   Nachdem Sie einen aktivierten zu löschen oder Element hinzugefügt, er erscheint nicht in der **Anstehende Eincheckvorgänge** Fenster.  
  
-   Das Element ist immer noch im Speicher quellcodeverwaltung, vorhanden ist, auch nach dem Löschvorgang erhalten, und muss manuell gelöscht werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Löschen eines Clientprojekts|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Entfernen Sie das gesamte Projekt aus Projektmappe|Allgemeine Erwartetes Verhalten.|  
|Löschen Sie eine leere Datei|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie eine Datei zum Projekt hinzu.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Wählen Sie die Datei, löschen Sie diese.|Allgemeine Erwartetes Verhalten.|  
|Löschen eines Ordners mit einer Datei|1.  Einzelne Projektmappe zu erstellen.<br />2.  Fügen Sie einen Ordner hinzu.<br />3.  Fügen Sie eine Datei in den Ordner hinzu.<br />4.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />5.  Sehen Sie sich das Projekt aus, um aufforderungen zu vermeiden.<br />6.  Löschen Sie den Ordner an.|Allgemeine Erwartetes Verhalten.|  
|Löschen einer Datei System-Webprojekt|1.  Erstellen Sie eine Datei System Web-Projekt (verwenden Sie die Schaltfläche zum Durchsuchen an einen UNC-Pfad).<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Entfernen Sie das gesamte Projekt aus der Projektmappe.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt (verschiedene Pfade durch den Code ausführt, aber hat die gleiche externe Schnittstelle und das Verhalten).|Allgemeine Erwartetes Verhalten.|  
|Löschen einer Datei aus einer Datei System-Webprojekt|1.  Erstellen Sie ein Projekt Datei System.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Löschen Sie eine Datei aus dem Projekt ein.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt (verschiedene Pfade durch den Code ausführt, aber hat die gleiche externe Schnittstelle und das Verhalten).|Allgemeine Erwartetes Verhalten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)