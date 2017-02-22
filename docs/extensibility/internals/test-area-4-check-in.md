---
title: "Testbereich 4: &#220;berpr&#252;fen Sie im | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Überprüfung der Elemente in der Datenquellen-Steuerelement [Visual Studio SDK]"
  - "Source Control-Plug-ins Elemente einchecken"
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Testbereich 4: &#220;berpr&#252;fen Sie im
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Datenquellen\-Steuerelement Test\-Plug\-in Hierunter Senden von aktualisierten Elemente in den Versionsspeicher über die **Einchecken** Befehl.  
  
## Befehl Menüzugriff  
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrated Development\-Umgebung im Menüpfade werden in den Testfällen verwendet.  
  
##### Ankunft:  
 **Datei**, **Quellcodeverwaltung**, **Einchecken**.  
  
 **Datei**, **Einchecken**.  
  
 Klicken Sie im Kontextmenü **Einchecken**.  
  
## Allgemeine erwartet  
  
-   Projekte und Projektmappen oder Projekten Quellcodeverwaltungsprojekt hinzugefügten Dateien angezeigt, der **Einchecken** Dialogfeld und der **Anstehende Eincheckvorgänge** Fenster.  
  
-   Nach dem Einchecken werden Sie im Datenquellen\-Steuerelement hinzugefügten Elemente angezeigt.  
  
-   Nach der Prüfung in sind aktualisierte Elemente ordnungsgemäß mit Versionsangabe im Speicher.  
  
## Testfälle  
 Im folgenden sind bestimmte Testfälle für die Checkin\-Testbereich.  
  
### Case\-4a: geänderten Elemente  
 Beschreibt die Verwendung der Kontrollkästchen in Aktion eine quellcodeverwaltete Datei aktualisieren, die geändert wurde.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Ändern Sie eine Textdatei, die ausgecheckt wurde, überprüfen Sie in nur\-Datei \(**Einchecken** Dialogfeld\)|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Checken Sie aus und ändern Sie die Textdatei.<br />4.  Über das Dialogfeld Einchecken Einchecken \(**Datei**, **Quellcodeverwaltung**, **Einchecken**\).|Allgemeine erwartet.|  
|Ändern Sie eine Textdatei, die ausgecheckt wurde, überprüfen Sie in nur\-Datei \(**Anstehende Eincheckvorgänge** Fenster\)|1.  Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Checken Sie aus und ändern Sie die Textdatei.<br />4.  Überprüfen Sie die im über die **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet.|  
  
### Fall 4 b: Hinzufügen von Dateien  
 Beim Hinzufügen einer Datei zu einem Projekt oder ein Element zu einer Lösung muss auch das Projekt oder die Projektmappe ändern. Daher wird die übergeordnete Datei ebenfalls ausgecheckt und muss eingecheckt werden, das Hinzufügen abgeschlossen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Fügen Sie eine Textdatei, und alles einchecken \(**Einchecken** Dialogfeld\)|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Fügen Sie dem Projekt eine Textdatei.<br />4.  Auschecken des Projekts wird akzeptiert, wenn Sie dazu aufgefordert werden.<br />5.  Wählen Sie die Projektmappe in **Projektmappen\-Explorer**.<br />6.  Einchecken aus dem **Einchecken** \(Dialogfeld\).|Allgemeine erwartet.|  
|Fügen Sie eine Textdatei, und alles einchecken \(**Anstehende Eincheckvorgänge** Fenster\)|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Fügen Sie dem Projekt eine Textdatei.<br />4.  Auschecken des Projekts wird akzeptiert, wenn Sie dazu aufgefordert werden.<br />5.  Einchecken von Projektmappen aus **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet|  
  
### Fall 4c: Hinzufügen von Projekten  
 Wenn Sie ein Projekt zu einer Projektmappe hinzufügen, muss die Lösung auch ändern. Daher wird die Projektmappendatei auch ausgecheckt und muss eingecheckt werden, das Hinzufügen abgeschlossen.  
  
|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|  
|------------|------------------|-------------------------------------|  
|Fügen Sie ein Projekt auf eine leere Projektmappe unter quellcodeverwaltung \(**Einchecken** Dialogfeld\)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Fügen Sie ein neues Projekt.<br />4.  Akzeptieren Sie Auschecken der Lösung, wenn Sie aufgefordert werden.<br />5.  Einchecken aus dem **Einchecken** \(Dialogfeld\).|Allgemeine erwartet.|  
|Fügen Sie ein Projekt auf eine leere Projektmappe unter quellcodeverwaltung \(**Anstehende Eincheckvorgänge** Fenster\)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur Versionskontrolle hinzu.<br />3.  Fügen Sie ein neues Projekt.<br />4.  Akzeptieren Sie Auschecken der Lösung, wenn Sie aufgefordert werden.<br />5.  Einchecken von Projektmappen aus **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)