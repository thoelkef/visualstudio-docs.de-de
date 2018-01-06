---
title: "Handbuch für die Datenquellen-Steuerelement-Plug-ins | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0fdab6cb0b259fe169a9ebd43c92158a5ce20d4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testhandbuch für die Datenquellen-Steuerelement-Plug-ins
Dieser Abschnitt enthält Anweisungen zum Testen als Quellcodeverwaltungs-Plug-in mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Eine umfassende Übersicht über die am häufigsten verwendeten Testbereiche sowie einige mehr komplizierte Bereiche, die möglicherweise problematisch wird bereitgestellt. Diese Übersicht ist nicht vorgesehen, um eine vollständige Liste der Testfälle.  
  
> [!NOTE]
>  Einige Fehlerbehebungen und Verbesserungen auf die neueste [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE möglicherweise Probleme mit vorhandenen Datenquellen-Steuerelement-Plug-ins, die bei der Verwendung von früheren Versionen von zuvor nicht gefunden wurden aufdecken [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Es wird dringend empfohlen, dass Sie vorhandene Quellcodeverwaltungs-Plug-In für die Bereiche, die in diesem Abschnitt aufgelisteten testen, auch wenn keine Änderungen seit der vorherigen Version von an das plug-in vorgenommen wurden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Allgemeine Vorbereitung  
 Ein Computer mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und das Ziel-Datenquellen-Steuerelement-Plug-In installiert ist, ist erforderlich. Ein zweiter Computer entsprechend konfiguriert, kann für die Benutzeroberflächenelemente von der Open Source Control Tests verwendet werden.  
  
## <a name="definition-of-terms"></a>Begriffsdefinition  
 Verwenden Sie in dieser Anleitung die folgenden Begriffsdefinitionen:  
  
 Client-Projekt  
 Ein Projekt in verfügbaren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , die Integration der quellcodeverwaltung unterstützt (z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], oder [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Webprojekt  
 Es gibt vier Arten von Webprojekten: File System, lokaler IIS Remotestandorten und FTP.  
  
-   Datei-System-Projekte werden in einem lokalen Verzeichnis erstellt, aber die IIS (Internetinformationsdienste) installiert werden, wie sie werden intern über einen UNC-Pfad zugegriffen, und in der quellcodeverwaltung aus der IDE, ähnlich wie clientprojekten platziert werden können, nicht erforderlich.  
  
-   Lokale IIS-Projekte können mit IIS, die auf dem gleichen Computer installiert ist und erfolgt mit einer URL auf dem lokalen Computer verweist.  
  
-   Entfernten Standorten Projekte werden auch unter IIS-Dienste erstellt, jedoch werden sie platziert, in der quellcodeverwaltung auf dem IIS-Servercomputer und nicht von innerhalb der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   FTP-Projekte erfolgt über eine FTP-Remoteserver, aber sie können nicht in der quellcodeverwaltung platziert werden.  
  
 Eintragung  
 Eine andere Bezeichnung für die Projektmappe oder das Projekt unter quellcodeverwaltung.  
  
 Versionsspeicher  
 Der Quellcode-Verwaltungsdatenbank, die über die Quelle Steuerelement-Plug-in-API zugegriffen wird.  
  
## <a name="test-areas-covered-in-this-section"></a>In diesem Abschnitt behandelten Testbereiche  
  
-   [Testbereich 1: Fügen Sie hinzu, / Open-aus der Quellcodeverwaltung](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Case-1a: Hinzufügen von Projektmappen zur Quellcodeverwaltung  
  
    -   Fall 1 b: Öffnen Sie die Projektmappe aus der Quellcodeverwaltung  
  
    -   Fall 1c: Hinzufügen von Projektmappen aus der Quellcodeverwaltung  
  
-   [Testbereich 2: Abrufen aus der Quellcodeverwaltung](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Testbereich 3: Auschecken / rückgängig: Auschecken](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Fall 3: Auschecken / rückgängig: Auschecken  
  
    -   Case-3a: Auschecken  
  
    -   Fall 3 b: Auschecken getrennt  
  
    -   Fall 3c: Abfrage bearbeiten/Abfrage speichern (QEQS.)  
  
    -   Fall 3d: Automatische Auschecken  
  
    -   Case-3e: Auschecken rückgängig machen  
  
-   [Testbereich 4: Einchecken](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Case-4a: geänderten Elemente  
  
    -   Fall 4: Hinzufügen von Dateien  
  
    -   Fall 4c: Hinzufügen von Projekten  
  
-   [Testbereich 5: Ändern der Quellcodeverwaltung](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Fall 5a: Binden  
  
    -   Fall 5 b: Aufheben der Bindung  
  
    -   Case-5c: erneut binden  
  
-   [Testbereich 6: Löschen](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Testbereich 7: Freigeben](../../extensibility/internals/test-area-7-share.md)  
  
-   [Testbereich 8: Plug-In-Wechsel](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Fall 8a: automatisch ändern  
  
    -   Case-8 b: Change basierten Lösung  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)