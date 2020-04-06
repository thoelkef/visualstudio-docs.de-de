---
title: 'Testbereich 5: Quellsteuerung ändern | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704527"
---
# <a name="test-area-5-change-source-control"></a>Testbereich 5: Ändern der Quellcodeverwaltung
Dieser Quellcodeverwaltungs-Plug-In-Testbereich behandelt das Ändern der Quellcodeverwaltung über den Befehl **Quellcodeverwaltung ändern.**

 Der Befehl **"Quellcodeverwaltung ändern"** bietet vier grundlegende Funktionen für den Benutzer:

- **Binden:**

   Ermöglicht einem Benutzer das Einrichten oder Wiederherstellen einer Quellcodeverwaltungsverknüpfung zwischen einer Projektmappe/einem Projekt und dem Versionsspeicher.

- **Bindung:**

   Entfernt ein Projekt/eine Projektmappe pro Verbindung aus der Quellcodeverwaltung.

- **Verbinden/Trennen:**

  Schaltet den verbundenen oder Offline-Status der gesteuerten Lösung um, die in Bereich 3 behandelt wird. Weitere Informationen finden Sie unter [Testbereich 3: Auschecken/Auschecken rückgängig machen](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Befehlsmenüzugriff
 Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] folgende integrierte Menüpfad für die Entwicklungsumgebung wird in den Testfällen verwendet.

 Quellsteuerung ändern:**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**.

## <a name="test-cases"></a>Testfälle
 Im Folgenden finden Sie spezifische Testfälle für den Testbereich des Befehlstestbereichs **"Quellcodesteuerung ändern".**

### <a name="case-5a-bind"></a>Fall 5a: Bind
 Bind ermöglicht es dem Benutzer, Quellcodeverwaltungsinformationen zu den ausgewählten Projekten und Lösungen hinzuzufügen. Der Benutzer wird in der Regel aufgefordert, ein Projekt in der Quellcodeverwaltung zu identifizieren, dem diese hinzugefügt werden sollen. Der Benutzer kann im Rahmen dieses Vorgangs kein neues Projekt in der Quellcodeverwaltung erstellen (im Gegensatz zu Zur Quellcodeverwaltung hinzufügen).

