---
title: 'Testbereich 4: Einchecken | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704576"
---
# <a name="test-area-4-check-in"></a>Testbereich 4: Einchecken
Dieser Quellcodeverwaltungs-Plug-In-Testbereich umfasst das Senden aktualisierter Elemente an den Versionsspeicher über den Befehl **Einchecken.**

## <a name="command-menu-access"></a>Befehlsmenüzugriff
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Testfällen werden die folgenden integrierten Menüpfade für Entwicklungsumgebungen verwendet.

##### <a name="check-in"></a>Einchecken:
 **Datei**, **Quellcodeverwaltung**, **Einchecken .**

 **Datei**, **Einchecken in**.

 Shortcut-Menü, **Einchecken**.

## <a name="common-expected-behavior"></a>Häufiges erwartetes Verhalten

- Projekte und Dateien, die einer Projektmappe oder einem Projekt unter Quellcodeverwaltung hinzugefügt wurden, werden im Dialogfeld **Einsehen** und im Fenster **Ausstehende Eincheckungen** angezeigt.

- Nach dem Einchecken werden hinzugefügte Elemente in der Quellcodeverwaltung angezeigt.

- Nach dem Einchecken werden aktualisierte Elemente ordnungsgemäß im Shop versioniert.

## <a name="test-cases"></a>Testfälle
 Im Folgenden finden Sie spezifische Testfälle für den Check-in-Testbereich.

### <a name="case-4a-modified-items"></a>Fall 4a: Geänderte Artikel
 Beschreibt die Verwendung der Eincheckaktion zum Aktualisieren einer Datei unter Quellcodeverwaltung, die geändert wurde.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Ändern einer ausgecheckten Textdatei, Nur Datei einchecken (Dialogfeld**Einchecken)**|1. Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Auschecken und ändern Sie die Textdatei.<br />4. Einchecken über das Dialogfeld Einchecken (**Datei**, **Quellcodeverwaltung**, **Einchecken**).|Häufiges erwartetes Verhalten.|
|Ändern einer ausgecheckten Textdatei, nur Datei einchecken ( Fenster**Ausstehende Eincheckungen)**|1. Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Auschecken und ändern Sie die Textdatei.<br />4. Check-in über das Fenster **Ausstehende Eincheckungen.**|Häufiges erwartetes Verhalten.|

### <a name="case-4b-adding-files"></a>Fall 4b: Hinzufügen von Dateien
 Beim Hinzufügen einer Datei zu einem Projekt oder einem Element zu einer Projektmappe muss sich auch das Projekt oder die Projektmappe ändern. Daher ist auch die übergeordnete Datei ausgecheckt und muss eingecheckt werden, um den Zusatz abzuschließen.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Hinzufügen einer Textdatei und Einchecken von allem (Dialogfeld**Einchecken)**|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Fügen Sie dem Projekt eine Textdatei hinzu.<br />4. Akzeptieren Sie das Auschecken des Projekts, wenn Sie dazu aufgefordert werden.<br />5. Wählen Sie die Projektmappe im **Projektmappen-Explorer**aus.<br />6. Check-in im Dialogfeld **Einchecken.**|Häufiges erwartetes Verhalten.|
|Hinzufügen einer Textdatei und Einchecken von allem (Fenster**Ausstehende Eincheckungen)**|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Fügen Sie dem Projekt eine Textdatei hinzu.<br />4. Akzeptieren Sie das Auschecken des Projekts, wenn Sie dazu aufgefordert werden.<br />5. Einchecken Lösung aus **Ausstehenden Eincheckungen** Fenster.|Häufiges erwartetes Verhalten|

### <a name="case-4c-adding-projects"></a>Fall 4c: Hinzufügen von Projekten
 Beim Hinzufügen eines Projekts zu einer Projektmappe muss sich auch die Projektmappe ändern. Daher ist auch die Lösungsdatei ausgecheckt und muss eingecheckt werden, um den Zusatz abzuschließen.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Hinzufügen eines Projekts zu einer leeren Projektmappe unter Quellcodeverwaltung (Dialogfeld**Einchecken)**|1. Erstellen Sie eine leere Lösung.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Fügen Sie ein neues Projekt hinzu.<br />4. Akzeptieren Sie das Auschecken der Lösung, wenn Sie dazu aufgefordert werden.<br />5. Check-in im Dialogfeld **Einchecken.**|Häufiges erwartetes Verhalten.|
|Hinzufügen eines Projekts zu einer leeren Projektmappe unter Quellcodeverwaltung (Fenster**Ausstehende Eincheckungen)**|1. Erstellen Sie eine leere Lösung.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Fügen Sie ein neues Projekt hinzu.<br />4. Akzeptieren Sie das Auschecken der Lösung, wenn Sie dazu aufgefordert werden.<br />5. Einchecken Lösung aus **Ausstehenden Eincheckungen** Fenster.|Häufiges erwartetes Verhalten.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
