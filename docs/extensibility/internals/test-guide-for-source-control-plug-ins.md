---
title: Testhandbuch für Quellcodeverwaltungs-Plug-Ins | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704373"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testleitfaden für Quellcodeverwaltungs-Plug-Ins
Dieser Abschnitt enthält Anleitungen zum Testen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]des Quellcodeverwaltungs-Plug-Ins mit . Ein umfassender Überblick über die am häufigsten gegeuzten Testbereiche sowie einige der komplizierteren Bereiche, die problematisch sein können, wird bereitgestellt. Diese Übersicht soll keine erschöpfende Liste von Testfällen sein.

> [!NOTE]
> Einige Fehlerbehebungen und [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Verbesserungen der neuesten IDE können Probleme mit vorhandenen Quellcodeverwaltungs-Plug-Ins aufdecken, die zuvor bei der Verwendung früherer Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]nicht aufgetreten sind. Es wird dringend empfohlen, das vorhandene Quellcodeverwaltungs-Plug-In für die in diesem Abschnitt aufgezählten Bereiche zu testen, auch [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]wenn seit der vorherigen Version von keine Änderungen am Plug-In vorgenommen wurden.

## <a name="common-preparation"></a>Gemeinsame Vorbereitung
 Eine Maschine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit und das Ziel-Quellcodeverwaltungs-Plug-in ist erforderlich. Eine zweite Maschine, die ähnlich konfiguriert ist, kann für einige der Open from Source Control-Tests verwendet werden.

## <a name="definition-of-terms"></a>Definition der Begriffe
 Verwenden Sie für die Zwecke dieses Testhandbuchs die folgenden Begriffsdefinitionen:

 Clientprojekt Jeder [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in verfügbare Projekttyp unterstützt die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Quellcodeverwaltungsintegration (z. B. , oder [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Webprojekt Es gibt vier Arten von Webprojekten: Dateisystem, lokale IIS, Remotesites und FTP.

- Dateisystemprojekte werden auf einem lokalen Pfad erstellt, erfordern jedoch nicht, dass die Internetinformationsdienste (Internet Information Services, IIS) installiert werden, da sie intern über einen UNC-Pfad aufgerufen werden, und können von der IDE aus unter Quellcodeverwaltung gestellt werden, ähnlich wie Clientprojekte.

- Lokale IIS-Projekte arbeiten mit IIS, das auf demselben Computer installiert ist und auf den mit einer URL zugegriffen wird, die auf den lokalen Computer verweist.

- Remotesites-Projekte werden ebenfalls unter einem IIS-Dienst erstellt, aber sie werden unter Quellcodeverwaltung auf dem IIS-Servercomputer und nicht innerhalb der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE platziert.

- Auf FTP-Projekte wird über einen Remote-FTP-Server zugegriffen, sie können jedoch nicht unter Quellcodeverwaltung gestellt werden.

  Einschreibeantrag Ein weiterer Begriff für die Projektmappe oder das Projekt unter Quellcodeverwaltung.

  Versionsspeicher Die Quellcodeverwaltungsdatenbank, auf die über die Quellcodeverwaltungs-Plug-In-API zugegriffen wird.

## <a name="test-areas-covered-in-this-section"></a>Testbereiche, die in diesem Abschnitt behandelt werden

- [Testbereich 1: Hinzufügen zu/Öffnen von der Quellcodeverwaltung](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Fall 1a: Hinzufügen einer Lösung zur Quellcodeverwaltung

  - Fall 1b: Open Solution von source Control

  - Fall 1c: Hinzufügen einer Lösung aus der Quellcodeverwaltung

- [Testbereich 2: Abrufen aus der Quellcodeverwaltung](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Testbereich 3: Auschecken/Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Fall 3: Auschecken/Auschecken rückgängig machen

  - Fall 3a: Check Out

  - Fall 3b: Getrennte Kasse

  - Fall 3c: Abfragebearbeitung/Abfragespeicherung (QEQS)

  - Fall 3d: Stille Kasse

  - Fall 3e: Auschecken rückgängig machen

- [Testbereich 4: Einchecken](../../extensibility/internals/test-area-4-check-in.md)

  - Fall 4a: Geänderte Artikel

  - Fall 4b: Hinzufügen von Dateien

  - Fall 4c: Hinzufügen von Projekten

- [Testbereich 5: Ändern der Quellcodeverwaltung](../../extensibility/internals/test-area-5-change-source-control.md)

  - Fall 5a: Bind

  - Fall 5b: Unbind

  - Fall 5c: Rebind

- [Testbereich 6: Löschen](../../extensibility/internals/test-area-6-delete.md)

- [Testbereich 7: Freigeben](../../extensibility/internals/test-area-7-share.md)

- [Testbereich 8: Plug-In-Wechsel](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Fall 8a: Automatischer Wechsel

  - Fall 8b: Lösungsbasierter Wandel

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)
