---
title: Erstellen von Outlook-Formularbereichen
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bd30624c2948b12885af3a29eb095227cf795f9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865774"
---
# <a name="create-outlook-form-regions"></a>Erstellen von Outlook-Formularbereichen
  Formularbereiche können zum Anpassen von Microsoft Office Outlook-Formularen verwendet werden. Visual Studio bietet erweiterte Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Vorteile der Verwendung von Formularbereichen](#Enhance)  
  
-   [Hinzufügen eines Outlook-Formularbereichs zu Ihrem Projekt](#Adding)  
  
-   [Verwenden des Formularbereich-Designers](#UsingFormRegionDesigner)  
  
-   [Verwenden eines in Outlook entworfenen Formularbereichs](#UsingFormRegionDesignedOutlook)  
  
-   [Hinzufügen von benutzerdefiniertem Code zu einem Formularbereich](#AddingCustomCode)  
  
-   [Erstellen Sie das Projekt](#Building)  
  
-   [Debuggen eines Formularbereichs](#Debugging)  
  
-   [Bereitstellen eines Formularbereichs](#Deploying)  
  
##  <a name="Enhance"></a> Vorteile der Verwendung von Formularbereichen  
 Formularbereiche bieten zahlreiche Verbesserungen gegenüber der traditionellen Outlook-Formularentwicklung:  
  
- Anpassen der Standardseite beliebiger Standardformulare.  
  
- Hinzufügen von bis zu 12 zusätzlichen Seiten zu einem beliebigen Standardformular.  
  
- Ersetzen Sie oder Optimieren beliebiger Standardformulare.  
  
- Anzeigen einer benutzerdefinierten Benutzeroberfläche im Lesebereich und in den Inspektoren.  
  
  Weitere Informationen finden Sie unter [Anpassen von Formularseiten und Formularbereichen](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).  
  
##  <a name="Adding"></a> Hinzufügen eines Outlook-Formularbereichs zu Ihrem Projekt  
 Sie können die **neuer Outlook-Formularbereich** Assistenten können Sie einen neuen Formularbereich entwerfen oder einen, der in Outlook entworfenen Formularbereich importieren. Wenn Sie über einen Formularbereich verfügen, den Sie in einem anderen Outlook VSTO-Add-In-Projekt verwendet haben, können Sie außerdem Ihren vorhandenen Formularbereich wiederverwenden.  
  
###  <a name="CreatingFormRegion"></a> Erstellen eines neuen Formularbereichs mithilfe des Assistenten  
 Fügen Sie zum Erstellen eines Formularbereichs ein **Outlook-Formularbereich** Element zu einem Outlook-VSTO-Add-in-Projekt. Dies startet den **neuer Outlook-Formularbereich** Assistenten.  
  
 Verwenden Sie den Assistenten, um anzugeben, ob Sie einen neuen Formularbereich entwerfen oder einen in Outlook entworfenen Formularbereich importieren möchten. Weitere Informationen zum Entwerfen eines neuen Formularbereichs finden Sie unter [Verwenden des Formularbereich-Designers](#UsingFormRegionDesigner). Weitere Informationen zur Verwendung eines in Outlook entworfenen Formularbereichs finden Sie unter [einen in Outlook entworfenen Formularbereich importieren](#UsingFormRegionDesignedOutlook).  
  
 Verwenden Sie den Assistenten, um den Typ des zu erstellenden Formularbereichs auszuwählen. In der folgenden Tabelle werden die einzelnen Formularbereichtypen beschrieben.  
  
|Bereichstyp|Beschreibung|  
|-----------------|-----------------|  
|Getrennt|Fügt den Formularbereich als neue Seite in einem Outlook-Formular hinzu.|  
|Benachbart|Fügt den Formularbereich am unteren Rand einer Outlook-Standardseite des Formulars hinzu.|  
|Ersetzung|Fügt den Formularbereich als neue Seite hinzu, die die Standardseite eines Outlook-Formulars ersetzt.|  
|Alle ersetzen|Ersetzt das gesamte Outlook-Formular durch den Formularbereich.|  
  
 Sie können den Assistenten auch verwenden, um Anzeigebedingungen anzugeben und den Typ des zu erweiternden Formulars auszuwählen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Die Auswahl, die Sie im Assistenten vornehmen, besitzt Auswirkungen auf die auf den anderen Seiten des Assistenten verfügbaren Optionen. Bei Auswahl von beispielsweise **benachbarten** oder **Separate** in die **erstellen Sie einen neuen Outlook-Formularbereich** Seite die **Titel** und **Beschreibung** Felder sind nicht verfügbar, in der **Geben Sie einen beschreibenden Text, und wählen Sie die Anzeigeeinstellungen** Seite. Der Grund besteht darin, dass Outlook diese Felder beim Anzeigen eines benachbarten oder getrennten Formularbereichs nicht verwendet.  
  
#### <a name="form-region-files"></a>Formularbereichdateien  
 Nach Abschluss der **neuer Outlook-Formularbereich** Assistent bietet Ihnen Visual Studio fügt automatisch die folgenden Dateien zu Ihrem Projekt hinzu:  
  
-   Eine Formularbereich-Codedatei. Diese Datei enthält den Namen, den Sie, für angeben die **Outlook-Formularbereich** Element in der **neues Element hinzufügen** Dialogfeld. Fügen Sie dieser Datei Code zum Behandeln von Formularbereichereignissen hinzu.  
  
-   Eine Codedatei des Formularbereich-Designers. Diese Datei beinhaltet vom Formularbereich-Designer generierten Code und sollte nicht direkt bearbeitet werden.  
  
-   Outlook Form Storage (*OFS*) Datei.  
  
    > [!NOTE]  
    >  Diese Datei wird dem Projekt nur hinzugefügt, wenn Sie einen Formularbereich importieren, der in Outlook entworfenen wurde.  
  
#### <a name="form-region-factory-class"></a>Formularbereichsfactory-Klasse  
 Die Formularbereich-Codedatei enthält eine partielle Klasse, die die <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>-Schnittstelle implementiert. Dies ist die Formularbereichsfactory-Klasse. Die Formularbereichsfactory-Klasse ist für das Erstellen neuer Instanzen des Formularbereichs verantwortlich.  
  
 Sie finden diese Klasse erweitert die **Formularbereichsfactory** Region.  
  
 Die **neuer Outlook-Formularbereich** Assistenten Fügt Attribute auf diese Klasse, die den internen Namen des Formularbereichs angeben und die Meldungsklassen an, die den Formularbereich anzeigen. Sie können diese Attribute manuell ändern, nachdem die Datei dem Projekt hinzugefügt wurde.  
  
 Ein Großteil der Formularbereichsfactory-Klasse wird in der Codedatei des Formularbereich-Designers implementiert. Allerdings wird der `FormRegionInitializing`-Ereignishandler in der Formularbereich-Codedatei bereitgestellt. Sie können diesen Ereignishandler zum Angeben verwenden, ob Outlook den Formularbereich anzeigen soll. Weitere Informationen finden Sie unter [Behandeln von formularbereichereignissen](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Hinzufügen eines vorhandenen Formularbereichs zu Ihrem Projekt  
 Wenn Sie über einen Outlook-Formularbereich verfügen, den Sie in einem anderen Outlook-Projekt verwendet haben, können Sie diesen in Ihrem aktuellen Outlook VSTO-Add-In-Projekt wiederverwenden, indem Sie mit das Dialogfeld **Vorhandenes Element hinzufügen** verwenden.  
  
 Der vorhandenen Formularbereich benötigen eine Codedatei (*vb* oder *cs*); Outlook Form Storage kann nicht hinzugefügt werden (*OFS*) Dateien mithilfe der **vorhandenes Element hinzufügen** Dialogfeld. Allerdings können Sie einen neuen Formularbereich durch Importieren einer OSF-Datei (Outlook Form Storage) erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Verwenden des Formularbereich-Designers  
 Der Formularbereich-Designer unterstützt Sie beim Entwerfen des Layouts und des Erscheinungsbilds eines Formularbereichs. Sie können verwaltete Steuerelemente auf die Oberfläche des Designers gezogen, doppelklicken Sie auf die Steuerelemente, um Ereignishandler zu öffnen, und legen Sie Eigenschaften der **Eigenschaften** Fenster.  
  
> [!NOTE]  
>  Sie finden die Eigenschaften, die Einfluss auf die des Formularbereichs in Outlook unter der **Manifest** Knoten in der **Eigenschaften** Fenster.  
  
 Der Formularbereich-Designer ist nur verfügbar, wenn Sie auswählen, **einen neuen Formularbereich entwerfen** in die **wählen, wie der Formularbereich erstellt werden sollen** auf der Seite die **neuer Outlook-Formularbereich** Der Assistent.  
  
 Zum Öffnen des Formularbereich-Designers stehen drei Möglichkeiten zur Verfügung:  
  
- In **Projektmappen-Explorer**, doppelklicken Sie auf die Formularbereich-Codedatei.  
  
- In **Projektmappen-Explorer**mit der rechten Maustaste auf die Formularbereich-Codedatei, und klicken Sie dann auf **Ansicht-Designer**.  
  
- In **Projektmappen-Explorer**, wählen Sie den Formularbereich-Codedatei, und klicken Sie auf die **Ansicht** Menü klicken Sie auf **Designer**.  
  
  Der Formularbereich-Designer unterstützt nur verwaltete Steuerelemente. Sie können keine systemeigenen Outlook-Steuerelemente hinzufügen.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Importieren Sie einen in Outlook entworfenen Formularbereich  
 Wenn Sie in Outlook entwerfen, können Sie dem Formularbereich systemeigene Outlook-Steuerelemente hinzufügen. Systemeigene Outlook-Steuerelemente ermöglichen es Ihnen, Outlook-Daten zur Entwurfszeit zu binden. Allerdings können Sie den Formularbereich-Designer nicht zum Hinzufügen verwalteter Steuerelemente oder zum Ändern des Entwurfs des Formularbereichs verwenden.  
  
 Sie können Formularbereiche in ein Outlook VSTO-Add-in-Projekt importieren, mit der **neuer Outlook-Formularbereich** Assistenten. Auf der **wählen, wie der Formularbereich erstellt werden sollen** Seite **Outlook Form Storage (OFS)-Datei importieren**. Sie können dann zum Speicherort der Datei Outlook Form Storage navigieren (*OFS*) Datei. (Outlook speichert Formularbereiche als *OFS* Dateien.)  
  
 Die **neuer Outlook-Formularbereich** Assistent kopiert das *OFS* -Datei in das Projektverzeichnis und fügt Steuerelementverweise an der Designerdatei Region. Anschließend können Sie die Steuerelementereignisse in der Formularbereich-Codedatei behandeln.  
  
 Wählen Sie ein Ereignis aus der Methodennamenliste oben im Code-Editor aus, um Ereignisse in einem Visual Basic-Projekt zu behandeln.  
  
 Um Ereignisse in einem C#-Projekt zu behandeln, abonnieren Sie Steuerelementereignisse in der Methode <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Weitere Informationen finden Sie unter [Vorgehensweise: Abonnieren und abbestellen von Ereignisabonnements &#40;C&#35; Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 Sie können die Eigenschaften von Formularbereichen in der Methode `InitializeManifest` der Formularbereichsfactory-Klasse ändern.  
  
> [!NOTE]  
>  Um einen Formularbereich zu importieren, müssen Sie in einem Projekt arbeiten, das als Ziel dieselbe Version von Outlook verwendet, die Sie auf dem Entwicklungscomputer installiert haben. Z. B. Wenn Sie Outlook 2010 installiert haben, importieren ein Formular Region funktioniert nur in einem Projekt erstellt wurde mithilfe der **Outlook 2010-Add-in** Projektvorlage.  
  
### <a name="update-an-imported-form-regions-design"></a>Aktualisieren eines importierten Formularbereichs-Entwurf  
 Sie können Steuerelemente für den Formularbereich hinzufügen, entfernen oder ändern. Bevor Sie diese Aufgaben ausführen, erstellen Sie eine Sicherung des Codes, den Sie der Formularbereich-Codedatei hinzugefügt haben. Öffnen Sie dann die *OFS* Datei in Outlook, ändern Sie den Formularbereich und speichern Sie die Änderungen. Verwenden der **neuer Outlook-Formularbereich** Assistenten, um die geänderte importieren *OFS* Datei. Anschließend können Sie Ihren Code in die neue Formularbereich-Codedatei einfügen.  
  
##  <a name="AddingCustomCode"></a> Hinzufügen von benutzerdefiniertem Code zu einem Formularbereich  
 Der Namespace <xref:Microsoft.Office.Tools.Outlook> ermöglicht Ihnen den Zugriff auf Klassen, die den Formularbereich darstellen, das Outlook-Element, das den Formularbereich angezeigt, und andere nützliche Elemente. Die **Outlook-Formularbereich** Element fügt automatisch einen Verweis auf diese Assembly im Projekt und fügt die entsprechende **mit** oder **Importe** Anweisung am Anfang der Formularbereich-Codedatei.  
  
 Sie können Klassen, Methoden und Eigenschaften im Namespace `Microsoft.Office.Interop.Outlook` verwenden, um die meisten Outlook-Programmieraufgaben auszuführen. Weitere Informationen zu Outlook-Objektmodell, finden Sie unter [Übersicht über Outlook-Objektmodell](../vsto/outlook-object-model-overview.md). Beispiele für typische Aufgaben, die Outlook-Objektmodell verwenden, finden Sie unter [Outlook-Projektmappen](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Behandeln von formularbereichereignissen  
 Die **Outlook-Formularbereich** Element automatisch die folgenden drei Ereignishandler auf die Formularbereich-Codedatei hinzugefügt.  
  
|event|Beschreibung|  
|-----------|-----------------|  
|FormRegionInitializing|Tritt auf, bevor der Formularbereich initialisiert wird. Sie können die Bedingungen in diesem Ereignishandler überprüfen, um zu ermitteln, ob Outlook den Formularbereich anzeigen soll. Weitere Informationen finden Sie unter [Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Tritt nach dem Erstellen einer Instanz des Formularbereichs, jedoch vor dem Anzeigen des Formularbereichs auf.|  
|FormRegionClosed|Tritt auf, bevor der Formularbereich geschlossen wird.|  
  
##  <a name="Building"></a> Erstellen Sie das Projekt  
 Wenn Sie ein Outlook VSTO-Add-In-Projekt erstellen, das einen Formularbereich enthält, fügt Visual Studio der Registrierung die folgenden Informationen hinzu:  
  
- Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.  
  
- Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO-Add-Ins darstellt.  
  
  Outlook verwendet diese Informationen zum Laden der Formularbereiche.  
  
##  <a name="Debugging"></a> Debuggen eines Formularbereichs  
 Sie können ein Outlook VSTO-Add-in, das einen Formularbereich enthält, auf die gleiche Weise wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projekte debuggen. Beim Starten des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Debuggers startet Visual Studio automatisch Outlook.  
  
 Um den Formularbereich anzuzeigen, müssen Sie das entsprechende Outlook-Element öffnen. Öffnen Sie z. B. ein E-Mail-Element, wenn ein benachbarter Formularbereich am Ende des E-Mail-Elements angefügt wird.  
  
##  <a name="Deploying"></a> Bereitstellen eines Formularbereichs  
 Formularbereiche werden automatisch mit dem zugehörigen Outlook VSTO-Add-In bereitgestellt. Daher müssen Sie keine besonderen Aufgaben ausführen, um einen Formularbereich bereitzustellen. Weitere Informationen zum Bereitstellen von VSTO-Add-ins finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erstellen Sie Richtlinien für Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)|Enthält Informationen, mit denen Sie Formularbereiche optimieren und potenzielle Probleme vermeiden können.|  
|[Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Erfahren Sie, wie erstellen Sie einen Formularbereich, um eine Standard- oder benutzerdefiniertes Microsoft Office Outlook-Formular mit Erweitern der **neuer Outlook-Formularbereich** Assistenten.|  
|[Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Erläutert, wie angegeben wird, welche Elemente von Microsoft Office Outlook einen Formularbereich anzeigen, indem der Formularbereich der Nachrichtenklasse jedes Elements zugeordnet wird.|  
|[Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)|Zeigt, wie ein benutzerdefinierter Formularbereich entworfen wird, der als neue Seite im Inspektor-Fenster eines Kontaktelements angezeigt wird.|  
|[Exemplarische Vorgehensweise: Importieren Sie einen, der in Outlook entworfenen Formularbereich](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Zeigt, wie ein Formularbereich in Microsoft Office Outlook entworfen und anschließend mithilfe des Formularbereichs in ein Outlook VSTO-Add-in-Projekt importiert die **neuer Outlook-Formularbereich** Assistenten.|  
|[Zugriff auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)|Beschreibt, wie Sie Code zum Einblenden, Ausblenden oder Ändern von Steuerelementen in einem Formularbereich schreiben und Benutzern ermöglichen, den Code aus anderen Bereichen im Projekt mithilfe der Klasse `Globals` auszuführen.|  
|[Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Zeigt, wie verhindert wird, dass Microsoft Office Outlook einen Formularbereich für ein bestimmtes Element anzeigt.|  
|Zeigt, wie auf das Outlook-Element zugegriffen wird, in dem ein Formularbereich angezeigt wird.|  
|[Benutzerdefinierte Aktionen in Outlook-Formularbereichen](../vsto/custom-actions-in-outlook-form-regions.md)|Beschreibt, wie es Benutzern ermöglicht wird, auf ein Outlook-Element zu reagieren.|  
