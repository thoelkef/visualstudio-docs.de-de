---
title: 'Test Bereich 4: Einchecken | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9144bf3aa677a2478bce81634d22d6446e77626b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722519"
---
# <a name="test-area-4-check-in"></a>Testbereich 4: Einchecken
Dieser Testbereich des Quell Code Verwaltungs-Plug-ins umfasst das Senden aktualisierter Elemente an den Versionsspeicher über den Befehl **Einchecken** .

## <a name="command-menu-access"></a>Befehlsmenü Zugriff
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung-Menü Pfade werden in den Testfällen verwendet.

##### <a name="check-in"></a>Ankunft:
 **Datei**, **Quell**Code Verwaltung, **Einchecken**.

 **Datei**, **Einchecken**.

 Eincheck KontextMenü.

## <a name="common-expected-behavior"></a>Häufiges erwartetes Verhalten

- Projekte und Dateien, die einer Projekt Mappe oder einem Projekt unter Quell Code Verwaltung hinzugefügt wurden, werden im Dialogfeld **Einchecken** und im Fenster **ansteh** Ende Eincheck Vorgänge angezeigt.

- Nach dem Einchecken werden hinzugefügte Elemente in der Quell Code Verwaltung angezeigt.

- Nach dem Einchecken werden aktualisierte Elemente ordnungsgemäß im Speicher gespeichert.

## <a name="test-cases"></a>Testfälle
 Im folgenden finden Sie spezifische Testfälle für den Check-in-Testbereich.

### <a name="case-4a-modified-items"></a>Fall 4a: geänderte Elemente
 Beschreibt die Verwendung der Check-in-Aktion zum Aktualisieren einer Datei in der Quell Code Verwaltung, die geändert wurde.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Ändern einer ausgecheckten Textdatei, Einchecken von Dateien (Dialogfeld**Einchecken** )|1. Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. sehen Sie sich die Textdatei an, und ändern Sie Sie.<br />4. checken Sie über das Dialogfeld "Einchecken" ein (**Datei**, **Quell**Code Verwaltung, **Einchecken**).|Häufiges erwartetes Verhalten.|
|Ändern einer ausgecheckten Textdatei, Einchecken von Dateien (Fenster "**ausstehende Eincheck** Vorgänge")|1. Erstellen Sie ein neues Projekt mit einer Textdatei.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. sehen Sie sich die Textdatei an, und ändern Sie Sie.<br />4. checken Sie über das Fenster **ausstehende Eincheck** Vorgänge ein.|Häufiges erwartetes Verhalten.|

### <a name="case-4b-adding-files"></a>Fall 4B: Hinzufügen von Dateien
 Beim Hinzufügen einer Datei zu einem Projekt oder einem Element zu einer Projekt Mappe muss das Projekt oder die Projekt Mappe ebenfalls geändert werden. Daher wird auch die übergeordnete Datei ausgecheckt und muss eingecheckt werden, um die Addition abzuschließen.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Fügen Sie eine Textdatei hinzu, und checken Sie alles ein (**Einchecken** -Dialogfeld).|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Fügen Sie dem Projekt eine Textdatei hinzu.<br />4. akzeptieren Sie das Projekt Auschecken, wenn Sie dazu aufgefordert werden.<br />5. Wählen Sie die Projekt Mappe in **Projektmappen-Explorer**aus.<br />6. checken Sie im Dialogfeld **Einchecken** ein.|Häufiges erwartetes Verhalten.|
|Textdatei hinzufügen und alles einchecken (Fenster**ausstehende Eincheck** Vorgänge)|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Fügen Sie dem Projekt eine Textdatei hinzu.<br />4. akzeptieren Sie das Projekt Auschecken, wenn Sie dazu aufgefordert werden.<br />5. checken Sie die Projekt Mappe aus dem Fenster **ausstehende Eincheck** Vorgänge ein.|Häufiges erwartetes Verhalten|

### <a name="case-4c-adding-projects"></a>Fall 4C: Hinzufügen von Projekten
 Wenn Sie einer Projekt Mappe ein Projekt hinzufügen, muss die Projekt Mappe ebenfalls geändert werden. Daher wird die Projektmappendatei ebenfalls ausgecheckt und muss eingecheckt werden, um die Addition abzuschließen.

|Aktion|Test Schritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Hinzufügen eines Projekts zu einer leeren Projekt Mappe unter Quell Code Verwaltung (Dialogfeld**Einchecken** )|1. Erstellen Sie eine leere Projekt Mappe.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Fügen Sie ein neues Projekt hinzu.<br />4. Wenn Sie dazu aufgefordert werden, sollten Sie die Lösung Auschecken.<br />5. checken Sie im Dialogfeld **Einchecken** ein.|Häufiges erwartetes Verhalten.|
|Hinzufügen eines Projekts zu einer leeren Projekt Mappe unter Quell Code Verwaltung (Fenster**ausstehende Eincheck** Vorgänge)|1. Erstellen Sie eine leere Projekt Mappe.<br />2. Fügen Sie die Projekt Mappe der Quell Code Verwaltung hinzu.<br />3. Fügen Sie ein neues Projekt hinzu.<br />4. Wenn Sie dazu aufgefordert werden, sollten Sie die Lösung Auschecken.<br />5. checken Sie die Projekt Mappe aus dem Fenster **ausstehende Eincheck** Vorgänge ein.|Häufiges erwartetes Verhalten.|

## <a name="see-also"></a>Siehe auch
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)