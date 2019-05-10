---
title: 'Testbereich 2: Abrufen aus der Quellcodeverwaltung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d7942aa658208143aea3c3ae3a09eb677568f17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908911"
---
# <a name="test-area-2-get-from-source-control"></a>Testbereich 2: Abrufen aus der Quellcodeverwaltung
Test Hierunter Testfälle für das Abrufen von Elementen aus dem Versionsspeicher über den Get-Befehl. Diese Testfälle können sowohl lokale Pipes und Webprojekte angewendet werden.

## <a name="command-menu-access"></a>Menüzugriff Befehl
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Development-Umgebung im Menüpfade werden verwendet, in den Testfällen.

##### <a name="get-latest-version"></a>Neuste Version abrufen:

- **Datei**, **Quellcodeverwaltung**, **neuste Version abrufen**.

- **Datei**, **neuste Version abrufen**.

- Klicken Sie im Kontextmenü **neuste Version abrufen**.

- Erhalten: **Datei**, **Quellcodeverwaltung**, **erhalten**.

## <a name="expected-behavior"></a>Es wird erwartet

##### <a name="get-latest-version"></a>Neuste Version abrufen:
 Führt im Hintergrund (ohne Benutzeroberfläche) Abruf der neuesten Version des Elements aus dem Versionsspeicher.

##### <a name="get"></a>Erhalten:
 Zeigt die **erhalten** Dialogfeld und ermöglicht dem Benutzer, die den Dateisatz ändern, die abgerufen werden soll und ändern die Optionen, die beeinflussen, wie die Dateien abgerufen werden.

## <a name="test-cases"></a>Testfälle

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Abrufen der neuesten Version einer Datei, die lokal nicht vorhanden ist|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Löschen Sie die lokale Kopie des Elements.<br />5.  Abrufen der neuesten Version des Elements (klicken Sie im Kontextmenü **neuste Version abrufen**).|Elementdatei wird lokal abgerufen.|
|Erhalten Sie eine Datei, die lokal nicht vorhanden ist|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Löschen Sie die lokale Kopie des Elements.<br />5.  Das Element zu erhalten (**Datei**, **Quellcodeverwaltung**, **erhalten** \<Element >).|Elementdatei wird lokal abgerufen.|
|Abrufen einer Datei, die exklusiv ausgecheckt und wurde lokal geändert wurden|1.  Erstellen eines Projekts.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Sehen Sie sich das Projektelement ausschließlich an.<br />5.  Ändern Sie die lokale Kopie.<br />6.  Abrufen der neuesten Version des Elements (**Datei**, **neuste Version abrufen, der** \<Element >). Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />7.  Klicken Sie auf **ersetzen** Schaltfläche im Dialogfeld "Warnung".|**ReResult aus Schritt 6** `:`<br /><br /> Warnungsdialogfeld gibt an, dass die Datei ausgecheckt ist.<br /><br /> **ReResult aus Schritt 7:**<br /><br /> Geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Datei ist Lese-/Schreibzugriff.|
|Abrufen Sie und Ersetzen Sie die Datei, die ausgecheckt wird, freigegeben und wurde lokal geändert.|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Sehen Sie sich das Projektelement als freigegeben.<br />5.  Ändern Sie die lokale Kopie.<br />6.  Abrufen der neuesten Version des Elements (**Datei**, **neuste Version abrufen, der** \<Element >). Wenn dieser Schritt erfolgreich ist, können Sie mit nächsten Schritt fort.<br />7.  Klicken Sie auf **ersetzen** im Dialogfeld "Warnung".|**Führen Sie in Schritt 6:**<br /><br /> Warnungsdialogfeld gibt an, dass die Datei ausgecheckt ist.<br /><br /> **Führen Sie aus Schritt 7:**<br /><br /> Geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Datei ist Lese-/Schreibzugriff.|
|Erhalten Sie eine Datei, die lokal vorhanden ist identisch mit der neuesten Version in den Versionsspeicher|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie dem Projekt ein Element hinzu.<br />3.  Fügen Sie das Projekt unter quellcodeverwaltung.<br />4.  Das Element zu erhalten (**Datei**, **Quellcodeverwaltung**, **erhalten** \<Element >).|Lokale Datei bleibt unverändert.|
|Holen Sie eine Lösung mit einem Projekt|1.  Erstellen Sie eine Projektmappe mit einem Projekt ein.<br />2.  Platzieren Sie die Projektmappe unter quellcodeverwaltung.<br />3.  Löschen Sie alle Projektdateien lokal.<br />4.  Abrufen der Projektmappe (**Datei**, **Quellcodeverwaltung**, **erhalten**).|Alle gelöschte Dateien werden lokal wiederhergestellt werden.|

## <a name="see-also"></a>Siehe auch
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)