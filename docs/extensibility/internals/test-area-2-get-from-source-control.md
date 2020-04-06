---
title: 'Testbereich 2: Abrufen von der Quellcodeverwaltung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704606"
---
# <a name="test-area-2-get-from-source-control"></a>Testbereich 2: Abrufen aus der Quellcodeverwaltung
Dieser Testbereich umfasst Testfälle zum Abrufen von Elementen aus dem Versionsspeicher über den Befehl Abrufen. Diese Testfälle können sowohl auf lokale als auch auf Webprojekte angewendet werden.

## <a name="command-menu-access"></a>Befehlsmenüzugriff
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Testfällen werden die folgenden integrierten Menüpfade für Entwicklungsumgebungen verwendet.

##### <a name="get-latest-version"></a>Aktuelle Version:

- **Datei**, **Quellcodeverwaltung**, **Abrufen der neuesten Version**.

- **Datei**, **Abrufen der neuesten Version**.

- Shortcut-Menü, **Get Latest Version**.

- Abrufen: **Datei**, **Quellcodeverwaltung**, **Abrufen**.

## <a name="expected-behavior"></a>Erwartetes Verhalten

##### <a name="get-latest-version"></a>Aktuelle Version:
 Führt einen automatischen (keine UI) Abruf der neuesten Version des Elements aus dem Versionsspeicher durch.

##### <a name="get"></a>Get:
 Zeigt das Dialogfeld **Abrufen** an und ermöglicht es dem Benutzer, Änderungen am Dateisatz vorzunehmen, der abgerufen wird, sowie die Optionen zu ändern, die sich auf das Abrufen der Dateien auswirken.

## <a name="test-cases"></a>Testfälle

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Abrufen der neuesten Version einer Datei, die nicht lokal vorhanden ist|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Stellen Sie das Projekt unter Quellcodeverwaltung.<br />4. Löschen Sie die lokale Kopie des Artikels.<br />5. Holen Sie sich die neueste Version des Elements (Shortcut Menu, **Get Latest Version**).|Die Elementdatei wird lokal abgerufen.|
|Abrufen einer Datei, die nicht lokal vorhanden ist|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Stellen Sie das Projekt unter Quellcodeverwaltung.<br />4. Löschen Sie die lokale Kopie des Artikels.<br />5. Holen Sie sich das Element (**Datei**, **Quellcodeverwaltung**, **Holen Sie** \<Artikel>).|Die Elementdatei wird lokal abgerufen.|
|Abrufen einer Datei, die exklusiv ausgecheckt und lokal geändert wurde|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Stellen Sie das Projekt unter Quellcodeverwaltung.<br />4. Schauen Sie sich den Projektartikel exklusiv an.<br />5. Ändern Sie die lokale Kopie.<br />6. Holen Sie sich die neueste Version des Artikels (**Datei**, **Holen Sie sich neueste Version von** \<Element>). Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />7. Klicken Sie im Warndialogfeld auf **Ersetzen.**|**ReResult aus Schritt 6**`:`<br /><br /> Das Dialogfeld "Warnsignal" gibt an, dass die Datei ausgecheckt ist.<br /><br /> **ReResult aus Schritt 7:**<br /><br /> Die geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Die Datei ist Lesen/Schreiben.|
|Abrufen und Ersetzen von Dateien, die lokal ausgecheckt, freigegeben und geändert werden|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Stellen Sie das Projekt unter Quellcodeverwaltung.<br />4. Schauen Sie sich das Projektelement als freigegeben an.<br />5. Ändern Sie die lokale Kopie.<br />6. Holen Sie sich die neueste Version des Artikels (**Datei**, **Holen Sie sich neueste Version von** \<Element>). Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />7. Klicken Sie im Warndialogfeld auf **Ersetzen.**|**Ergebnis aus Schritt 6:**<br /><br /> Das Dialogfeld "Warnsignal" gibt an, dass die Datei ausgecheckt ist.<br /><br /> **Ergebnis aus Schritt 7:**<br /><br /> Die geänderte lokale Datei wird durch die ursprüngliche Version aus dem Versionsspeicher ersetzt.<br /><br /> Die Datei ist Lesen/Schreiben.|
|Abrufen einer Datei, die lokal vorhanden ist, wie die neueste Version im Versionsspeicher|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie dem Projekt ein Element hinzu.<br />3. Stellen Sie das Projekt unter Quellcodeverwaltung.<br />4. Holen Sie sich das Element (**Datei**, **Quellcodeverwaltung**, **Holen Sie** \<Artikel>).|Die lokale Datei ist unverändert.|
|Erhalten Sie eine Lösung mit einem Projekt|1. Erstellen Sie eine Projektmappe mit einem Projekt.<br />2. Stellen Sie die Lösung unter Quellcodeverwaltung.<br />3. Löschen Sie alle Projektdateien lokal.<br />4. Holen Sie sich die Lösung (**Datei**, **Quellcodeverwaltung**, **Get**).|Alle gelöschten Dateien werden lokal wiederhergestellt.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
