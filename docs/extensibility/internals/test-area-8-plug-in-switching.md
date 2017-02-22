---
title: "Testbereich 8: Plug-In-Umschaltung | Microsoft Docs"
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
  - "Datenquellen-Steuerelement [Visual Studio SDK] switching-Plug-ins"
  - "Source Control-Plug-ins wechseln"
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Testbereich 8: Plug-In-Umschaltung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung \(IDE\) verfügt über die Benutzeroberfläche \(UI\), um den aktuellen Quelle Plug\-In für steuer zu ändern.  Dieses Testgebiet stellt Testfälle für den Prozess des Sammelns, der für Projektmappen quellcodeverwaltung das Plug\-In zu verwenden.  
  
## Befehls\-Menü\-Zugriff  
 Die folgenden integrierten Entwicklungsumgebung [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für Menüs werden in Testfällen verwendet.  
  
-   Plug\-In für steuer aktuellen Quelle: **Extras** \- \> **Optionen** \- \> **Quellcodeverwaltung** \- \> **Plug\-In\-Auswahl**.  
  
-   Ändern quellcodeverwaltungsbindung: **Datei** \- \> **Quellcodeverwaltung** \- \> **Quellcodeverwaltung ändern**…  
  
## Allgemeines erwartetes Verhalten  
 Das Quellcodeverwaltungs\-Plug\-In für eine Projektmappe zu ändern ist möglich, ohne Visual Studio zu beenden oder die Projektmappe erneut zu laden.  Außerdem ändert der aktuellen Quelle steuer automatisch auf das Plug\-In für das von einer Projektmappe verwendet wird, wenn diese Projektmappe geladen wird.  
  
## Testfälle  
 Im Folgenden sind bestimmte Testfälle für das Plug\-In umschaltende Testgebiet.  
  
### Fall 8a: Automatische Änderung  
  
#### Erwartetes Verhalten  
 Wenn ein Benutzer eine Projektmappe geladen wird, die der Quellcodeverwaltung unterliegt, wird die Projektmappe automatisch geladen und das entsprechende Quellcodeverwaltungs\-Plug\-In wird als aktuell ausgewählt.  
  
|Aktion|Testschritte|Erwartete Ergebnisse zu überprüfen|  
|------------|------------------|----------------------------------------|  
|Automatische Quellcodeverwaltungs\-Plug\-In\-Änderung|1.  Wählen Sie in Plug\-In als versucht \> \-**Extras** \(Current \> \- **OptionenQuellcodeverwaltung** \- \> **Plug\-In\-Auswahl**\).<br />2.  Erstellen Sie ein neues Projekt.<br />3.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />4.  Wählen Sie ein anderes Plug\-In aus \(z. B. [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />5.  Accept Projektmappen Eingabeaufforderung nehmend entladen.<br />6.  Öffnen Sie die Projektmappe aus dem Datenträger.|Projektmappe geöffnet ist.<br /><br /> Plug\-In getestet wird das Plug\-In für steuer aktuellen Quelle.|  
  
### Fall 8b: Projektmappe\-basierte Änderung  
  
#### Erwartetes Verhalten  
 Die Projektmappe kann das zugehörige geändertes Quellcodeverwaltungs\-Plug\-In haben.  
  
|Aktion|Testschritte|Erwartete Ergebnisse zu überprüfen|  
|------------|------------------|----------------------------------------|  
|Ändern des Plug\-Ins für eine Projektmappe|1.  Wählen Sie in Plug\-In als versucht \> \-**Extras** \(Current \> \- **OptionenQuellcodeverwaltung** \- \> **Plug\-In\-Auswahl**\).<br />2.  Erstellt ein neues Projekt und eine Projektmappe.<br />3.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />4.  Befreien Sie die Projektmappe aus der Quellcodeverwaltung \(unter Verwendung des **Quellcodeverwaltung ändern** Dialogfelds\).<br />5.  Wählen Sie ein anderes Plug\-In aus \(z. B. [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />6.  Laden Sie die Projektmappe von einem Datenträger, wenn Sie entladen werden.<br />7.  Fügen Sie die Projektmappe zur Quellcodeverwaltung hinzufügen.<br />8.  Befreien Sie die Projektmappe aus der Quellcodeverwaltung \(mithilfe **Quellcodeverwaltung ändern** Dialogfelds\).<br />9. Wählen Sie in Plug\-In versuchen Sie es erneut.<br />10. Lädt beim Ausführen von der Festplatte Projektmappe entladen werden.<br />11. Binden Sie die Projektmappe im ursprünglichen Speicherort \(unter Verwendung des **Quellcodeverwaltung ändern** Dialogfelds\).|Projektmappe zur Quellcodeverwaltung hinzugefügt wird, indem das ausgewählte Plug\-In verwendet.|  
  
## Siehe auch  
 [Test\-Handbuch für Source Control\-Plug\-ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)