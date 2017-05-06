---
title: "Gewusst wie: Erstellen von Office-Projekten in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.SelectDocWizard.Page1"
  - "VST.SelectDocWizard.Http"
  - "VST.SelectDocWizard.Extension"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Add-Ins [Office-Entwicklung in Visual Studio], Erstellen von Projekten"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Erstellen von Projekten"
  - "Anpassungen auf Dokumentebene [Office-Entwicklung in Visual Studio], Erstellen"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Erstellen"
  - "Office-Projekte [Office-Entwicklung in Visual Studio]"
  - "Projekte [Office-Entwicklung in Visual Studio], Erstellen"
ms.assetid: 0037dbd8-0d2a-4766-90ea-81c819379582
caps.latest.revision: 96
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 95
---
# Gewusst wie: Erstellen von Office-Projekten in Visual Studio
  Sie können mit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Anpassungen auf VSTO\-Add\-In\- und Dokumentebene für Microsoft Office\-Anwendungen erstellen. Weitere Informationen zu diesen Projekttypen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### So erstellen Sie ein VSTO\-Add\-In\-Projekt  
  
1.  Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt** aus.  Wenn die integrierte Entwicklungsumgebung \(IDE\) für [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Entwicklungseinstellungen konfiguriert ist, wählen Sie im Menü **Datei** die Optionen **Neu** und **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
    > [!NOTE]  
    >  Standardmäßig wird für Office\-Projekte [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] als Ziel festgelegt.  Weitere Informationen finden Sie in der [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
2.  Erweitern Sie im Vorlagenbereich unter dem Knoten für die Sprache, die Sie verwenden möchten, die Option **Office\/SharePoint**.  
  
3.  Wählen Sie den Knoten **Office\-Add\-Ins** aus.  
  
4.  Wählen Sie in der Liste der Projektvorlagen eine VSTO\-Add\-In\-Projektvorlage aus.  Eine Liste verfügbarer VSTO\-Add\-In\-Projektvorlagen finden Sie in der [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Wenn Projektvorlagen beim Auswählen des Knotens **Office\-Add\-Ins** nicht sichtbar sind, stellen Sie sicher, dass **.NET Framework 4** oder höher im Kombinationsfeld am oberen Rand des Dialogfelds ausgewählt ist.  Office\-Projektvorlagen sind für beide .NET Framework\-Versionen sichtbar.  
  
5.  Geben Sie im Feld **Name** einen Namen für das Projekt ein.  Dieser Projektname wird standardmäßig auch für die Projektmappenname verwendet.  
  
6.  Geben Sie im Feld **Speicherort** den Pfad ein, an dem Sie das Projekt erstellen möchten.  Sie können absolute und UNC\-Pfade \(Universal Naming Convention\) verwenden.  Verwenden Sie keinen HTTP\-, FTP\- oder sonstigen Protokollpfad.  
  
     Die Speicherorte haben die folgende Formate:  
  
    -   \[*Laufwerk*\]:\\  
  
    -   \\\\*Server*\\*Freigeben*  
  
     Verwenden Sie in der Pfadangabe keine der folgenden Zeichen:  
  
    -   Sternchen \(\*\)  
  
    -   Senkrechter Strich \(|\)  
  
    -   Doppelpunkt \(:\) \(außer nach dem Laufwerkbuchstaben\)  
  
    -   Anführungszeichen \("\) \(bei Pfaden mit Leerzeichen sind keine Anführungszeichen erforderlich\)  
  
    -   Kleiner als \(\<\)  
  
    -   Größer als \(\>\)  
  
    -   Fragezeichen \(?\)  
  
    -   Prozentzeichen \(%\)  
  
7.  Klicken Sie auf die Schaltfläche **OK**.  
  
    > [!NOTE]  
    >  Add\-In\-Projekte werden immer gespeichert, wenn sie erstellt werden.  Sie können nicht als temporäre Projekte erstellt werden.  Weitere Informationen zu temporären Projekten finden Sie unter [Temporäre Projekte](http://msdn.microsoft.com/de-de/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### So erstellen Sie ein Projekt für Anpassungen auf Dokumentebene  
  
1.  Wählen Sie im Menü **Datei** die Optionsfolge **Neu**, **Projekt** aus.  Wenn die IDE auf die Verwendung der Visual Basic\-Entwicklungseinstellungen festgelegt ist, wählen Sie im Menü **Datei** die Optionen **Neu** und **Projekt** aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
    > [!NOTE]  
    >  Standardmäßig wird für Office\-Projekte [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] als Ziel festgelegt.  Weitere Informationen finden Sie in der [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
2.  Erweitern Sie im Vorlagenbereich unter dem Knoten für die Sprache, die Sie verwenden möchten, die Option **Office\/SharePoint**.  
  
3.  Wählen Sie den Knoten **Office\-Add\-Ins** aus.  
  
4.  Wählen Sie in der Liste der Projektvorlagen eine Projektvorlage auf Dokumentebene aus.  Eine Liste der verfügbaren Projektvorlagen auf Dokumentebene finden Sie in der [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Wenn Projektvorlagen beim Auswählen des Knotens **Office\-Add\-Ins** nicht sichtbar sind, stellen Sie sicher, dass **.NET Framework 4** oder höher im Kombinationsfeld am oberen Rand des Dialogfelds ausgewählt ist.  Office\-Projektvorlagen sind für beide .NET Framework\-Versionen sichtbar.  
  
5.  Geben Sie im Feld **Name** einen Namen für das Projekt ein.  Dieser Name wird standardmäßig auch für das Dokument verwendet.  Falls Sie für die IDE Visual C\#\-Entwicklungseinstellungen oder Allgemeine Entwicklungseinstellungen festgelegt haben, müssen Sie zusätzlich einen Speicherort und einen Projektmappennamen eingeben.  
  
    > [!NOTE]  
    >  Der Pfad des Projektspeicherorts oder der Projektname dürfen keine Ersatzzeichen enthalten.  Informationen über Ersatzzeichen finden Sie unter [NIB: Unicode Support for Surrogate Pairs and Combining Character Sequences](http://msdn.microsoft.com/de-de/cba3285c-7b47-4ce8-8970-f48d6ac03e39).  Wenn Sie die Projektmappe für die Offlineverwendung bereitstellen möchten, müssen außerdem die Zeichen im Projektnamen den Spezifikationen des HTTP\-Protokolls entsprechen.  
  
6.  Klicken Sie auf die Schaltfläche **OK**.  
  
     Der **Projekt\-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
7.  Wählen Sie **Neues Dokument erstellen** aus, wenn Sie ein neues Dokument für die Projektmappe erstellen möchten. Oder wählen Sie **Vorhandenes Dokument kopieren** aus, wenn Sie ein vorhandenes Dokument anpassen möchten.  
  
     Wenn Sie ein neues Dokument erstellen, geben Sie den Namen im Feld **Name** an, und wählen Sie das Format des Dokuments mithilfe des Felds **Format** aus.  Weitere Informationen über die verfügbaren Formate finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
     Wenn Sie ein vorhandenes Dokument verwenden, geben Sie den Speicherort des Dokuments im Feld **Vollständiger Pfad zum vorhandenen Dokument** an.  Sie können sowohl absolute Pfade als auch UNC\-Pfade verwenden.  Verwenden Sie keinen HTTP\-, FTP\- oder sonstigen Protokollpfad für das Dokument.  
  
     Die Speicherorte haben die folgende Formate:  
  
    -   \[*Laufwerk*\]:\\  
  
    -   \\\\*Server*\\*Freigeben*  
  
     Verwenden Sie in der Pfadangabe keine der folgenden Zeichen:  
  
    -   Sternchen \(\*\)  
  
    -   Senkrechter Strich \(|\)  
  
    -   Doppelpunkt \(:\) \(außer nach dem Laufwerkbuchstaben\)  
  
    -   Anführungszeichen \("\) \(bei Pfaden mit Leerzeichen sind keine Anführungszeichen erforderlich\)  
  
    -   Kleiner als \(\<\)  
  
    -   Größer als \(\>\)  
  
    -   Fragezeichen \(?\)  
  
    -   Prozentzeichen \(%\)  
  
    > [!NOTE]  
    >  Öffnen Sie in einem [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]\-Projekt nur in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] erstellte oder in dieses Format konvertierte Dokumente.  Öffnen Sie entsprechend in einem Word 2010\-Projekt nur in Word 2010 erstellte oder in dieses Format konvertierte Dokumente.  Bestimmte Funktionen werden im Dokument deaktiviert, wenn Sie ein Dokument öffnen, das in einer früheren Word\-Version erstellt wurde.  Wenn Sie Code schreiben, von dem diese Funktionen verwendet werden, können Fehler im Projekt auftreten.  Zum Konvertieren eines Dokuments öffnen Sie es in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder Word 2010, und klicken Sie auf dem Menüband auf die Registerkarte **Datei**. Klicken Sie dann auf **Info** und anschließend auf **Konvertieren**.  
  
8.  Wählen Sie **Fertig stellen** aus.  
  
9. Fügen Sie der Liste von vertrauenswürdigen Speicherorten im Sicherheitscenter in Word in den folgenden Fällen den Projektordner und seine Unterordner hinzu:  
  
    -   Sie erstellen ein Word\-Dokument, das auf einer DOCM\-Datei basiert, und das Dokument enthält ein VBA\-Projekt oder hostet Windows Forms\-Steuerelemente.  Durch Hinzufügen des Projektordners zur Liste der vertrauenswürdigen Speicherorte können Sie sicherstellen, dass das zur Entwurfszeit wie erwartet funktioniert.  
  
    -   Sie erstellen ein Word\-Vorlagenprojekt, das auf einer DOTX\-Datei basiert.  Sie müssen der Liste der vertrauenswürdigen Speicherorte den Projektordner hinzufügen, damit das Projekt ausgeführt und gedebuggt werden kann.  
  
     Weitere Informationen über das Hinzufügen eines Dokuments zu den vertrauenswürdigen Speicherorten finden Sie auf der Microsoft Office\-Website [Erstellen, Entfernen oder Ändern eines vertrauenswürdigen Speicherorts für Ihre Dateien](https://support.office.com/de-de/article/Erstellen-Entfernen-oder-%C3%84ndern-eines-vertrauensw%C3%BCrdigen-Speicherorts-f%C3%BCr-Ihre-Dateien-f5151879-25ea-4998-80a5-4208b3540a62?ui=de-DE&rs=de-DE&ad=DE).  
  
## Siehe auch  
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)   
 [Gemeinsame Entwicklung von Office-Lösungen](../vsto/collaborative-development-of-office-solutions.md)   
 [Entwerfen und Erstellen von Office-Lösungen](../vsto/designing-and-creating-office-solutions.md)   
 [Erste Schritte beim Programmieren von VSTO-Add-Ins](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  