---
title: 'Gewusst wie: Erstellen von Office-Projekten in Visual Studio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 06d91a2a9e7dc206e2303637bce013b473cf6560
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839036"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Gewusst wie: Erstellen von Office-Projekten in Visual Studio
  Sie können [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zum Erstellen von VSTO-Add-in und Dokumentebene Anpassungen für Microsoft Office-Anwendungen. Weitere Informationen zu diesen Projekttypen finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>So erstellen Sie ein VSTO-Add-In-Projekt  
  
1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus. Wenn die integrierte Entwicklungsumgebung (IDE) festgelegt ist, verwenden [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] entwicklungseinstellungen auf der **Datei** Menü wählen **neu** > **Projekt**.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
   > [!NOTE]  
   >  Standardmäßig wird für Office-Projekte [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] als Ziel festgelegt. Weitere Informationen finden Sie unter [.NET Framework-Clientprofil](/dotnet/framework/deployment/client-profile).  
  
2. Erweitern Sie im Vorlagenbereich unter dem Knoten für die Sprache, die Sie verwenden möchten, **Office/SharePoint**.  
  
3. Wählen Sie die **Office-Add-ins** Knoten.  
  
4. Wählen Sie in der Liste der Projektvorlagen eine VSTO-Add-In-Projektvorlage aus. Eine Liste der verfügbaren VSTO-Add-in-Projektvorlagen, finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Wenn Projektvorlagen nicht sichtbar sind bei der Auswahl der **Office-Add-ins** Knoten stellen Sie sicher, dass **.NET Framework 4** oder höher im Kombinationsfeld am oberen Rand des Dialogfelds ausgewählt ist. Office-Projektvorlagen sind für beide .NET Framework-Versionen sichtbar.  
  
5. In der **Namen** geben einen Namen für das Projekt. Dieser Projektname wird standardmäßig auch für die Projektmappenname verwendet.  
  
6. In der **Speicherort** Geben Sie den Pfad, in dem Sie das Projekt erstellen möchten. Sie können absolute und UNC-Pfade (Universal Naming Convention) verwenden. Verwenden Sie keinen HTTP-, FTP- oder sonstigen Protokollpfad.  
  
    Die Speicherorte haben die folgende Formate:  
  
   * [*Laufwerk*\]\:  
  
   * \\\\*Server*\\*Freigabe*  
  
     Verwenden Sie in der Pfadangabe keine der folgenden Zeichen:  
  
   * Sternchen (*)  
  
   * Senkrechter Strich (|)  
  
   * Doppelpunkt (:) (außer nach dem Laufwerkbuchstaben)  
  
   * Anführungszeichen (") (bei Pfaden mit Leerzeichen sind keine Anführungszeichen erforderlich)  
  
   * Kleiner als (\<)  
  
   * Größer als (>)  
  
   * Fragezeichen (?)  
  
   * Prozentzeichen (%)  
  
7. Klicken Sie auf die Schaltfläche **OK** .
  
    > [!NOTE]  
    >  Add-In-Projekte werden immer gespeichert, wenn sie erstellt werden. Sie können nicht als temporäre Projekte erstellt werden. Weitere Informationen zu temporären Projekten finden Sie unter [temporäre Projekte](http://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>So erstellen Sie ein Projekt für Anpassungen auf Dokumentebene  
  
1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus. Wenn die IDE festgelegt ist, verwenden Sie Visual Basic-entwicklungseinstellungen auf der **Datei** im Menü wählen **neu** > **Projekt**.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
   > [!NOTE]  
   >  Standardmäßig wird für Office-Projekte [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] als Ziel festgelegt.  Weitere Informationen finden Sie unter [.NET Framework-Clientprofil](/dotnet/framework/deployment/client-profile).  
  
2. Erweitern Sie im Vorlagenbereich unter dem Knoten für die Sprache, die Sie verwenden möchten, **Office/SharePoint**.  
  
3. Wählen Sie den Knoten **Office-Add-Ins** aus.  
  
4. Wählen Sie in der Liste der Projektvorlagen eine Projektvorlage auf Dokumentebene aus. Eine Liste der verfügbaren Projektvorlagen auf Dokumentebene, finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Wenn Projektvorlagen nicht sichtbar sind bei der Auswahl der **Office-Add-ins** Knoten stellen Sie sicher, dass **.NET Framework 4** oder höher im Kombinationsfeld am oberen Rand des Dialogfelds ausgewählt ist. Office-Projektvorlagen sind für beide .NET Framework-Versionen sichtbar.  
  
5. In der **Namen** geben einen Namen für das Projekt. Dieser Name wird standardmäßig auch für das Dokument verwendet. Falls Sie für die IDE Visual C#-Entwicklungseinstellungen oder Allgemeine Entwicklungseinstellungen festgelegt haben, müssen Sie zusätzlich einen Speicherort und einen Projektmappennamen eingeben.  
  
   > [!NOTE]  
   >  Der Pfad des Projektspeicherorts oder der Projektname dürfen keine Ersatzzeichen enthalten. Wenn Sie die Projektmappe für die Offlineverwendung bereitstellen möchten, müssen außerdem die Zeichen im Projektnamen den Spezifikationen des HTTP-Protokolls entsprechen.  
  
6. Klicken Sie auf die Schaltfläche **OK** .  
  
    Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
7. Wählen Sie **ein neues Dokument erstellen** sollten Sie ein neues Dokument für die Projektmappe erstellen, oder wählen Sie **vorhandenes Dokument kopieren** , wenn Sie ein vorhandenes Dokument anpassen möchten.  
  
    Wenn Sie ein neues Dokument erstellen, geben Sie den Namen in der **Namen** Feld, und wählen Sie das Format des Dokuments mithilfe der **Format** Feld. Weitere Informationen über die verfügbaren Formate finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
    Wenn Sie ein vorhandenes Dokument verwenden, geben Sie den Speicherort des Dokuments in der **vollständiger Pfad zum vorhandenen Dokument** Feld. Sie können sowohl absolute Pfade als auch UNC-Pfade verwenden. Verwenden Sie keinen HTTP-, FTP- oder sonstigen Protokollpfad für das Dokument.  
  
    Die Speicherorte haben die folgende Formate:  
  
   - [*Laufwerk*\]\:  
  
   - \\\\*Server*\\*Freigabe*  
  
     Verwenden Sie in der Pfadangabe keine der folgenden Zeichen:  
  
   - Sternchen (*)  
  
   - Senkrechter Strich (|)  
  
   - Doppelpunkt (:) (außer nach dem Laufwerkbuchstaben)  
  
   - Anführungszeichen (") (bei Pfaden mit Leerzeichen sind keine Anführungszeichen erforderlich)  
  
   - Kleiner als (\<)  
  
   - Größer als (>)  
  
   - Fragezeichen (?)  
  
   - Prozentzeichen (%)  
  
   > [!NOTE]  
   >  Öffnen Sie in einem [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]-Projekt nur in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] erstellte oder in dieses Format konvertierte Dokumente. Öffnen Sie entsprechend in einem Word 2010-Projekt nur in Word 2010 erstellte oder in dieses Format konvertierte Dokumente. Bestimmte Funktionen werden im Dokument deaktiviert, wenn Sie ein Dokument öffnen, das in einer früheren Word-Version erstellt wurde. Wenn Sie Code schreiben, von dem diese Funktionen verwendet werden, können Fehler im Projekt auftreten. Zum Konvertieren eines Dokuments, öffnen Sie es in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] oder Word 2010, auf die **Datei** Registerkarte im Menüband **Informationen** > **konvertieren**.  
  
8. Klicken Sie auf **Fertig stellen**.  
  
9. Fügen Sie der Liste von vertrauenswürdigen Speicherorten im Sicherheitscenter in Word in den folgenden Fällen den Projektordner und seine Unterordner hinzu:  
  
   - Sie erstellen ein Word-Dokument auf der Grundlage einer *.docm* -Datei und das Dokument enthält ein VBA-Projekt oder hostet Windows Forms-Steuerelemente. Durch Hinzufügen des Projektordners zur Liste der vertrauenswürdigen Speicherorte können Sie sicherstellen, dass das zur Entwurfszeit wie erwartet funktioniert.  
  
   - Sie erstellen ein Word-Vorlagenprojekt auf der Grundlage einer *.dotx* Datei. Sie müssen der Liste der vertrauenswürdigen Speicherorte den Projektordner hinzufügen, damit das Projekt ausgeführt und gedebuggt werden kann.  
  
     Weitere Informationen zum Hinzufügen eines Dokuments zu den vertrauenswürdigen Speicherorten finden Sie unter der Microsoft Office Online-Website [erstellen, entfernen oder Ändern eines vertrauenswürdigen Speicherorts für Ihre Dateien](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)   
 [Gemeinsame Entwicklung von Office-Projektmappen](../vsto/collaborative-development-of-office-solutions.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  
