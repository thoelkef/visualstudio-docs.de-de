---
title: Allgemeine Aufgaben in Office-Programmierung
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 234f5c70c05e058cac084780ab2777d9f302834a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911196"
---
# <a name="common-tasks-in-office-programming"></a>Allgemeine Aufgaben in Office-Programmierung
  Dieses Thema soll Ihnen helfen, Antworten auf die folgenden Kategorien häufig gestellter Fragen zum Programmieren von Office-Projektmappen mithilfe von Visual Studio zu finden.  
  
-   [Setup und allgemeine Aufgaben](#projects).  
  
-   [Aufgaben zur Anpassung der Benutzeroberfläche](#ui).  
  
-   [Excel-Automatisierungsaufgaben](#excel).  
  
-   [Word-Automatisierungsaufgaben](#word).  
  
-   [Datenaufgaben](#data).  
  
-   [Serverseitige Dokumentverwaltungsaufgaben](#server).  
  
-   [Sicherheitsaufgaben](#security).  
  
-   [Bereitstellungsaufgaben](#deployment).  
  
##  <a name="projects"></a> Setup und allgemeine Aufgaben  
  
-   [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
-   [Vorgehensweise: Aktualisieren von Office-Projektmappen](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e).  
  
-   [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [Vorgehensweise: Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
-   [Vorgehensweise: Öffnen Sie Office-Projektmappen ohne die Ausführung von Code](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [Vorgehensweise: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [Vorgehensweise: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [Vorgehensweise: Add-In-Benutzeroberflächenfehler anzeigen](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> Aufgaben zur Anpassung der Benutzeroberfläche  
  
### <a name="controls-on-documents-and-worksheets"></a>Steuerelemente in Dokumenten und Arbeitsblättern  
  
-   [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Vorgehensweise: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [Vorgehensweise: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Vorgehensweise: Inhalt hinzufügen von Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [Vorgehensweise: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### <a name="task-panes-in-document-level-customizations"></a>Aufgabenbereiche in Anpassungen auf Dokumentebene  
  
-   [Vorgehensweise: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
### <a name="task-panes-in-vsto-add-ins"></a>Aufgabenbereiche in VSTO-Add-ins  
  
-   [Vorgehensweise: Hinzufügen ein benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="ribbon-customizations"></a>Menübandanpassungen  
  
-   [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [Vorgehensweise: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
-   [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
-   [Vorgehensweise: Exportieren eines Menübands vom Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="outlook-form-regions"></a>Outlook-Formularbereiche  
  
-   [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### <a name="custom-menus"></a>Benutzerdefinierte Menüs  
  
-   [Vorgehensweise: Hinzufügen von Befehlen zu Kontextmenüs](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
##  <a name="excel"></a> Excel-Automatisierungsaufgaben  
  
-   [Vorgehensweise: Programmgesteuertes Anzeigen einer Zeichenfolge in eine Zelle eines Arbeitsblatts](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).  
  
-   [Vorgehensweise: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md).  
  
-   [Vorgehensweise: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).  
  
-   [Vorgehensweise: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).  
  
-   [Vorgehensweise: Programmgesteuertes Ändern der Formatierung in Arbeitsblattzeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).  
  
-   [Vorgehensweise: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).  
  
-   [Vorgehensweise: Programmgesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md).  
  
-   [Vorgehensweise: Programmgesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).  
  
-   [Vorgehensweise: Programmgesteuertes Sortieren von Daten in Arbeitsblättern](../vsto/how-to-programmatically-sort-data-in-worksheets.md).  
  
##  <a name="word"></a> Word-Automatisierungsaufgaben  
  
-   [Vorgehensweise: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Speichern von Dokumenten](../vsto/how-to-programmatically-save-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Formatieren von Text in Dokumenten](../vsto/how-to-programmatically-format-text-in-documents.md).  
  
-   [Vorgehensweise: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Aktualisieren von Lesezeichentext](../vsto/how-to-programmatically-update-bookmark-text.md).  
  
-   [Vorgehensweise: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md).  
  
-   [Vorgehensweise: Programmgesteuertes Erstellen von Word-Tabellen](../vsto/how-to-programmatically-create-word-tables.md).  
  
-   [Vorgehensweise: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).  
  
-   [Vorgehensweise: Programmgesteuertes zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md).  
  
##  <a name="data"></a> Datenaufgaben  
  
### <a name="data-bound-controls"></a>Datengebundene Steuerelemente  
  
-   [Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### <a name="cached-data-in-document-level-solutions"></a>Zwischengespeicherte Daten in Projektmappen auf Anwendungsebene  
  
-   [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [Vorgehensweise: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### <a name="custom-xml-data"></a>Benutzerdefinierte XML-Daten  
  
-   [Vorgehensweise: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [Vorgehensweise: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
##  <a name="server"></a> Serverseitige Dokumentverwaltungsaufgaben  
  
-   [Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).  
  
-   [Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md).  
  
##  <a name="security"></a> Sicherheitsaufgaben  
  
-   [Vorgehensweise: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md).  
  
##  <a name="deployment"></a> Bereitstellungsaufgaben  
  
-   [Vorgehensweise: Veröffentlichen einer Office-Projektmappe mit ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
-   [Vorgehensweise: Veröffentlichen einer Office-Projektmappe auf Dokumentebene auf einem SharePoint Server mithilfe von ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
-   [Vorgehensweise: Installieren einer ClickOnce-Office-Projektmappe](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065).  
  
-   [Vorgehensweise: Installieren der erforderlichen Komponenten auf Endbenutzercomputern zum Ausführen von Office-Projektmappen](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
-   [Vorgehensweise: Vorbereiten von IIS für die Bereitstellung von Office-Projektmappen](https://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4).  
  
-   [Vorgehensweise: Update bereitgestellt, Office-Projektmappen](https://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13).  
  
-   [Vorgehensweise: Ändern des Installationspfads einer Office-Projektmappe](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Verfügbare Funktionen nach Office-Anwendung und Projekt geben.](../vsto/features-available-by-office-application-and-project-type.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)  
