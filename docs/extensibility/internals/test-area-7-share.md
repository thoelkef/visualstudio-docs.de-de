---
title: 'Testbereich 7: Freigabe | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ca75f06a72cf3da9dcbbd97ad6559772928152d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596853"
---
# <a name="test-area-7-share"></a>Testbereich 7: Freigeben
Test Hierunter Freigabe Elemente zwischen den Standorten über die **Freigabe** Befehl.

 Ein Vorgang Hhare ist offensichtlich Duplikate von Dateien und von Ordnerelementen zwischen zwei oder mehr Standorte in einer Quellhierarchie für Steuerelement-Datei. Duplizierung erfolgt tatsächlich nicht auf dem Server, jedoch wird die gleiche Datei im angegebenen Speicherorten von zwei oder mehr angezeigt. Wenn keines der gemeinsam genutzten Elemente geändert werden, werden diese Änderungen an allen anderen freigegebenen Speicherorten angezeigt.

 Freigabe in Ordnern funktioniert, wenn Sie einen Ordner mit mindestens einer Datei unter quellcodeverwaltung darin auswählen. Der Befehl "freigeben" ist deaktiviert, in den folgenden Situationen:

-   Wenn der ausgewählte Ordner einen leeren Ordner ist.

-   Wenn ein echter Ordner vorhanden ist, aber es wurden keine Quelldateien-Steuerelement enthält.

-   Ist ein virtueller Ordner, sind oder nicht Dateien unter quellcodeverwaltung gibt an, ob es ein.

-   Wenn es ein Remote-Website-Web-Projekt ist.

## <a name="command-menu-access"></a>Menüzugriff Befehl
 Die folgenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Development-Umgebung im Menüpfade werden verwendet, in den Testfällen.

 Freigeben: **Datei**->**Quellcodeverwaltung**->**Freigabe**.

## <a name="expected-behavior"></a>Es wird erwartet

-   Freigegebene Datei wird im freigegebenen Speicherort angezeigt.

-   Zeigen die Datenquellen-Steuerelement Version Store Verlauf zeigt, dass Dateien freigegeben werden.

-   Bearbeiten einer freigegebenen Datei bearbeitet beide Speicherorte der Datei.

## <a name="test-cases"></a>Testfälle
 Im folgenden finden bestimmte Testfälle für die Freigabe Testbereich.

|Aktion|Testschritte|Erwartete Ergebnisse überprüfen|
|------------|----------------|--------------------------------|
|Freigeben Sie eine Datei aus einem geladenes Projekt unter quellcodeverwaltung zu einem anderen geladenen Projekt|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe ein zweites Projekt hinzu.<br />3.  Erstellen Sie eine Datei in das zweite Projekt mit einem Namen, der nicht in das erste Projekt ist.<br />4.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />5.  Wählen Sie das erste Projekt.<br />6.  Open **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />7.  Die Datei aus dem zweiten Projekt auf das erste Projekt frei.<br />8.  Akzeptieren Sie **Auschecken** Wenn Sie aufgefordert werden.|Allgemeine Erwartetes Verhalten.|
|Freigeben einer Datei in einem Projekt auf einen anderen|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen sie quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie ein zweites Projekt (neue Lösung.)<br />5.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />6.  Wählen Sie das Projekt ein.<br />7.  Öffnen der **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />8.  Eine Datei aus dem zuvor hinzugefügten Projekt auf dem geöffneten Projekt frei.<br />9. Akzeptieren Sie **Auschecken** Wenn Sie aufgefordert werden.|Allgemeine Erwartetes Verhalten.|
|Geben Sie eine Datei nicht Teil des Projekts aus der quellcodeverwaltung in die aktuell geladenes Projekt frei.|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie eine Datei zur quellcodeverwaltung, die nicht Teil des Projekts oder der Projektmappe ist.<br />4.  Wählen Sie das Projekt, und öffnen Sie die **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />5.  Wählen Sie eine Datei innerhalb der **freigeben** Dialogfeld, das nicht in das aktuelle Projekt oder die Lösung vorhanden sein und teilen Sie sie.<br />6.  Akzeptieren Sie **Auschecken** Wenn Sie aufgefordert werden.|Speicher der quellcodeverwaltung hat einen Get, ausgeführt werden, damit die Datei jetzt am lokalen Speicherort des Projekts ist.|
|Freigeben von Dateien im selben Projekt in einen anderen Ordner|1.  Wählen Sie **automatisch Auschecken** in **Tools** -> **Optionen** -> **Quellcodeverwaltung**.<br />2.  Erstellen eines neuen Projekts, und fügen Sie es zur quellcodeverwaltung hinzu.<br />3.  Fügen Sie dem Projekt einen Ordner hinzu.<br />4.  Fügen Sie eine Datei in den Ordner aus, und überprüfen Sie im Ordner "".<br />5.  Wählen Sie den Ordner an.<br />6.  Open **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />7.  Die Datei in den ausgewählten Ordner frei.|Allgemeine Erwartetes Verhalten.<br /><br /> Ordner muss sich eine Datei ausgecheckt werden, bevor sie für die Freigabe verwendet werden kann.|
|Freigeben eines Ordners in das Projekt geladen, rekursive|1.  Erstellen Sie ein neues Projekt.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Wählen Sie das Projekt ein.<br />4.  Öffnen der **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />5.  Wählen Sie einen Ordner.<br />6.  Verwenden Sie die Ordner rekursiv in das Projekt ein.|Allgemeine Erwartetes Verhalten.|
|Mehrere Dateien von einem Projekt auf einen anderen zu teilen|1.  Erstellen eines neuen Projekts mit mehreren Dateien.<br />2.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />3.  Schließen Sie die Projektmappe.<br />4.  Erstellen Sie ein neues Projekt in einer neuen Projektmappe ein.<br />5.  Fügen Sie der Projektmappe zur quellcodeverwaltung hinzu.<br />6.  Wählen Sie das Projekt ein.<br />7.  Öffnen der **Freigabe** (Dialogfeld) (**Datei** -> **Quellcodeverwaltung** -> **Freigabe**).<br />8.  Freigeben Sie mehrere Dateien aus dem zuvor erstellten Projekt der aktuell geöffneten Projekt.|Allgemeine Erwartetes Verhalten.|

## <a name="see-also"></a>Siehe auch
- [Testleitfaden für Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)