---
title: Allgemeine Aufgaben in Office-Programmierung
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 085ed1a4f430be957d96991798458e411bc22992
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672807"
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
  
-   [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
-   [Gewusst wie: Upgrade von Office-Projektmappen](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e).  
  
-   [Gewusst wie: Installieren von Office primary interop-Assemblys](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [Gewusst wie: Target Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [Gewusst wie: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
-   [Gewusst wie: Öffnen Office-Projektmappen ohne Ausführen von Code](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [Gewusst wie: Einrichten von Konfigurationsinformationen für eine Office-Projektmappe](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [Gewusst wie: Anzeigen der Registerkarte "Entwickler" auf dem Menüband](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [Gewusst wie: Anzeigen-Add-in-Benutzeroberflächenfehler](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> Aufgaben zur Anpassung der Benutzeroberfläche  
  
### <a name="controls-on-documents-and-worksheets"></a>Steuerelemente in Dokumenten und Arbeitsblättern  
  
-   [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Gewusst wie: Hinzufügen von NamedRange-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [Gewusst wie: Hinzufügen von ListObject-Steuerelementen zu Arbeitsblättern](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Gewusst wie: Hinzufügen von Inhalt von Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [Gewusst wie: Hinzufügen von Lesezeichen-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### <a name="task-panes-in-document-level-customizations"></a>Aufgabenbereiche in Anpassungen auf Dokumentebene  
  
-   [Gewusst wie: Hinzufügen eines Aktionsbereichs zu Word-Dokumenten oder Excel-Arbeitsmappen](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
### <a name="task-panes-in-vsto-add-ins"></a>Aufgabenbereiche in VSTO-Add-ins  
  
-   [Gewusst wie: Hinzufügen ein benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="ribbon-customizations"></a>Menübandanpassungen  
  
-   [Gewusst wie: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [Gewusst wie: Ändern der Position einer Registerkarte des Menübands](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
-   [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
-   [Vorgehensweise: Exportieren eines Menübands aus dem Menüband-Designer in Menüband-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="outlook-form-regions"></a>Outlook-Formularbereiche  
  
-   [Gewusst wie: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### <a name="custom-menus"></a>Benutzerdefinierte Menüs  
  
-   [Gewusst wie: Hinzufügen von Befehlen zu Kontextmenüs](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
##  <a name="excel"></a> Excel-Automatisierungsaufgaben  
  
-   [Gewusst wie: Programmgesteuertes Anzeigen einer Zeichenfolge in eine Zelle eines Arbeitsblatts](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).  
  
-   [Gewusst wie: Programmgesteuertes Erstellen neuer Arbeitsmappen](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Öffnen von Arbeitsmappen](../vsto/how-to-programmatically-open-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Speichern von Arbeitsmappen](../vsto/how-to-programmatically-save-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Schließen von Arbeitsmappen](../vsto/how-to-programmatically-close-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Hinzufügen neuer Arbeitsblätter zu Arbeitsmappen](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Ausblenden von Arbeitsblättern](../vsto/how-to-programmatically-hide-worksheets.md).  
  
-   [Gewusst wie: Programmgesteuertes Verschieben von Arbeitsblättern in Arbeitsmappen](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Schützen von Arbeitsmappen](../vsto/how-to-programmatically-protect-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Verweisen auf Arbeitsblattbereiche im Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).  
  
-   [Gewusst wie: Programmgesteuertes Anwenden von Formaten auf Bereiche in Arbeitsmappen](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).  
  
-   [Gewusst wie: Programmgesteuertes Ändern der Formatierung in Arbeitsblattzeilen, die ausgewählte Zellen enthalten](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).  
  
-   [Gewusst wie: Programmgesteuertes Suchen nach Text in Arbeitsblattbereichen](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).  
  
-   [Gewusst wie: Programmgesteuertes Drucken von Arbeitsblättern](../vsto/how-to-programmatically-print-worksheets.md).  
  
-   [Gewusst wie: Programmgesteuertes Ausführen von Excel-Berechnungen](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).  
  
-   [Gewusst wie: Programmgesteuertes Sortieren von Daten in Arbeitsblättern](../vsto/how-to-programmatically-sort-data-in-worksheets.md).  
  
##  <a name="word"></a> Word-Automatisierungsaufgaben  
  
-   [Gewusst wie: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Öffnen vorhandener Dokumente](../vsto/how-to-programmatically-open-existing-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Speichern von Dokumenten](../vsto/how-to-programmatically-save-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Schließen von Dokumenten](../vsto/how-to-programmatically-close-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Formatieren von Text in Dokumenten](../vsto/how-to-programmatically-format-text-in-documents.md).  
  
-   [Gewusst wie: Hinzufügen von XMLNode-Steuerelementen zu Word-Dokumenten](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Aktualisieren von Lesezeichentext](../vsto/how-to-programmatically-update-bookmark-text.md).  
  
-   [Gewusst wie: Programmgesteuertes suchen und Ersetzen von Text in Dokumenten](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Drucken von Dokumenten](../vsto/how-to-programmatically-print-documents.md).  
  
-   [Gewusst wie: Programmgesteuertes Erstellen von Word-Tabellen](../vsto/how-to-programmatically-create-word-tables.md).  
  
-   [Gewusst wie: Programmgesteuertes Hinzufügen von Zeilen und Spalten zu Word-Tabellen](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).  
  
-   [Gewusst wie: Programmgesteuertes zählen von Zeichen in Dokumenten](../vsto/how-to-programmatically-count-characters-in-documents.md).  
  
##  <a name="data"></a> Datenaufgaben  
  
### <a name="data-bound-controls"></a>Datengebundene Steuerelemente  
  
-   [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### <a name="cached-data-in-document-level-solutions"></a>Zwischengespeicherte Daten in Projektmappen auf Anwendungsebene  
  
-   [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [Gewusst wie: Programmgesteuertes Zwischenspeichern von Datenquellen in einem Office-Dokument](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [Vorgehensweise: Zwischenspeichern von Daten in einem kennwortgeschützten Dokument](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### <a name="custom-xml-data"></a>Benutzerdefinierte XML-Daten  
  
-   [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Abschnitten zu Anpassungen auf Dokumentebene](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [Gewusst wie: Hinzufügen von benutzerdefinierten XML-Elementen zu Dokumenten mithilfe von VSTO-Add-ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
##  <a name="server"></a> Serverseitige Dokumentverwaltungsaufgaben  
  
-   [Gewusst wie: Entfernen Sie Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).  
  
-   [Gewusst wie: Anfügen Erweiterungen durch verwalteten Code zu Dokumenten](../vsto/how-to-attach-managed-code-extensions-to-documents.md).  
  
##  <a name="security"></a> Sicherheitsaufgaben  
  
-   [Gewusst wie: Signieren von Office-Projektmappen](../vsto/how-to-sign-office-solutions.md).  
  
##  <a name="deployment"></a> Bereitstellungsaufgaben  
  
-   [Gewusst wie: Veröffentlichen einer Office-Projektmappe mit ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
-   [Gewusst wie: Veröffentlichen einer Office-Projektmappe auf Dokumentebene auf einem SharePoint Server mithilfe von ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
-   [Gewusst wie: Installieren einer ClickOnce-Office-Projektmappe](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065).  
  
-   [Gewusst wie: Installieren der erforderlichen Komponenten auf Endbenutzercomputern zum Ausführen von Office-Projektmappen](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
-   [Gewusst wie: Vorbereiten von IIS für die Bereitstellung von Office-Projektmappen](https://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4).  
  
-   [Gewusst wie: Update bereitgestellt, Office-Projektmappen](https://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13).  
  
-   [Gewusst wie: Ändern des Installationspfads einer Office-Projektmappe](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Verfügbare Funktionen nach Office-Anwendung und Projekt geben.](../vsto/features-available-by-office-application-and-project-type.md)   
 [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md)  
  
  