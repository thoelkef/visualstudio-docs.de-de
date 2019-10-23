---
title: Test Handbuch für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51595708bf30472fd001bde394c7d8c80e39ad45
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722401"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testleitfaden für Quellcodeverwaltungs-Plug-Ins
Dieser Abschnitt enthält Anleitungen zum Testen des Quellcodeverwaltungs-Plug-ins mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Eine umfassende Übersicht über die gängigsten Testbereiche sowie einige der komplizierteren Bereiche, die möglicherweise problematisch sind, werden bereitgestellt. Diese Übersicht soll keine vollständige Liste von Testfällen sein.

> [!NOTE]
> Einige Fehlerbehebungen und Verbesserungen an der neuesten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE können Probleme mit vorhandenen Quellcodeverwaltungs-Plug-ins aufdecken, die zuvor bei früheren Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht aufgetreten sind. Es wird dringend empfohlen, das vorhandene Quellcodeverwaltungs-Plug-in für die Bereiche zu testen, die in diesem Abschnitt aufgeführt sind, auch wenn seit der vorherigen Version von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] keine Änderungen an dem Plug-in vorgenommen wurden.

## <a name="common-preparation"></a>Häufige Vorbereitung
 Ein Computer, auf dem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und das Ziel-Quellcodeverwaltungs-Plug-in installiert sind, ist erforderlich. Ein zweiter Computer, der ähnlich konfiguriert ist, kann für einige der geöffneten from-Quell Code Verwaltungs Tests verwendet werden.

## <a name="definition-of-terms"></a>Definition von Begriffen
 Verwenden Sie für diesen Test Leitfaden die folgenden Begriffs Definitionen:

 Client Projekt beliebiger Projekttyp, der in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügbar ist, die die Integration der Quell Code Verwaltung unterstützt (z.b. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Webprojekt es gibt vier Arten von Webprojekten: Datei System, lokale IIS, Remote Sites und FTP.

- Datei System Projekte werden auf einem lokalen Pfad erstellt, erfordern jedoch nicht, dass die Internetinformationsdienste (IIS) installiert werden, da auf Sie intern über einen UNC-Pfad zugegriffen wird. Sie können auch in der IDE unter Quell Code Verwaltung platziert werden, ähnlich wie bei Client Projekten.

- Lokale IIS-Projekte funktionieren mit IIS, das auf dem gleichen Computer installiert ist und auf die mit einer URL zugegriffen wird, die auf den lokalen Computer verweist.

- Projekte für Remote Standorte werden ebenfalls unter einem IIS-Dienst erstellt, aber Sie werden auf dem IIS-Server Computer unter Quell Code Verwaltung platziert und nicht innerhalb der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- Auf FTP-Projekte wird über einen Remote-FTP-Server zugegriffen, Sie können jedoch nicht unter Quell Code Verwaltung platziert werden.

  Eintragung eines anderen Begriffs für die Projekt Mappe oder das Projekt unter Quell Code Verwaltung.

  Version speichert die Quellcodeverwaltungs-Datenbank, auf die über die Quellcodeverwaltungs-Plug-in-API zugegriffen wird.

## <a name="test-areas-covered-in-this-section"></a>In diesem Abschnitt behandelte Test Bereiche

- [Testbereich 1: Hinzufügen/Öffnen über die Quellcodeverwaltung](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Fall 1a: Hinzufügen einer Projekt Mappe zur Quell Code Verwaltung

  - Fall 1B: Projekt Mappe aus Quell Code Verwaltung öffnen

  - Fall 1C: Hinzufügen einer Projekt Mappe aus der Quell Code Verwaltung

- [Testbereich 2: Abrufen aus der Quellcodeverwaltung](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Testbereich 3: Auschecken/Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Fall 3: Auschecken/rückgängig machen

  - Fall 3a: Auschecken

  - Fall 3B: Auschecken getrennt

  - Fall 3C: Abfrage Bearbeitung/Abfrage speichern (QEQS)

  - Fall 3D: Automatisches Auschecken

  - Fall 3e: Auschecken rückgängig machen

- [Testbereich 4: Einchecken](../../extensibility/internals/test-area-4-check-in.md)

  - Fall 4a: geänderte Elemente

  - Fall 4B: Hinzufügen von Dateien

  - Fall 4C: Hinzufügen von Projekten

- [Testbereich 5: Ändern der Quellcodeverwaltung](../../extensibility/internals/test-area-5-change-source-control.md)

  - Fall 5a: Binden

  - Fall 5B: Bindung aufheben

  - Case 5C: Rebind

- [Testbereich 6: Löschen](../../extensibility/internals/test-area-6-delete.md)

- [Testbereich 7: Freigeben](../../extensibility/internals/test-area-7-share.md)

- [Testbereich 8: Plug-In-Wechsel](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Case 8a: automatische Änderung

  - Fall 8B: Lösungs basierte Änderung

## <a name="see-also"></a>Siehe auch
- [Quellcodeverwaltungs-Plug-Ins](../../extensibility/source-control-plug-ins.md)
