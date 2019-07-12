---
title: Testleitfaden für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6790e61eddc81045bb168028ee7aeef7a0492e3c
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825746"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testleitfaden für Quellcodeverwaltungs-Plug-Ins
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dieser Abschnitt enthält Anweisungen zum Testen Ihrer plug-in mit quellcodeverwaltung [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Ein umfassender Überblick über die am häufigsten verwendeten Tests Bereiche sowie einige der schwierigeren Bereiche, die möglicherweise problematische wird bereitgestellt. In dieser Übersicht ist nicht vorgesehen, um eine vollständige Liste der Testfälle.  
  
> [!NOTE]
> Einige Fehlerkorrekturen und Verbesserungen an den neuesten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE unter Umständen Probleme mit vorhandenen Quellcodeverwaltungs-Plug-ins, die bei der Verwendung von früheren Versionen von zuvor nicht aufgetreten sind aufdecken [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Es wird dringend empfohlen, dass Sie Ihrem vorhandenen Quellcodeverwaltungssystem-Plug-In für die Bereiche, die in diesem Abschnitt aufgelisteten testen, auch wenn keine Änderungen seit der vorherigen Version von an das plug-in vorgenommen wurden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="common-preparation"></a>Allgemeine Vorbereitung  
 Ein Computer mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und das Ziel-Quellcodeverwaltungs-Plug-In installiert ist, ist erforderlich. Ein zweiter Computer, auf ähnliche Weise konfiguriert werden, kann für einige der Öffnen aus der Quellcodeverwaltung, Tests verwendet werden.  
  
## <a name="definition-of-terms"></a>Begriffsdefinition  
 Verwenden Sie im Rahmen dieser Anleitung die folgenden Definitionen für den Ausdruck ein:  
  
 Client-Projekt  
 Einen Projekttyp in verfügbaren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , unterstützt die Integration der quellcodeverwaltung (z. B. [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], oder [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]).  
  
 Webprojekt  
 Es gibt vier Arten von Webprojekten: Dateisystem, lokale IIS, Remotestandorten und FTP.  
  
- Datei-System-Projekte unter einem lokalen Pfad erstellt, aber sie erfordern nicht die IIS (Internetinformationsdienste) installiert werden, wie sie intern über einen UNC-Pfad zugegriffen wird, und in der quellcodeverwaltung aus der IDE, ähnlich wie Clientprojekte platziert werden können.  
  
- Lokale IIS-Projekte funktionieren mit IIS, die auf dem gleichen Computer installiert ist und erfolgt mit einer URL, die auf dem lokalen Computer verweist.  
  
- Entfernte Standorte Projekte auch unter IIS-Dienste erstellt werden, jedoch werden sie platziert, in der quellcodeverwaltung auf dem IIS-Server-Computer und nicht von innerhalb der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
- FTP-Projekten erfolgt über eine FTP-Remoteserver, aber sie können nicht unter quellcodeverwaltung gestellt werden.  
  
  Eintragung  
  Ein weiterer Begriff für die Projektmappe oder das Projekt unter quellcodeverwaltung.  
  
  Version-Store  
  Der Quellcode-Verwaltungsdatenbank, die über die Source-Plug-in-API zugegriffen wird.  
  
## <a name="test-areas-covered-in-this-section"></a>In diesem Abschnitt behandelten Testbereiche  
  
- [Testbereich 1: Hinzufügen/Öffnen über die Quellcodeverwaltung](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
  - Groß-/Kleinschreibung 1a: Projektmappe zur Quellcodeverwaltung hinzufügen  

  - Fall 1 b: Die Projektmappe aus der Quellcodeverwaltung öffnen  

  - Fall 1c: Fügen Sie die Lösung aus der Quellcodeverwaltung hinzu  

- [Testbereich 2: Abrufen aus der Quellcodeverwaltung](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
- [Testbereich 3: Auschecken/Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
  - Fall 3: Auschecken / Auschecken rückgängig machen  

  - Groß-/Kleinschreibung 3a: Auschecken  

  - Fall 3 b: Offline-Auscheckvorgang  

  - Fall 3c: / Queryeditquerysave (QEQS.)  

  - Case-3d: Automatische Auschecken  

  - Groß-/Kleinschreibung 3e: Rückgängig: Auschecken  
  
- [Testbereich 4: Einchecken](../../extensibility/internals/test-area-4-check-in.md)  
  
  - Groß-/Kleinschreibung 4a: Geänderte Elemente  

  - Groß-/Kleinschreibung 4 b: Hinzufügen von Dateien  

  - Fall 4c: Hinzufügen von Projekten  
  
- [Testbereich 5: Ändern der Quellcodeverwaltung](../../extensibility/internals/test-area-5-change-source-control.md)  
  
  - Groß-/Kleinschreibung 5a: Binden  

  - Case 5b: Aufheben der Bindung  

  - Fall 5c: erneut binden  

- [Testbereich 6: Löschen](../../extensibility/internals/test-area-6-delete.md)  

- [Testbereich 7: Freigeben](../../extensibility/internals/test-area-7-share.md)  

- [Testbereich 8: Plug-In-Wechsel](../../extensibility/internals/test-area-8-plug-in-switching.md)  

  - Groß-/Kleinschreibung 8a: Automatische Änderung  

  - Groß-/Kleinschreibung 8 b: Informationsreiche lösungsbasierte ändern  

## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)
