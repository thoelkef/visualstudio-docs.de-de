---
title: Erstellen von Outlook-Formularbereichen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 550514444e7931b188951bbf05f8d371bc361aca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="creating-outlook-form-regions"></a>Creating Outlook Form Regions
  Formularbereiche können zum Anpassen von Microsoft Office Outlook-Formularen verwendet werden. Visual Studio bietet erweiterte Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Vorteile der Verwendung von Formularbereichen](#Enhance)  
  
-   [Hinzufügen eines Outlook-Formularbereichs zu Ihrem Projekt](#Adding)  
  
-   [Verwenden des Formularbereich-Designers](#UsingFormRegionDesigner)  
  
-   [Verwenden eines in Outlook entworfenen Formularbereichs](#UsingFormRegionDesignedOutlook)  
  
-   [Hinzufügen von benutzerdefiniertem Code zu einem Formularbereich](#AddingCustomCode)  
  
-   [Beim Erstellen des Projekts](#Building)  
  
-   [Debuggen eines Formularbereichs](#Debugging)  
  
-   [Bereitstellen eines Formularbereichs](#Deploying)  
  
##  <a name="Enhance"></a> Vorteile der Verwendung von Formularbereichen  
 Formularbereiche bieten zahlreiche Verbesserungen gegenüber der traditionellen Outlook-Formularentwicklung:  
  
-   Anpassen der Standardseite beliebiger Standardformulare.  
  
-   Hinzufügen von bis zu 12 zusätzlichen Seiten zu einem beliebigen Standardformular.  
  
-   Ersetzen Sie oder Optimieren beliebiger Standardformulare.  
  
-   Anzeigen einer benutzerdefinierten Benutzeroberfläche im Lesebereich und in den Inspektoren.  
  
 Weitere Informationen finden Sie unter [Anpassen von Formularseiten und Formularbereichen](http://msdn.microsoft.com/library/office/ff869060.aspx).  
  
##  <a name="Adding"></a> Hinzufügen eines Outlook-Formularbereichs zu Ihrem Projekt  
 Sie können die **neuer Outlook-Formularbereich** Assistenten können Sie einen neuen Formularbereich entwerfen oder einen, der in Outlook entworfenen Formularbereich importieren. Wenn Sie über einen Formularbereich verfügen, den Sie in einem anderen Outlook VSTO-Add-In-Projekt verwendet haben, können Sie außerdem Ihren vorhandenen Formularbereich wiederverwenden.  
  
###  <a name="CreatingFormRegion"></a> Erstellen eines neuen Formularbereichs mithilfe des Assistenten  
 Fügen Sie zum Erstellen eines Formularbereichs ein **Outlook-Formularbereich** Element zu einem Outlook-VSTO-Add-in-Projekt. Dies startet den **neuer Outlook-Formularbereich** Assistenten.  
  
 Verwenden Sie den Assistenten, um anzugeben, ob Sie einen neuen Formularbereich entwerfen oder einen in Outlook entworfenen Formularbereich importieren möchten. Weitere Informationen zum Entwerfen eines neuen Formularbereichs finden Sie unter [mithilfe des Formularbereich-Designers](#UsingFormRegionDesigner). Weitere Informationen zur Verwendung eines in Outlook entworfenen Formularbereichs finden Sie unter [importieren ein Formular in Outlook entworfenen Formularbereichs](#UsingFormRegionDesignedOutlook).  
  
 Verwenden Sie den Assistenten, um den Typ des zu erstellenden Formularbereichs auszuwählen. In der folgenden Tabelle werden die einzelnen Formularbereichtypen beschrieben.  
  
|Bereichstyp|Beschreibung|  
|-----------------|-----------------|  
|Getrennt|Fügt den Formularbereich als neue Seite in einem Outlook-Formular hinzu.|  
|Benachbart|Fügt den Formularbereich am unteren Rand einer Outlook-Standardseite des Formulars hinzu.|  
|Ersetzung|Fügt den Formularbereich als neue Seite hinzu, die die Standardseite eines Outlook-Formulars ersetzt.|  
|Alle ersetzen|Ersetzt das gesamte Outlook-Formular durch den Formularbereich.|  
  
 Sie können den Assistenten auch verwenden, um Anzeigebedingungen anzugeben und den Typ des zu erweiternden Formulars auszuwählen. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Die Auswahl, die Sie im Assistenten vornehmen, besitzt Auswirkungen auf die auf den anderen Seiten des Assistenten verfügbaren Optionen. Angenommen, Sie wählen **benachbarten** oder **Separate** in der **Erstellen eines neuen Outlook-Formularbereichs** Seite die **Titel** und **Beschreibung** Felder sind nicht verfügbar in der **Geben Sie einen beschreibenden Text, und wählen Sie die Anzeigeeinstellungen** Seite. Der Grund besteht darin, dass Outlook diese Felder beim Anzeigen eines benachbarten oder getrennten Formularbereichs nicht verwendet.  
  
#### <a name="form-region-files"></a>Formularbereichdateien  
 Nach dem Abschluss der **neuer Outlook-Formularbereich** Assistent, Visual Studio fügt automatisch die folgenden Dateien zu Ihrem Projekt:  
  
-   Eine Formularbereich-Codedatei. Diese Datei hat den Namen, den Sie, für angeben die **Outlook-Formularbereich** Element in der **neues Element hinzufügen** (Dialogfeld). Fügen Sie dieser Datei Code zum Behandeln von Formularbereichereignissen hinzu.  
  
-   Eine Codedatei des Formularbereich-Designers. Diese Datei beinhaltet vom Formularbereich-Designer generierten Code und sollte nicht direkt bearbeitet werden.  
  
-   Eine OFS-Datei (Outlook Form Storage).  
  
    > [!NOTE]  
    >  Diese Datei wird dem Projekt nur hinzugefügt, wenn Sie einen Formularbereich importieren, der in Outlook entworfenen wurde.  
  
#### <a name="form-region-factory-class"></a>Formularbereichsfactory-Klasse  
 Die Formularbereich-Codedatei enthält eine partielle Klasse, die die <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>-Schnittstelle implementiert. Dies ist die Formularbereichsfactory-Klasse. Die Formularbereichsfactory-Klasse ist für das Erstellen neuer Instanzen des Formularbereichs verantwortlich.  
  
 Sie finden diese Klasse, durch Erweitern der **Formularbereichsfactory** Region.  
  
 Die **neuer Outlook-Formularbereich** Assistent fügt Attribute hinzu, um diese Klasse, die den internen Namen des Formularbereichs angeben und die Meldungsklassen an, die den Formularbereich anzeigen. Sie können diese Attribute manuell ändern, nachdem die Datei dem Projekt hinzugefügt wurde.  
  
 Ein Großteil der Formularbereichsfactory-Klasse wird in der Codedatei des Formularbereich-Designers implementiert. Allerdings wird der `FormRegionInitializing`-Ereignishandler in der Formularbereich-Codedatei bereitgestellt. Sie können diesen Ereignishandler zum Angeben verwenden, ob Outlook den Formularbereich anzeigen soll. Weitere Informationen finden Sie unter [Behandeln von Formularbereichereignissen](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Hinzufügen eines vorhandenen Formularbereichs zu Ihrem Projekt  
 Wenn Sie über einen Outlook-Formularbereich verfügen, den Sie in einem anderen Outlook-Projekt verwendet haben, können Sie diesen in Ihrem aktuellen Outlook VSTO-Add-In-Projekt wiederverwenden, indem Sie mit das Dialogfeld **Vorhandenes Element hinzufügen** verwenden.  
  
 Die vorhandenen Formularbereich muss eine Codedatei (VB- oder CS) verfügen. Sie können keine hinzufügen, Outlook Form Storage (OFS) Dateien mithilfe der **vorhandenes Element hinzufügen** (Dialogfeld). Allerdings können Sie einen neuen Formularbereich durch Importieren einer OSF-Datei (Outlook Form Storage) erstellen. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Verwenden des Formularbereich-Designers  
 Der Formularbereich-Designer unterstützt Sie beim Entwerfen des Layouts und des Erscheinungsbilds eines Formularbereichs. Sie können verwaltete Steuerelemente auf die Oberfläche des Designers ziehen, doppelklicken Sie auf Steuerelemente, um Ereignishandler zu öffnen, und legen Sie Eigenschaften der **Eigenschaften** Fenster.  
  
> [!NOTE]  
>  Sie finden die Eigenschaften, die Einfluss auf die des Formularbereichs in Outlook unterhalb der **Manifest** Knoten in der **Eigenschaften** Fenster.  
  
 Der Formularbereich-Designer ist nur verfügbar, wenn Sie auswählen, **einen neuen Formularbereich entwerfen** in der **auswählen, wie der Formularbereich erstellt werden sollen** auf der Seite der **neuer Outlook-Formularbereich** Assistenten.  
  
 Zum Öffnen des Formularbereich-Designers stehen drei Möglichkeiten zur Verfügung:  
  
-   In **Projektmappen-Explorer**, doppelklicken Sie auf die Formularbereich-Codedatei.  
  
-   In **Projektmappen-Explorer**mit der rechten Maustaste auf die Formularbereich-Codedatei, und klicken Sie dann auf **Sicht-Designer**.  
  
-   In **Projektmappen-Explorer**, wählen Sie den Formularbereich-Codedatei, und klicken Sie auf die **Ansicht** Menü klicken Sie auf **Designer**.  
  
 Der Formularbereich-Designer unterstützt nur verwaltete Steuerelemente. Sie können keine systemeigenen Outlook-Steuerelemente hinzufügen.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Importieren eines in Outlook entworfenen Formularbereichs  
 Wenn Sie in Outlook entwerfen, können Sie dem Formularbereich systemeigene Outlook-Steuerelemente hinzufügen. Systemeigene Outlook-Steuerelemente ermöglichen es Ihnen, Outlook-Daten zur Entwurfszeit zu binden. Allerdings können Sie den Formularbereich-Designer nicht zum Hinzufügen verwalteter Steuerelemente oder zum Ändern des Entwurfs des Formularbereichs verwenden.  
  
 Sie können Formularbereiche in ein Outlook VSTO-Add-in-Projekt importieren, mit der **neuer Outlook-Formularbereich** Assistenten. Auf der **auswählen, wie der Formularbereich erstellt werden sollen** Seite **Outlook Form Storage (OFS)-Datei importieren**. Sie können dann zum Speicherort einer OFS-Datei (Outlook Form Storage) navigieren. (Outlook speichert Formularbereiche als OFS-Dateien).  
  
 Die **neuer Outlook-Formularbereich** Assistent kopiert die OFS-Datei in das Projektverzeichnis und fügt Steuerelementverweise-Designer-Datei des Formularbereichs hinzu. Anschließend können Sie die Steuerelementereignisse in der Formularbereich-Codedatei behandeln.  
  
 Wählen Sie ein Ereignis aus der Methodennamenliste oben im Code-Editor aus, um Ereignisse in einem Visual Basic-Projekt zu behandeln.  
  
 Um Ereignisse in einem C#-Projekt zu behandeln, abonnieren Sie Steuerelementereignisse in der Methode <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Weitere Informationen finden Sie unter [wie: abonnieren und Kündigen des Abonnements von Ereignissen &#40;C&#35; Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 Sie können die Eigenschaften von Formularbereichen in der Methode `InitializeManifest` der Formularbereichsfactory-Klasse ändern.  
  
> [!NOTE]  
>  Um einen Formularbereich zu importieren, müssen Sie in einem Projekt arbeiten, das als Ziel dieselbe Version von Outlook verwendet, die Sie auf dem Entwicklungscomputer installiert haben. Z. B. Wenn Sie Outlook 2010 installiert haben, importieren eine Form Bereich funktioniert nur in einem Projekt erstellt wurde mithilfe der **Outlook 2010-Add-in** -Projektvorlage.  
  
### <a name="updating-an-imported-form-regions-design"></a>Aktualisieren eines importierten Formularbereichentwurfs  
 Sie können Steuerelemente für den Formularbereich hinzufügen, entfernen oder ändern. Bevor Sie diese Aufgaben ausführen, erstellen Sie eine Sicherung des Codes, den Sie der Formularbereich-Codedatei hinzugefügt haben. Öffnen Sie dann die OFS-Datei in Outlook, ändern Sie den Formularbereich, und speichern Sie die Änderungen anschließend. Verwenden der **neuer Outlook-Formularbereich** Assistenten, um die geänderte OFS-Datei zu importieren. Anschließend können Sie Ihren Code in die neue Formularbereich-Codedatei einfügen.  
  
##  <a name="AddingCustomCode"></a> Hinzufügen von benutzerdefiniertem Code zu einem Formularbereich  
 Der Namespace <xref:Microsoft.Office.Tools.Outlook> ermöglicht Ihnen den Zugriff auf Klassen, die den Formularbereich darstellen, das Outlook-Element, das den Formularbereich angezeigt, und andere nützliche Elemente. Die **Outlook-Formularbereich** Element fügt automatisch einen Verweis auf diese Assembly im Projekt und fügt die entsprechende **mit** oder **Importe** Anweisung am Anfang der Formularbereich-Codedatei.  
  
 Sie können Klassen, Methoden und Eigenschaften im Microsoft.Office.Interop.Outlook-Namespace verwenden, um die meisten Outlook-Programmieraufgaben auszuführen. Weitere Informationen über das Outlook-Objektmodell finden Sie unter [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md). Beispiele für typische Aufgaben, die von der Outlook-Objektmodell verwenden, finden Sie unter [Outlook-Projektmappen](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Behandeln von Formularbereichereignissen  
 Die **Outlook-Formularbereich** Element automatisch die folgenden drei Ereignishandler auf die Formularbereich-Codedatei hinzugefügt.  
  
|event|Beschreibung|  
|-----------|-----------------|  
|FormRegionInitializing|Tritt auf, bevor der Formularbereich initialisiert wird. Sie können die Bedingungen in diesem Ereignishandler überprüfen, um zu ermitteln, ob Outlook den Formularbereich anzeigen soll. Weitere Informationen finden Sie unter [wie: verhindern Outlook aus der Anzeige eines Formularbereichs](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Tritt nach dem Erstellen einer Instanz des Formularbereichs, jedoch vor dem Anzeigen des Formularbereichs auf.|  
|FormRegionClosed|Tritt auf, bevor der Formularbereich geschlossen wird.|  
  
##  <a name="Building"></a> Beim Erstellen des Projekts  
 Wenn Sie ein Outlook VSTO-Add-In-Projekt erstellen, das einen Formularbereich enthält, fügt Visual Studio der Registrierung die folgenden Informationen hinzu:  
  
-   Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.  
  
-   Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO-Add-Ins darstellt.  
  
 Outlook verwendet diese Informationen zum Laden der Formularbereiche.  
  
##  <a name="Debugging"></a> Debuggen eines Formularbereichs  
 Sie können ein Outlook VSTO-Add-in, das einen Formularbereich enthält, auf die gleiche Weise wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekte debuggen. Beim Starten des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers startet Visual Studio automatisch Outlook.  
  
 Um den Formularbereich anzuzeigen, müssen Sie das entsprechende Outlook-Element öffnen. Öffnen Sie z. B. ein E-Mail-Element, wenn ein benachbarter Formularbereich am Ende des E-Mail-Elements angefügt wird.  
  
##  <a name="Deploying"></a> Bereitstellen eines Formularbereichs  
 Formularbereiche werden automatisch mit dem zugehörigen Outlook VSTO-Add-In bereitgestellt. Daher müssen Sie keine besonderen Aufgaben ausführen, um einen Formularbereich bereitzustellen. Weitere Informationen zum Bereitstellen von VSTO-Add-ins finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)|Enthält Informationen, mit denen Sie Formularbereiche optimieren und potenzielle Probleme vermeiden können.|  
|[Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Veranschaulicht die Erstellen eines Formularbereichs zum Erweitern einer Standard- oder benutzerdefiniertes Microsoft Office Outlook-Formular mithilfe der **neuer Outlook-Formularbereich** Assistenten.|  
|[Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Erläutert, wie angegeben wird, welche Elemente von Microsoft Office Outlook einen Formularbereich anzeigen, indem der Formularbereich der Nachrichtenklasse jedes Elements zugeordnet wird.|  
|[Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)|Zeigt, wie ein benutzerdefinierter Formularbereich entworfen wird, der als neue Seite im Inspektor-Fenster eines Kontaktelements angezeigt wird.|  
|[Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Zeigt, wie ein Formularbereich in Microsoft Office Outlook entworfen und importieren Sie den Formularbereich in ein Outlook VSTO-Add-in-Projekt mithilfe der **neuer Outlook-Formularbereich** Assistenten.|  
|[Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)|Beschreibt, wie Sie Code zum Einblenden, Ausblenden oder Ändern von Steuerelementen in einem Formularbereich schreiben und Benutzern ermöglichen, den Code aus anderen Bereichen im Projekt mithilfe der Klasse `Globals` auszuführen.|  
|[Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Zeigt, wie verhindert wird, dass Microsoft Office Outlook einen Formularbereich für ein bestimmtes Element anzeigt.|  
|Zeigt, wie auf das Outlook-Element zugegriffen wird, in dem ein Formularbereich angezeigt wird.|  
|[Benutzerdefinierte Aktionen in Outlook-Formularbereichen](../vsto/custom-actions-in-outlook-form-regions.md)|Beschreibt, wie es Benutzern ermöglicht wird, auf ein Outlook-Element zu reagieren.|  
  
  