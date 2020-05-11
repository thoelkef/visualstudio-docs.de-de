---
title: 'Testbereich 6: Löschen | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704513"
---
# <a name="test-area-6-delete"></a>Testbereich 6: Löschen
Dieser Quellsteuerungs-Plug-In-Testbereich umfasst Löschaktionen.

 Die Quellcodeverwaltung reagiert auf Löschaktionen im **Projektmappen-Explorer**.

 Im Folgenden finden Sie eine Liste der Elemente, die gelöscht werden können:

- Dateien

- Ordner

- Project

  Je nach Projekttyp haben Sie möglicherweise die Möglichkeit, das Projekt zu **entfernen** (die Dateien auf dem Datenträger zu belassen) oder das Projekt zu **löschen** (entfernt die Dateien auf dem Datenträger). Entweder die Aktion entfernt das Projekt oder Element aus dem **Projektmappen-Explorer**.

## <a name="expected-behavior"></a>Erwartetes Verhalten
 Das erwartete Verhalten für die Testfälle im Löschtestbereich lautet:

- Gelöschtes Element ist im **Projektmappen-Explorer**nicht mehr sichtbar.

- Das übergeordnete Element des gelöschten Projekts oder Elements wird nach Bedarf ausgecheckt (möglicherweise mit einer Eingabeaufforderung).

- Nachdem Sie ein ausgechecktes oder hinzugefügtes Element gelöscht haben, wird es NICHT im Fenster **Ausstehende Eincheckvorgänge** angezeigt.

- Das Element ist auch nach dem Löschen noch im Quellcodeverwaltungsspeicher vorhanden und muss manuell gelöscht werden.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Löschen eines Clientprojekts|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Entfernen Sie das gesamte Projekt aus der Projektmappe|Häufiges erwartetes Verhalten.|
|Löschen einer leeren Datei|1. Erstellen Sie ein Clientprojekt.<br />2. Fügen Sie dem Projekt eine Nullbytedatei hinzu.<br />3. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />4. Wählen Sie die Datei aus, löschen Sie sie.|Häufiges erwartetes Verhalten.|
|Löschen eines Ordners mit einer Datei|1. Erstellen Sie eine einzelne Projektlösung.<br />2. Fügen Sie einen Ordner hinzu.<br />3. Fügen Sie dem Ordner eine Datei hinzu.<br />4. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />5. Schauen Sie sich das Projekt an, um Eingabeaufforderungen zu vermeiden.<br />6. Löschen Sie den Ordner.|Häufiges erwartetes Verhalten.|
|Löschen eines File System-Webprojekts|1. Erstellen Sie ein Dateisystem-Webprojekt (verwenden Sie die Schaltfläche Durchsuchen, um einen UNC-Pfad anzugeben).<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Entfernen Sie das gesamte Projekt aus der Projektmappe.<br />4. Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt (führt verschiedene Pfade durch den Code aus, hat aber die gleiche externe Schnittstelle und das gleiche Verhalten).|Häufiges erwartetes Verhalten.|
|Löschen einer Datei aus einem Dateisystemwebprojekt|1. Erstellen Sie ein File System-Webprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Löschen Sie eine Datei aus dem Projekt.<br />4. Wiederholen Sie die Schritte 1 bis 3 für ein lokales Webprojekt (führt verschiedene Pfade durch den Code aus, hat aber die gleiche externe Schnittstelle und das gleiche Verhalten).|Häufiges erwartetes Verhalten.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
