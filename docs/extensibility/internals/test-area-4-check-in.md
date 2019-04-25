---
title: 'Testbereich 4: Überprüfen Sie die im | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34d988f88787efc2f40b663ef2f22e6273055533
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038711"
---
# <a name="test-area-4-check-in"></a>Testbereich 4: Einchecken
Quellcodeverwaltung-Plug-in Test Hierunter Senden von aktualisierten Elemente in den Versionsspeicher über die **Einchecken** Befehl.

## <a name="command-menu-access"></a>Menüzugriff Befehl
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Development-Umgebung im Menüpfade werden verwendet, in den Testfällen.

##### <a name="check-in"></a>Ankunft:
 **Datei**, **Quellcodeverwaltung**, **Einchecken**.

 **Datei**, **Einchecken**.

 Klicken Sie im Kontextmenü **Einchecken**.

## <a name="common-expected-behavior"></a>Allgemeine erwartet

- Projekte und Dateien, die zu einer Projektmappe oder das Projekt unter quellcodeverwaltung hinzugefügt werden, der **Einchecken** Dialogfeld und der **Anstehende Eincheckvorgänge** Fenster.

- Werden Sie nach der Überprüfung im hinzugefügten Elemente in der quellcodeverwaltung angezeigt.

- Nach der Überprüfung in sind aktualisierte Elemente im Speicher ordnungsgemäß mit Versionen versehen.

## <a name="test-cases"></a>Testfälle
 Im folgenden finden bestimmte Testfälle für den Eincheckvorgang Testbereich.

### <a name="case-4a-modified-items"></a>Groß-/Kleinschreibung 4a: Geänderte Elemente
 Beschreibt die Verwendung der Überprüfung in Aktion um zu eine Datei unter quellcodeverwaltung zu aktualisieren, die geändert wurde.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Ändern Sie eine Textdatei, die ausgecheckt wurde, überprüfen Sie in nur-Datei (**Einchecken** Dialogfeld)|1.  Erstellen eines neuen Projekts mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Sehen Sie sich, und ändern Sie die Textdatei.<br />4.  Checken Sie sich über das Einchecken (Dialogfeld) (**Datei**, **Quellcodeverwaltung**, **Einchecken**).|Allgemeine Erwartetes Verhalten.|
|Ändern Sie eine Textdatei, die ausgecheckt wurde, überprüfen Sie in nur-Datei (**Anstehende Eincheckvorgänge** Fenster)|1.  Erstellen eines neuen Projekts mit einer Textdatei.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Sehen Sie sich, und ändern Sie die Textdatei.<br />4.  Überprüfen Sie die im über die **Anstehende Eincheckvorgänge** Fenster.|Allgemeine Erwartetes Verhalten.|

### <a name="case-4b-adding-files"></a>Groß-/Kleinschreibung 4 b: Hinzufügen von Dateien
 Wenn Sie eine Datei für ein Projekt oder ein Element zu einer Projektmappe hinzufügen, muss das Projekt oder die Lösung auch ändern. Daher wird die übergeordnete Datei ebenfalls ausgecheckt und muss eingecheckt werden können, um das Hinzufügen abgeschlossen.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Fügen Sie eine Textdatei hinzu, und alles einchecken (**Einchecken** Dialogfeld)|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie dem Projekt eine Textdatei.<br />4.  Akzeptieren Sie Auschecken des Projekts, wenn Sie aufgefordert werden.<br />5.  Wählen Sie die Projektmappe in **Projektmappen-Explorer**.<br />6.  Einchecken aus der **Einchecken** Dialogfeld.|Allgemeine Erwartetes Verhalten.|
|Fügen Sie eine Textdatei hinzu, und alles einchecken (**Anstehende Eincheckvorgänge** Fenster)|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie dem Projekt eine Textdatei.<br />4.  Akzeptieren Sie Auschecken des Projekts, wenn Sie aufgefordert werden.<br />5.  Überprüfen Sie in der Lösung von **Anstehende Eincheckvorgänge** Fenster.|Allgemeine erwartet|

### <a name="case-4c-adding-projects"></a>Fall 4c: Hinzufügen von Projekten
 Wenn Sie ein Projekt zu einer Projektmappe hinzufügen möchten, muss die Lösung auch ändern. Daher wird die Projektmappendatei wird auch ausgecheckt und muss eingecheckt werden können, um das Hinzufügen abgeschlossen.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Hinzufügen eines Projekts zu einer leeren Projektmappe unter quellcodeverwaltung (**Einchecken** Dialogfeld)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie ein neues Projekt hinzu.<br />4.  Akzeptieren Sie sehen Sie sich die Lösung, wenn Sie aufgefordert werden.<br />5.  Einchecken aus der **Einchecken** Dialogfeld.|Allgemeine Erwartetes Verhalten.|
|Hinzufügen eines Projekts zu einer leeren Projektmappe unter quellcodeverwaltung (**Anstehende Eincheckvorgänge** Fenster)|1.  Erstellen Sie eine leere Projektmappe.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie ein neues Projekt hinzu.<br />4.  Akzeptieren Sie sehen Sie sich die Lösung, wenn Sie aufgefordert werden.<br />5.  Überprüfen Sie in der Lösung von **Anstehende Eincheckvorgänge** Fenster.|Allgemeine Erwartetes Verhalten.|

## <a name="see-also"></a>Siehe auch
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)