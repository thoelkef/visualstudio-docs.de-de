---
title: "Testbereich 4: Überprüfen Sie die im | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3694e8f4a8cdbdac147df3d6e60324888bccf048
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-4-check-in"></a>Testbereich 4: Melden Sie sich
Dieser Bereich der quellcodeverwaltung für die Test-Plug-in behandelt Senden der aktualisierten Elemente in den Versionsspeicher über die **Einchecken** Befehl.  
  
## <a name="command-menu-access"></a>Menüzugriff Befehl  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
##### <a name="check-in"></a>Ankunft:  
 **Datei**, **Quellcodeverwaltung**, **Einchecken**.  
  
 **Datei**, **Einchecken**.  
  
 Klicken Sie im Kontextmenü **Einchecken**.  
  
## <a name="common-expected-behavior"></a>Allgemeine erwartet  
  
-   Projekte und Projektmappen oder Projekten unter quellcodeverwaltung hinzugefügten Dateien angezeigt, der **Einchecken** Dialogfeld und der **Anstehende Eincheckvorgänge** Fenster.  
  
-   Nach der Prüfung in werden Sie in der quellcodeverwaltung hinzugefügte Elemente angezeigt.  
  
-   Nach der Prüfung in sind aktualisierte Elemente im Speicher ordnungsgemäß mit Versionsangabe.  
  
## <a name="test-cases"></a>Testfälle  
 Im folgenden finden bestimmte Testfälle zum Bereich "Checkin-Test".  
  
### <a name="case-4a-modified-items"></a>Case-4a: geänderten Elemente  
 Beschreibt die Verwendung der Kontrollkästchen in Aktion zu eine quellcodeverwalteten Datei aktualisieren, die geändert wurde.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Ändern Sie eine Textdatei, die ausgecheckt wurde, überprüfen Sie im nur-Datei (**Einchecken** Dialogfeld)|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Checken Sie aus und ändern Sie die Textdatei.<br />4.  Über das Dialogfeld Einchecken Einchecken (**Datei**, **Quellcodeverwaltung**, **Einchecken**).|Allgemeine erwartet.|  
|Ändern Sie eine Textdatei, die ausgecheckt wurde, überprüfen Sie im nur-Datei (**Anstehende Eincheckvorgänge** Fenster)|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Checken Sie aus und ändern Sie die Textdatei.<br />4.  Überprüfen Sie die im über die **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet.|  
  
### <a name="case-4b-adding-files"></a>Fall 4: Hinzufügen von Dateien  
 Beim Hinzufügen einer Datei für ein Projekt oder ein Element zu einer Lösung muss das Projekt oder eine Projektmappe auch ändern. Daher wird die übergeordnete Datei ist auch ausgecheckt und muss eingecheckt werden können, um das Hinzufügen abgeschlossen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Fügen Sie eine Textdatei, und alles einchecken (**Einchecken** Dialogfeld)|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie dem Projekt eine Textdatei.<br />4.  Akzeptieren Sie Auschecken des Projekts, wenn Sie aufgefordert werden.<br />5.  Wählen Sie die Projektmappe in **Projektmappen-Explorer**.<br />6.  Überprüfen Sie der **Einchecken** (Dialogfeld).|Allgemeine erwartet.|  
|Fügen Sie eine Textdatei, und alles einchecken (**Anstehende Eincheckvorgänge** Fenster)|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie dem Projekt eine Textdatei.<br />4.  Akzeptieren Sie Auschecken des Projekts, wenn Sie aufgefordert werden.<br />5.  Einchecken der Lösung von **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet|  
  
### <a name="case-4c-adding-projects"></a>Fall 4c: Hinzufügen von Projekten  
 Wenn Sie ein Projekt zu einer Projektmappe hinzufügen, muss die Lösung auch ändern. Daher wird die Projektmappendatei auch ausgecheckt und muss eingecheckt werden können, um das Hinzufügen abgeschlossen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|----------------|--------------------------------|  
|Hinzufügen eines Projekts zu einer leeren Projektmappe unter quellcodeverwaltung (**Einchecken** Dialogfeld)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie ein neues Projekt hinzu.<br />4.  Akzeptieren Sie der Projektmappe Auschecken, wenn Sie aufgefordert werden.<br />5.  Überprüfen Sie der **Einchecken** (Dialogfeld).|Allgemeine erwartet.|  
|Hinzufügen eines Projekts zu einer leeren Projektmappe unter quellcodeverwaltung (**Anstehende Eincheckvorgänge** Fenster)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie ein neues Projekt hinzu.<br />4.  Akzeptieren Sie der Projektmappe Auschecken, wenn Sie aufgefordert werden.<br />5.  Einchecken der Lösung von **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)