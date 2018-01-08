---
title: "Testbereich 6: Löschen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 204038ac7a86c0b458ea08c2f4bd2c6a4dffe7cd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-6-delete"></a>Testbereich 6: Löschen
Dieser Bereich der quellcodeverwaltung für die Test-Plug-in behandelt Delete-Aktionen.  
  
 Datenquellen-Steuerelements zum Löschen von Aktionen in reagiert **Projektmappen-Explorer**.  
  
 Es folgt eine Liste von Elementen, die gelöscht werden können:  
  
-   Dateien  
  
-   Ordner  
  
-   Projekt  
  
 Je nach Projekttyp, haben Sie möglicherweise die Möglichkeit, **entfernen** des Projekts (bewirkt, dass die Dateien auf dem Datenträger) oder **löschen** des Projekts (entfernt die Dateien auf dem Datenträger). Aktionen entfernt, das Projekt oder Element von **Projektmappen-Explorer**.  
  
## <a name="expected-behavior"></a>Erwartetes Verhalten  
 Das erwartete Verhalten für die Testfälle in der Delete-Test-Bereich ist:  
  
-   Gelöschtes Element wird nicht mehr angezeigt, in **Projektmappen-Explorer**.  
  
-   Das übergeordnete Element der gelöschten Projekts oder des Elements ist ausgecheckt, Bedarf (möglicherweise mit einer Eingabeaufforderung.)  
  
-   Nach dem Löschen einer überprüften oder Element hinzugefügt, es erscheint nicht in der **Anstehende Eincheckvorgänge** Fenster.  
  
-   Das Element noch vorhanden ist in den Speicher der quellcodeverwaltung, auch nach dem Löschen und muss manuell gelöscht werden.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Löschen Sie ein Clientprojekt|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Entfernen Sie das gesamte Projekt aus der Projektmappe|Allgemeine erwartet.|  
|Löschen Sie eine leere Datei|1.  Erstellen Sie ein Clientprojekt.<br />2.  Fügen Sie dem Projekt eine Datei mit NULL Byte hinzu.<br />3.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />4.  Wählen Sie die Datei, löschen Sie ihn.|Allgemeine erwartet.|  
|Löschen Sie einen Ordner mit einer Datei|1.  Einzelnen Projektmappe zu erstellen.<br />2.  Fügen Sie einen Ordner hinzu.<br />3.  Fügen Sie eine Datei in den Ordner ein.<br />4.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />5.  Sehen Sie sich das Projekt, um aufforderungen zu vermeiden.<br />6.  Löschen Sie den Ordner an.|Allgemeine erwartet.|  
|Löschen einer Datei System-Webprojekt|1.  Erstellen Sie eine Datei System-Webprojekt (verwenden Sie die Schaltfläche zum Durchsuchen an einen UNC-Pfad).<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Entfernen Sie das gesamte Projekt aus der Projektmappe.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für eine lokale Webprojekt (unterschiedliche Pfade durch den Code ausführt, aber hat die gleiche externe Schnittstelle und das Verhalten).|Allgemeine erwartet.|  
|Löschen einer Datei aus einer Datei System-Webprojekt|1.  Erstellen Sie eine Datei System-Webprojekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Löschen Sie eine Datei aus dem Projekt ein.<br />4.  Wiederholen Sie die Schritte 1 bis 3 für eine lokale Webprojekt (unterschiedliche Pfade durch den Code ausführt, aber hat die gleiche externe Schnittstelle und das Verhalten).|Allgemeine erwartet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)