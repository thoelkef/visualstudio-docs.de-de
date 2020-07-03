---
title: Test Handbuch für Quellcodeverwaltungs-Plug-ins | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: overview
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
ms.openlocfilehash: 321d61175068f135aae87bff73f13ac800f4793c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905157"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Testleitfaden für Quellcodeverwaltungs-Plug-Ins
Dieser Abschnitt enthält Anleitungen zum Testen des Quellcodeverwaltungs-Plug-ins mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Eine umfassende Übersicht über die gängigsten Testbereiche sowie einige der komplizierteren Bereiche, die möglicherweise problematisch sind, werden bereitgestellt. Diese Übersicht soll keine vollständige Liste von Testfällen sein.

> [!NOTE]
> Einige Fehlerbehebungen und Verbesserungen an der aktuellen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE lösen möglicherweise Probleme mit vorhandenen Quellcodeverwaltungs-Plug-ins, die zuvor nicht bei früheren Versionen von aufgetreten sind [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Es wird dringend empfohlen, das vorhandene Quellcodeverwaltungs-Plug-in für die Bereiche zu testen, die in diesem Abschnitt aufgeführt sind, auch wenn seit der vorherigen Version von keine Änderungen am Plug-in vorgenommen wurden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="common-preparation"></a>Häufige Vorbereitung
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Es ist ein Computer erforderlich, auf dem und das Ziel-Quellcodeverwaltungs-Plug-in installiert ist. Ein zweiter Computer, der ähnlich konfiguriert ist, kann für einige der geöffneten from-Quell Code Verwaltungs Tests verwendet werden.

## <a name="definition-of-terms"></a>Definition von Begriffen
 Verwenden Sie für diesen Test Leitfaden die folgenden Begriffs Definitionen:

 Client Projekt alle in verfügbaren Projekttypen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , die die Integration der Quell Code Verwaltung unterstützen (z [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . b., [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ).

 Webprojekt es gibt vier Arten von Webprojekten: Datei System, lokale IIS, Remote Sites und FTP.

- Datei System Projekte werden auf einem lokalen Pfad erstellt, erfordern jedoch nicht, dass die Internetinformationsdienste (IIS) installiert werden, da auf Sie intern über einen UNC-Pfad zugegriffen wird. Sie können auch in der IDE unter Quell Code Verwaltung platziert werden, ähnlich wie bei Client Projekten.

- Lokale IIS-Projekte funktionieren mit IIS, das auf dem gleichen Computer installiert ist und auf die mit einer URL zugegriffen wird, die auf den lokalen Computer verweist.

- Projekte für Remote Standorte werden ebenfalls unter einem IIS-Dienst erstellt, aber Sie werden auf dem IIS-Server Computer und nicht innerhalb der IDE in der Quell Code Verwaltung platziert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Auf FTP-Projekte wird über einen Remote-FTP-Server zugegriffen, Sie können jedoch nicht unter Quell Code Verwaltung platziert werden.

  Eintragung eines anderen Begriffs für die Projekt Mappe oder das Projekt unter Quell Code Verwaltung.

  Version speichert die Quellcodeverwaltungs-Datenbank, auf die über die Quellcodeverwaltungs-Plug-in-API zugegriffen wird.

## <a name="test-areas-covered-in-this-section"></a>In diesem Abschnitt behandelte Test Bereiche

- [Test Bereich 1: Hinzufügen zu/öffnen aus der Quell Code Verwaltung](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Fall 1a: Hinzufügen einer Projekt Mappe zur Quell Code Verwaltung

  - Fall 1B: Projekt Mappe aus Quell Code Verwaltung öffnen

  - Fall 1C: Hinzufügen einer Projekt Mappe aus der Quell Code Verwaltung

- [Testbereich 2: Abrufen aus der Quellcodeverwaltung](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Test Bereich 3: Auschecken/rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

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