| Aktion | Testschritte | Erwartete Ergebnisse zur Überprüfung |
| - | - | - |
| An leeren Speicherort binden | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld **Source Control ändern** (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />4. Klicken Sie auf **Bindung auf**.<br />5. Akzeptieren Sie das Warndialogfeld, wenn es angezeigt wird.<br />6. Wählen Sie alle Elemente aus.<br />7. Klicken Sie auf **Binden**.<br />8. Navigieren Sie zu einem leeren Speicherort in einem Quellcodeverwaltungsspeicher.<br />9. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />10. Klicken Sie im Dialogfeld Bestätigung **auf Weiter mit diesen Bindungen.**<br />11. Klicken Sie im Warndialogfeld auf **OK,** wenn es angezeigt wird.<br />12. Checken Sie alles ein. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />13. Offene Lösung von der Quellcodeverwaltung zu einem neuen Standort. | `Result from Step 12:`<br /><br /> Projektmappe und Projekt sind an das neue Ziel im Versionsspeicher gebunden und werden darauf geschrieben.<br /><br /> Projektmappen- und Projektdateien werden eingecheckt.<br /><br /> Die Projekthierarchie des Versionsspeichers stimmt mit der Ordnerhierarchie des Projekts auf dem Datenträger überein.<br /><br /> `Result from Step 13:`<br /><br /> Alle Projektelemente werden heruntergeladen. |
| Binden an einen Speicherort, der mit dem Client synchronisiert ist | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Erstellen Sie ein Duplikat der Projektmappe [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]und des Projekts im Versionsspeicher (Freigeben und Zweigstellen, falls Sie ) verwenden.<br />4. Open **Change Source Control** Dialogfeld (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />5. Entbindern Sie alle.<br />6. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />7. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern** erneut.<br />8. Wählen Sie alle aus.<br />9. Klicken Sie auf **Binden**.<br />10. Navigieren Sie zum verzweigten Speicherort der Projektmappe und des Projekts (ab Schritt 3)<br />11. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />12. Holen Sie sich das Neueste rekursiv für alle Artikel. | Der Dateiinhalt nach dem Abrufen ist derselbe wie vor dem Abrufen. |
| Binden an einen Speicherort, der nicht mit dem Client synchronisiert ist | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Erstellen Sie ein Duplikat der Projektmappe [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]und des Projekts im Versionsspeicher (Freigeben und Zweigstellen, falls Sie ) verwenden.<br />4. Ändern Sie Dateien im verzweigten Projekt im Versionsspeicher.<br />5. Open **Change Source Control** Dialogfeld (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />6. Entbindern Sie alle.<br />7. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />8. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern** erneut.<br />9. Wählen Sie alle aus.<br />10. Klicken Sie auf **Binden**.<br />11. Navigieren Sie zu einem verzweigten Speicherort für Projektmappe und Projekt.<br />12. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />13. Akzeptieren Sie das Dialogfeld Warnsignal, wenn es angezeigt wird.<br />14. Holen Sie sich neueste rekursive für alle Artikel. | Dateien, die in Schritt 4 geändert wurden, werden ebenfalls lokal geändert. |
| Bind-Lösung, die nie unter Quellcodekontrolle stand | 1. Erstellen Sie einen leeren Ordner in der Quellcodeverwaltung.<br />2. Erstellen Sie ein Clientprojekt.<br />3. Öffnen Sie das Dialogfeld **Source Control ändern** (**Datei**, **Quellcodeverwaltung**, **Quellcodeverwaltung ändern**).<br />4. Binden Sie die Lösung an die leere Position in der Quellcodeverwaltung.<br />5. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />6. Klicken Sie im Dialogfeld Bestätigung **auf Weiter mit diesen Bindungen.**<br />7. Klicken Sie im Warndialogfeld auf **OK,** wenn es angezeigt wird. | Die Lösung wird der Quellcodeverwaltung hinzugefügt.<br /><br /> Projektmappe und Projekt sind ausgecheckt. |
| Abbrechen der Bindung | 1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld Quellcodeverwaltung ändern.<br />4. Entbindern Sie alle.<br />5. Klicken Sie auf **OK,** um das Dialogfeld zu schließen. Wenn dieser Schritt erfolgreich ist, fahren Sie mit dem nächsten Schritt fort.<br />6. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern** erneut.<br />7. Binden Sie an einen nicht verwandten Speicherort.<br />8. Klicken Sie auf **Abbrechen**. | `Result from Step 5:`<br /><br /> Die Lösung ist nicht mehr unter Quellcodekontrolle<br /><br /> `Result from Step 8:`<br /><br /> Die Lösung ist immer noch NICHT unter Quellcodeverwaltung. |

### <a name="case-5b-unbind"></a>Fall 5b: Unbind
 Unbind entfernt Quellcodeverwaltungsinformationen aus Projekten und deren Projektmappe. Die betroffenen Projekte und Projektmappen basieren auf einer Mischung aus Benutzerauswahl und wie die Elemente der Quellcodeverwaltung hinzugefügt wurden.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Aufbinden von Projektmappen, die ein Dateisystem oder ein lokales IIS-Webprojekt und ein Clientprojekt enthalten|1. Erstellen Sie ein Dateisystem oder ein lokales IIS-Webprojekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Fügen Sie der Projektmappe ein neues Clientprojekt hinzu.<br />4. Akzeptieren Sie das Auschecken der Lösung, wenn Sie dazu aufgefordert werden.<br />5. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern.**<br />6. Klicken Sie auf **Bindung auf**.<br />7. Klicken Sie auf **OK,** um das Dialogfeld zu schließen.<br />8. Versuchen Sie, Projektmappe, Projekt, Projektmappenelemente, Projektelemente auszuchecken.|Projektmappe und Projekte sind NICHT unter Quellcodeverwaltung.<br /><br /> Menübefehle der Quellcodeverwaltung werden nicht angezeigt.|
|Abbrechen der Bindung|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern.**<br />4. Klicken Sie auf **Alle binden**.<br />5. Klicken Sie auf **Abbrechen**.|Die Lösung befindet sich unter Quellcodeverwaltung.|

### <a name="case-5c-rebind"></a>Fall 5c: Rebind
 Rebind ist einfach eine Kombination aus Unbind und Bindf – der Prozess der Neubindung eines Projekts/einer Projektmappe, die zuvor unter Quellcodeverwaltung stand und nicht gebunden war.

|Aktion|Testschritte|Erwartete Ergebnisse zur Überprüfung|
|------------|----------------|--------------------------------|
|Rebind-Projektmappe und Projekte ohne Schließen des Dialogfelds **Quellcodeverwaltung ändern**|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />3. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern.**<br />4. Klicken Sie auf **Bindung auf**.<br />5. Wählen Sie alle Zeilen aus.<br />6. Klicken Sie auf **Binden**.<br />7. Klicken Sie auf **OK,** um das Dialogfeld **Quellcodeverwaltung ändern** zu schließen.<br />8. Akzeptieren Sie das Auschecken, wenn Sie dazu aufgefordert werden.|Projektmappe und Projekt stehen unter Quellcodeverwaltung.|
|Rebind-Projekt nur ohne Schließen des Dialogfelds **Quellcodesteuerung ändern**|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie das Projekt nur der Quellcodeverwaltung hinzu (Datei->-Quellcode->Ausgewählte Projekte zur Quellcodeverwaltung hinzufügen.<br />3. Öffnen Sie das Dialogfeld Quellcodeverwaltung ändern.<br />4. Entbinden Sie nur das Projekt.<br />5. Binden Sie nur das Projekt.|Die Lösung bleibt unkontrolliert.<br /><br /> Das Projekt bleibt unter Kontrolle.|
|Rebind-Lösung nur ohne Schließen des Dialogfelds **"Quellcodeverwaltung ändern"**|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie der Quellcodeverwaltung nur die Lösung hinzu, indem Sie (**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung**hinzufügen .<br />3. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern.**<br />4. Entbinden Sie nur die Lösung (Schließen Sie das Dialogfeld **Quellcodeverwaltung** ändern nicht.)<br />5. Binden Sie nur die Lösung.<br />6. Klicken Sie auf **OK,** um das Dialogfeld zu schließen.<br />7. Prüfen Sie Lösungs- und Lösungselemente (falls vorhanden)|Die Lösung bleibt unter Kontrolle.<br /><br /> Das Projekt bleibt unkontrolliert.|
|Rebind-Projektmappe/-projekt nur im selben Verzeichnis|1. Erstellen Sie ein Projekt.<br />2. Fügen Sie nur das Projekt zur Quellcodeverwaltung hinzu, indem Sie (**Datei**, **Quellcodeverwaltung**, **Ausgewählte Projekte zur Quellcodeverwaltung**hinzufügen .<br />3. Schließen Sie die Lösung.<br />4. Erstellen Sie eine neue Lösung mit mindestens zwei Projekten.<br />5. Fügen Sie die Lösung zur Quellcodeverwaltung hinzu.<br />6. Fügen Sie das in Schritt 1 erstellte Projekt aus der Quellcodeverwaltung hinzu.<br />7. Akzeptieren Sie das Auschecken der Lösung, wenn Sie dazu aufgefordert werden.<br />8. Überprüfen Sie die gesamte Lösung.<br />9. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern.**<br />10. Wählen Sie das hinzugefügte Projekt (aus Schritt 6) aus und klicken Sie auf **Bindung**auf .<br />11. Klicken Sie auf **OK,** um das Dialogfeld zu schließen.<br />12. Akzeptieren Sie die Kasse, wenn Sie dazu aufgefordert werden.<br />13. Öffnen Sie das Dialogfeld **Quellcodeverwaltung ändern** erneut.<br />14. Wählen Sie das hinzugefügte Projekt (aus Schritt 6) und klicken Sie auf **Binden**.<br />15. Wählen Sie den ursprünglichen Speicherort aus.|Lösung und Projekte bleiben unter Kontrolle.|

## <a name="see-also"></a>Weitere Informationen
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
