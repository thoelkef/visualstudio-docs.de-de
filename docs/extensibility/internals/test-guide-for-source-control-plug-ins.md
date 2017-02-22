---
title: "Test-Handbuch f&#252;r Source Control-Plug-ins | Microsoft Docs"
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
  - "Plug-ins und Datenquellen-Steuerelement"
  - "Test-Plug-ins der Datenquellen-Steuerelement [Visual Studio SDK]"
  - "Tests, Source Control-Plug-ins"
  - "Prüfung, Source Control-Plug-ins"
  - "Source Control-Plug-ins Testhandbuch"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Test-Handbuch f&#252;r Source Control-Plug-ins
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieser Abschnitt enthält Hinweise zum Testen des Quellcodeverwaltungs\-Plug\-In mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Eine ausführliche Übersicht über die gängigsten testenden Bereiche sowie einige der verwickelteren Bereiche, die möglicherweise problematisch ist, wird bereitgestellt.  In dieser Übersicht wird nicht um eine vollständige Liste von Testfällen handeln.  
  
> [!NOTE]
>  Einige Fehlerkorrekturen und Verbesserungen auf das neueste [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE anordnen können Probleme mit vorhandenen steckverbindungen Quellcodeverwaltung auf, die zuvor nicht bei der Verwendung von früheren Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aufgetreten sind.  Es wird dringend empfohlen, dass Sie das vorhandene Quellcodeverwaltungs\-Plug\-In für die Bereiche testen, die in diesem Abschnitt aufgelistet werden, auch wenn keine Änderungen am Plug\-In seit der vorherigen Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vorgenommen wurden.  
  
## Allgemeine Vorbereitung  
 Ein Computer mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und das Zielquellcodeverwaltungs\-plug\-in, das installiert wird, ist erforderlich.  Ein zweiter auf ähnliche Weise konfigurierter Computer kann für einige der Quellcodeverwaltung aus dem geöffneten Tests verwendet werden.  
  
## Definition von Ausdrücken  
 Um diesen Test handbuch, die Definitionen der folgenden Ausdruck:  
  
 Clientprojekt  
 Jeder Projekttyp verfügbar in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , der Quellcodeverwaltungsintegration unterstützt \(z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]oder [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\).  
  
 Webprojekt  
 Es gibt vier Typen von Webprojekten: Dateisystem, Lokale IIS, Remotewebsites und FTP.  
  
-   Dateisystem Projekte werden in einem lokalen Pfad erstellt, aber sie müssen nicht die Internetinformationsdienste \(IIS\) installiert, während sie intern über einen UNC\-Pfad zugegriffen werden kann und der IDE aus der Quellcodeverwaltung ausgecheckt, ähnlich wie bei Clientprojekte platziert werden.  
  
-   Lokale IIS\-Projekt Arbeit mit IIS, das auf dem gleichen Computer installiert ist und mit einer URL zugegriffen wird, das dem lokalen Computer verweist.  
  
-   Außerdem werden von Projekten Remotesite unter einem IIS\-Dienstleistungen erstellt, sie werden jedoch unter Quellcodeverwaltung auf dem IIS\-Server Computer und nicht aus dem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Bereichs platziert.  
  
-   FTP\-Projekte werden durch einen Remote FTP\-Server zugegriffen, nicht jedoch in einem Quellcodeverwaltungssystem gespeichert werden.  
  
 Eintragung  
 Ein anderer Ausdruck für die Projektmappe oder Projekt in die Quellcodeverwaltung einbezogen.  
  
 Versions\-Speicher  
 Die Quellcodeverwaltungs\-Datenbank, die durch das Quellcodeverwaltungs\-Plug\-In API zugegriffen wird.  
  
## Testbereiche in diesem Abschnitt beschriebenen  
  
-   [Testbereich 1: Fügen Sie und Öffnen von Datenquellen\-Steuerelement hinzu](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   1a Fall: Fügen Sie der Projektmappe zur Quellcodeverwaltung hinzufügen  
  
    -   1b Fall: Öffnen Sie die Projektmappe aus der Quellcodeverwaltung  
  
    -   1c Fall: Fügen Sie der Projektmappe aus der Quellcodeverwaltung hinzufügen  
  
-   [Testbereich 2: Abrufen von Datenquellen\-Steuerelement](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Testbereich 3: Auschecken \/ Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Fall 3: Stellen Sie sicher, out\/Rückgängig Auschecken  
  
    -   Fall 3a: Auschecken  
  
    -   Fall: 3b Nicht verbundenen Auschecken  
  
    -   Fall: 3c Abfragen\-Bearbeitung\/Abfragen\-Abwehr \(QEQS\)  
  
    -   Fall: 3D Automatisches Auschecken  
  
    -   Fall 3e: Auschecken rückgängig  
  
-   [Testbereich 4: Überprüfen Sie im](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   4a Fall: Der geänderte Elemente  
  
    -   Fall 4b: Hinzufügen von Dateien  
  
    -   4c Fall: Hinzufügen von Projekten  
  
-   [Testbereich 5: Change\-Datenquellen\-Steuerelement](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Fall: 5a Bindung  
  
    -   Fall: 5b Befreien von  
  
    -   Fall: 5c Binden Sie erneut  
  
-   [Testbereich 6: Löschen](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Testbereich 7: Freigabe](../../extensibility/internals/test-area-7-share.md)  
  
-   [Testbereich 8: Plug\-In\-Umschaltung](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Fall 8a: Automatische Änderung  
  
    -   Fall 8b: Projektmappe\-basierte Änderung  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../../extensibility/source-control-plug-ins.md)