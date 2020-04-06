---
title: 'Testbereich 7: Anteil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704408"
---
# <a name="test-area-7-share"></a>Testbereich 7: Freigeben
Dieser Testbereich umfasst die gemeinsame Nutzung von Elementen zwischen Standorten über den Befehl **Freigeben.**

 Ein hhare-Vorgang ist die offensichtliche Duplizierung von Dateien und Ordnerelementen zwischen zwei oder mehr Speicherorten innerhalb einer Quellcodeverwaltungsdateihierarchie. Duplizierung tritt nicht wirklich auf dem Server auf, aber der Benutzer sieht dieselbe Datei an zwei oder mehr angegebenen Speicherorten. Immer wenn Änderungen an einem der freigegebenen Elemente vorgenommen werden, werden diese Änderungen an allen anderen freigegebenen Speicherorten angezeigt.

 Die Freigabe in Ordnern funktioniert, wenn Sie einen Ordner mit mindestens einer Datei auswählen, in der sich die Quellcodeverwaltung befindet. Der Freigabebefehl ist unter den folgenden Bedingungen deaktiviert:

- Wenn der ausgewählte Ordner ein leerer Ordner ist.

- Wenn es einen echten Ordner gibt, dieser jedoch keine Quellcodeverwaltungsdateien enthält.

- Wenn sich ein virtueller Ordner befindet, ob dateienunter Quellcodeverwaltung darin sind oder nicht.

- Wenn ein Remotesite-Webprojekt vorhanden ist.

## <a name="command-menu-access"></a>Befehlsmenüzugriff
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Testfällen werden die folgenden integrierten Menüpfade für Entwicklungsumgebungen verwendet.

 Freigeben:->**Dateiquellcodesteuerungsfreigabe**->**Share**. **File**

## <a name="expected-behavior"></a>Erwartetes Verhalten

- Freigegebene Datei wird am freigegebenen Speicherort angezeigt.

- Wenn Sie den Speicherverlauf der Quellcodeverwaltungsversion anzeigen, wird angezeigt, dass Dateien freigegeben werden.

- Durch Bearbeiten einer freigegebenen Datei werden beide Speicherorte der Datei bearbeitet.

## <a name="test-cases"></a>Testfälle
 Im Folgenden finden Sie spezifische Testfälle für den Share-Testbereich.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Freigeben einer Datei aus einem geladenen Projekt unter Quellcodeverwaltung für ein anderes geladenes Projekt|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie der Projektmappe ein zweites Projekt hinzu.<br />3. Erstellen Sie eine Datei im zweiten Projekt mit einem Namen, der sich nicht im ersten Projekt befindet.<br />4. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />5. Wählen Sie das erste Projekt aus.<br />6. Öffnen Sie **das Dialogfeld Freigabe** (**Datei-Quellcodeverwaltungsfreigabe** -> **Share****File** -> ).<br />7. Teilen Sie die Datei vom zweiten Projekt bis zum ersten Projekt.<br />8. Akzeptieren Sie **auschecken,** wenn Sie dazu aufgefordert werden.|Häufiges erwartetes Verhalten.|
|Freigeben einer Datei von einem Projekt für ein anderes|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie es der Quellcodeverwaltung hinzu.<br />3. Schließen Sie die Lösung.<br />4. Erstellen Sie ein zweites Projekt (neue Lösung).)<br />5. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />6. Wählen Sie das Projekt aus.<br />7. Öffnen Sie das **Dialogfeld Freigeben** ( -> **Datei-Quellcodeverwaltungsfreigabe** -> **Share**).**File**<br />8. Teilen Sie eine Datei aus dem zuvor hinzugefügten Projekt für das geöffnete Projekt.<br />9. Akzeptieren Sie **auschecken,** wenn Sie dazu aufgefordert werden.|Häufiges erwartetes Verhalten.|
|Freigeben einer Datei, die nicht Teil des Projekts ist, aus der Quellcodeverwaltung für das aktuell geladene Projekt|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Fügen Sie eine Datei zur Quellcodeverwaltung hinzu, die nicht Teil des Projekts oder der Projektmappe ist.<br />4. Wählen Sie das Projekt aus und öffnen Sie das **Dialogfeld Freigeben** ( -> **Dateiquellcodefreigabe** -> **Share**).**File**<br />5. Wählen Sie im Dialogfeld **Freigabe** eine Datei aus, die nicht im aktuellen Projekt oder in der aktuellen Projektmappe vorhanden ist, und geben Sie sie gemeinsam.<br />6. Akzeptieren Sie **auschecken,** wenn Sie dazu aufgefordert werden.|Der Quellcodeverwaltungsspeicher hat ein Abrufen durchgeführt, sodass sich die Datei jetzt am lokalen Speicherort des Projekts befindet.|
|Freigeben von Dateien innerhalb desselben Projekts in einem anderen Ordner|1. Wählen Sie **Automatisch auschecken** in **Tools** -> **Options** -> Source**Control**.<br />2. Erstellen Sie ein neues Projekt und fügen Sie es der Quellcodeverwaltung hinzu.<br />3. Fügen Sie dem Projekt einen Ordner hinzu.<br />4. Fügen Sie dem Ordner eine Datei hinzu und checken Sie den Ordner ein.<br />5. Wählen Sie den Ordner aus.<br />6. Öffnen Sie **das Dialogfeld Freigabe** (**Datei-Quellcodeverwaltungsfreigabe** -> **Share****File** -> ).<br />7. Freigeben der Datei für den ausgewählten Ordner.|Häufiges erwartetes Verhalten.<br /><br /> Der Ordner muss mit einer Datei eingecheckt werden, bevor er für die Freigabe verwendet werden kann.|
|Freigeben eines Ordners für das geladene Projekt – Rekursiv|1. Erstellen Sie ein neues Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Wählen Sie das Projekt aus.<br />4. Öffnen Sie das **Dialogfeld Freigeben** ( -> **Datei-Quellcodeverwaltungsfreigabe** -> **Share**).**File**<br />5. Wählen Sie einen Ordner aus.<br />6. Geben Sie den Ordner rekursiv in das Projekt ein.|Häufiges erwartetes Verhalten.|
|Freigeben mehrerer Dateien von einem Projekt für ein anderes|1. Erstellen Sie ein neues Projekt mit mehreren Dateien darin.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Schließen Sie die Lösung.<br />4. Erstellen Sie ein neues Projekt in einer neuen Projektmappe.<br />5. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />6. Wählen Sie das Projekt aus.<br />7. Öffnen Sie das **Dialogfeld Freigeben** ( -> **Datei-Quellcodeverwaltungsfreigabe** -> **Share**).**File**<br />8. Teilen Sie mehrere Dateien aus dem zuvor erstellten Projekt für das aktuell geöffnete Projekt.|Häufiges erwartetes Verhalten.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
