---
title: "Erstellen von Outlook-Formularbereichen | Microsoft Docs"
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
  - "MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Formularbereiche [Office-Entwicklung in Visual Studio]"
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Erstellen"
  - "Outlook [Office-Entwicklung in Visual Studio], Formularbereiche"
ms.assetid: a8005641-cc8b-4e07-8dca-294327cdc8d4
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Erstellen von Outlook-Formularbereichen
  Formularbereiche können zum Anpassen von Microsoft Office Outlook\-Formularen verwendet werden.  Visual Studio bietet erweiterte Tools, die Ihnen das Entwerfen, Entwickeln und Debuggen von Formularbereichen erleichtern.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Vorteile der Verwendung von Formularbereichen](#Enhance)  
  
-   [Hinzufügen eines Outlook\-Formularbereichs zu Ihrem Projekt](#Adding)  
  
-   [Verwenden des Formularbereich\-Designers](#UsingFormRegionDesigner)  
  
-   [Verwenden eines in Outlook entworfenen Formularbereichs](#UsingFormRegionDesignedOutlook)  
  
-   [Hinzufügen von benutzerdefiniertem Code zu einem Formularbereich](#AddingCustomCode)  
  
-   [Erstellen des Projekts](#Building)  
  
-   [Debuggen eines Formularbereichs](#Debugging)  
  
-   [Bereitstellen eines Formularbereichs](#Deploying)  
  
##  <a name="Enhance"></a> Vorteile der Verwendung von Formularbereichen  
 Formularbereiche bieten zahlreiche Verbesserungen gegenüber der traditionellen Outlook\-Formularentwicklung:  
  
-   Anpassen der Standardseite beliebiger Standardformulare.  
  
-   Hinzufügen von bis zu 12 zusätzlichen Seiten zu einem beliebigen Standardformular.  
  
-   Ersetzen Sie oder Optimieren beliebiger Standardformulare.  
  
-   Anzeigen einer benutzerdefinierten Benutzeroberfläche im Lesebereich und in den Inspektoren.  
  
 Weitere Informationen finden Sie unter [Anpassen von Formularseiten und Formularbereichen](HV10038632).  
  
##  <a name="Adding"></a> Hinzufügen eines Outlook\-Formularbereichs zu Ihrem Projekt  
 Sie können den Assistenten **Neuer Outlook\-Formularbereich** verwenden, um einen neuen Formularbereich zu entwerfen oder einen in Outlook entworfenen Formularbereich zu importieren.  Wenn Sie über einen Formularbereich verfügen, den Sie in einem anderen Outlook VSTO\-Add\-In\-Projekt verwendet haben, können Sie außerdem Ihren vorhandenen Formularbereich wiederverwenden.  
  
###  <a name="CreatingFormRegion"></a> Erstellen eines neuen Formularbereichs mithilfe des Assistenten  
 Fügen Sie zum Erstellen eines Formularbereichs ein Element **Outlook\-Formularbereich** zu einem Outlook VSTO\-Add\-In\-Projekt hinzu.  Auf diese Weise wird der Assistent **Neuer Outlook\-Formularbereich** gestartet.  
  
 Verwenden Sie den Assistenten, um anzugeben, ob Sie einen neuen Formularbereich entwerfen oder einen in Outlook entworfenen Formularbereich importieren möchten.  Weitere Informationen zum Entwerfen eines neuen Formularbereichs finden Sie unter [Verwenden des Formularbereich\-Designers](#UsingFormRegionDesigner).  Weitere Informationen zum Verwenden eines in Outlook entworfenen Formularbereichs finden Sie unter [Importieren eines in Outlook entworfenen Formularbereichs](#UsingFormRegionDesignedOutlook).  
  
 Verwenden Sie den Assistenten, um den Typ des zu erstellenden Formularbereichs auszuwählen.  In der folgenden Tabelle werden die einzelnen Formularbereichtypen beschrieben.  
  
|Bereichstyp|Beschreibung|  
|-----------------|------------------|  
|Getrennt|Fügt den Formularbereich als neue Seite in einem Outlook\-Formular hinzu.|  
|Benachbart|Fügt den Formularbereich am unteren Rand einer Outlook\-Standardseite des Formulars hinzu.|  
|Ersetzung|Fügt den Formularbereich als neue Seite hinzu, die die Standardseite eines Outlook\-Formulars ersetzt.|  
|Alle ersetzen|Ersetzt das gesamte Outlook\-Formular durch den Formularbereich.|  
  
 Sie können den Assistenten auch verwenden, um Anzeigebedingungen anzugeben und den Typ des zu erweiternden Formulars auszuwählen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Die Auswahl, die Sie im Assistenten vornehmen, besitzt Auswirkungen auf die auf den anderen Seiten des Assistenten verfügbaren Optionen.  Wenn Sie z. B. die Option **Benachbart** oder **Getrennt** auf der Seite **Neuen Outlook\-Formularbereich erstellen** auswählen, sind die Felder **Titel** und **Beschreibung** auf der Seite **Geben Sie eine Beschreibung ein, und wählen Sie die Anzeigeeinstellungen aus** nicht verfügbar.  Der Grund besteht darin, dass Outlook diese Felder beim Anzeigen eines benachbarten oder getrennten Formularbereichs nicht verwendet.  
  
#### Formularbereichdateien  
 Wenn Sie den Assistenten **Neuer Outlook\-Formularbereich** fertig stellen, fügt Visual Studio Ihrem Projekt automatisch die folgenden Dateien hinzu:  
  
-   Eine Formularbereich\-Codedatei.  Diese Datei besitzt den Namen, den Sie für das **Outlook\-Formularbereich**\-Element im Dialogfeld **Neues Element hinzufügen** angeben.  Fügen Sie dieser Datei Code zum Behandeln von Formularbereichereignissen hinzu.  
  
-   Eine Codedatei des Formularbereich\-Designers.  Diese Datei beinhaltet vom Formularbereich\-Designer generierten Code und sollte nicht direkt bearbeitet werden.  
  
-   Eine OFS\-Datei \(Outlook Form Storage\).  
  
    > [!NOTE]  
    >  Diese Datei wird dem Projekt nur hinzugefügt, wenn Sie einen Formularbereich importieren, der in Outlook entworfenen wurde.  
  
#### Formularbereichsfactory\-Klasse  
 Die Formularbereich\-Codedatei enthält eine partielle Klasse, die die <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>\-Schnittstelle implementiert.  Dies ist die Formularbereichsfactory\-Klasse.  Die Formularbereichsfactory\-Klasse ist für das Erstellen neuer Instanzen des Formularbereichs verantwortlich.  
  
 Sie finden diese Klasse, indem Sie den Bereich **Formularbereichsfactory** erweitern.  
  
 Der Assistent **Neuer Outlook\-Formularbereich** fügt dieser Klasse Attribute hinzu, die den internen Namen des Formularbereichs und die Nachrichtenklassen angeben, die den Formularbereich anzeigen.  Sie können diese Attribute manuell ändern, nachdem die Datei dem Projekt hinzugefügt wurde.  
  
 Ein Großteil der Formularbereichsfactory\-Klasse wird in der Codedatei des Formularbereich\-Designers implementiert.  Allerdings wird der `FormRegionInitializing`\-Ereignishandler in der Formularbereich\-Codedatei bereitgestellt.  Sie können diesen Ereignishandler zum Angeben verwenden, ob Outlook den Formularbereich anzeigen soll.  Weitere Informationen finden Sie unter [Behandeln von Formularbereichereignissen](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Hinzufügen eines vorhandenen Formularbereichs zu Ihrem Projekt  
 Wenn Sie über einen Outlook\-Formularbereich verfügen, den Sie in einem anderen Outlook\-Projekt verwendet haben, können Sie diesen in Ihrem aktuellen Outlook VSTO\-Add\-In\-Projekt wiederverwenden, indem Sie mit das Dialogfeld **Vorhandenes Element hinzufügen** verwenden.  
  
 Der vorhandenen Formularbereich muss über eine Codedatei \(VB\- oder CS\-Datei\) verfügen. Sie könne keine OFS\-Dateien \(Outlook Form Storage\) mithilfe des Dialogfelds **Vorhandenes Element hinzufügen** hinzufügen.  Allerdings können Sie einen neuen Formularbereich durch Importieren einer OSF\-Datei \(Outlook Form Storage\) erstellen.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Verwenden des Formularbereich\-Designers  
 Der Formularbereich\-Designer unterstützt Sie beim Entwerfen des Layouts und des Erscheinungsbilds eines Formularbereichs.  Sie können verwaltete Steuerelemente auf die Oberfläche des Designers ziehen, auf Steuerelemente doppelklicken, um Ereignishandler zu öffnen, und Eigenschaften im Fenster **Eigenschaften** festlegen.  
  
> [!NOTE]  
>  Eigenschaften, die Einfluss auf die Darstellung des Formularbereichs in Outlook besitzen, finden Sie unter dem Knoten **Manifest** im Fenster **Eigenschaften**.  
  
 Der Formularbereich\-Designer ist nur verfügbar, wenn Sie **Neuen Formularbereich entwerfen** auf der Seite **Legen Sie fest, wie der Formularbereich erstellt werden soll** des Assistenten **Neuer Outlook\-Formularbereich** auswählen.  
  
 Zum Öffnen des Formularbereich\-Designers stehen drei Möglichkeiten zur Verfügung:  
  
-   Doppelklicken Sie im **Projektmappen\-Explorer** auf die Formularbereich\-Codedatei.  
  
-   Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Formularbereich\-Codedatei, und klicken Sie dann auf **Designer anzeigen**.  
  
-   Wählen Sie im **Projektmappen\-Explorer** die Formularbereich\-Codedatei aus, und klicken Sie dann im Menü **Ansicht** auf **Designer**.  
  
 Der Formularbereich\-Designer unterstützt nur verwaltete Steuerelemente.  Sie können keine systemeigenen Outlook\-Steuerelemente hinzufügen.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Importieren eines in Outlook entworfenen Formularbereichs  
 Wenn Sie in Outlook entwerfen, können Sie dem Formularbereich systemeigene Outlook\-Steuerelemente hinzufügen.  Systemeigene Outlook\-Steuerelemente ermöglichen es Ihnen, Outlook\-Daten zur Entwurfszeit zu binden.  Allerdings können Sie den Formularbereich\-Designer nicht zum Hinzufügen verwalteter Steuerelemente oder zum Ändern des Entwurfs des Formularbereichs verwenden.  
  
 Sie können Formularbereiche in ein Outlook VSTO\-Add\-In\-Projekt importieren, indem Sie den Assistenten **Neuer Outlook\-Formularbereich** verwenden.  Wählen Sie auf der Seite **Legen Sie fest, wie der Formularbereich erstellt werden soll** die Option **OFS\-Datei \(Outlook Form Storage\) importieren** aus.  Sie können dann zum Speicherort einer OFS\-Datei \(Outlook Form Storage\) navigieren.  \(Outlook speichert Formularbereiche als OFS\-Dateien\).  
  
 Der Assistent **Neuer Outlook\-Formularbereich** kopiert die OFS\-Datei in das Projektverzeichnis und fügt Steuerelementverweise aus die Codedatei des Formularbereich\-Designers hinzu.  Anschließend können Sie die Steuerelementereignisse in der Formularbereich\-Codedatei behandeln.  
  
 Wählen Sie ein Ereignis aus der Methodennamenliste oben im Code\-Editor aus, um Ereignisse in einem Visual Basic\-Projekt zu behandeln.  
  
 Um Ereignisse in einem C\#\-Projekt zu behandeln, abonnieren Sie Steuerelementereignisse in der Methode <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>.  Weitere Informationen finden Sie unter [Gewusst wie: Abonnieren von Ereignissen und Kündigen von Ereignisabonnements &#40;C&#35;-Programmierhandbuch&#41;](../Topic/How%20to:%20Subscribe%20to%20and%20Unsubscribe%20from%20Events%20(C%23%20Programming%20Guide).md).  
  
 Sie können die Eigenschaften von Formularbereichen in der Methode `InitializeManifest` der Formularbereichsfactory\-Klasse ändern.  
  
> [!NOTE]  
>  Um einen Formularbereich zu importieren, müssen Sie in einem Projekt arbeiten, das als Ziel dieselbe Version von Outlook verwendet, die Sie auf dem Entwicklungscomputer installiert haben.  Wenn Sie z. B. Outlook 2010 installiert haben, funktioniert das Importieren eines Formularbereichs nur in einem Projekt, das mithilfe der **Outlook 2010\-Add\-In**\-Projektvorlage erstellt wurde.  
  
### Aktualisieren eines importierten Formularbereichentwurfs  
 Sie können Steuerelemente für den Formularbereich hinzufügen, entfernen oder ändern.  Bevor Sie diese Aufgaben ausführen, erstellen Sie eine Sicherung des Codes, den Sie der Formularbereich\-Codedatei hinzugefügt haben.  Öffnen Sie dann die OFS\-Datei in Outlook, ändern Sie den Formularbereich, und speichern Sie die Änderungen anschließend.  Verwenden den Assistenten **Neuer Outlook\-Formularbereich**, um die geänderte OFS\-Datei zu importieren.  Anschließend können Sie Ihren Code in die neue Formularbereich\-Codedatei einfügen.  
  
##  <a name="AddingCustomCode"></a> Hinzufügen von benutzerdefiniertem Code zu einem Formularbereich  
 Der Namespace <xref:Microsoft.Office.Tools.Outlook> ermöglicht Ihnen den Zugriff auf Klassen, die den Formularbereich darstellen, das Outlook\-Element, das den Formularbereich angezeigt, und andere nützliche Elemente.  Das **Outlook\-Formularbereich**\-Element fügt dieser Assembly im Projekt automatisch einen Verweis hinzu und fügt die entsprechende **using**\- oder **Imports**\-Anweisung am Anfang der Formularbereich\-Codedatei ein.  
  
 Sie können Klassen, Methoden und Eigenschaften im Namespace Microsoft.Office.Interop.Outlook verwenden, um die meisten Outlook\-Programmieraufgaben auszuführen.  Weitere Informationen zum Outlook\-Objektmodell finden Sie unter [Übersicht über das Outlook-Objektmodell](../vsto/outlook-object-model-overview.md).  Beispiele für typische Aufgaben, in denen das Outlook\-Objektmodell verwendet wird, finden Sie unter [Outlook-Projektmappen](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Behandeln von Formularbereichereignissen  
 Das **Outlook\-Formularbereich**\-Element fügt die folgenden drei Ereignishandler der Formularbereich\-Codedatei automatisch hinzu.  
  
|Ereignis|Beschreibung|  
|--------------|------------------|  
|FormRegionInitializing|Tritt auf, bevor der Formularbereich initialisiert wird.  Sie können die Bedingungen in diesem Ereignishandler überprüfen, um zu ermitteln, ob Outlook den Formularbereich anzeigen soll.  Weitere Informationen finden Sie unter [Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Tritt nach dem Erstellen einer Instanz des Formularbereichs, jedoch vor dem Anzeigen des Formularbereichs auf.|  
|FormRegionClosed|Tritt auf, bevor der Formularbereich geschlossen wird.|  
  
##  <a name="Building"></a> Erstellen des Projekts  
 Wenn Sie ein Outlook VSTO\-Add\-In\-Projekt erstellen, das einen Formularbereich enthält, fügt Visual Studio der Registrierung die folgenden Informationen hinzu:  
  
-   Einen Schlüssel für jede Nachrichtenklasse, die mindestens einem Formularbereich zugeordnet ist.  
  
-   Einen Eintrag für jeden Formularbereich und einen zugeordneten Wert, der den Namen des Outlook VSTO\-Add\-Ins darstellt.  
  
 Outlook verwendet diese Informationen zum Laden der Formularbereiche.  
  
##  <a name="Debugging"></a> Debuggen eines Formularbereichs  
 Sie können ein Outlook VSTO\-Add\-in, das einen Formularbereich enthält, auf die gleiche Weise wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projekte debuggen.  Beim Starten des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debuggers startet Visual Studio automatisch Outlook.  
  
 Um den Formularbereich anzuzeigen, müssen Sie das entsprechende Outlook\-Element öffnen.  Öffnen Sie z. B. ein E\-Mail\-Element, wenn ein benachbarter Formularbereich am Ende des E\-Mail\-Elements angefügt wird.  
  
##  <a name="Deploying"></a> Bereitstellen eines Formularbereichs  
 Formularbereiche werden automatisch mit dem zugehörigen Outlook VSTO\-Add\-In bereitgestellt.  Daher müssen Sie keine besonderen Aufgaben ausführen, um einen Formularbereich bereitzustellen.  Weitere Informationen zum Bereitstellen von VSTO\-Add\-Ins finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)|Enthält Informationen, mit denen Sie Formularbereiche optimieren und potenzielle Probleme vermeiden können.|  
|[Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Zeigt, wie ein Formularbereich erstellt wird, um ein Standard\- oder benutzerdefiniertes Microsoft Office Outlook\-Formular mithilfe des Assistenten **Neuer Outlook\-Formularbereich** zu erweitern.|  
|[Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Erläutert, wie angegeben wird, welche Elemente von Microsoft Office Outlook einen Formularbereich anzeigen, indem der Formularbereich der Nachrichtenklasse jedes Elements zugeordnet wird.|  
|[Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)|Zeigt, wie ein benutzerdefinierter Formularbereich entworfen wird, der als neue Seite im Inspektor\-Fenster eines Kontaktelements angezeigt wird.|  
|[Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Zeigt, wie ein Formularbereich in Microsoft Office Outlook entworfen und anschließend mithilfe des Assistenten **Neuer Outlook\-Formularbereich** in ein Outlook VSTO\-Add\-In\-Projekt importiert wird.|  
|[Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)|Beschreibt, wie Sie Code zum Einblenden, Ausblenden oder Ändern von Steuerelementen in einem Formularbereich schreiben und Benutzern ermöglichen, den Code aus anderen Bereichen im Projekt mithilfe der Klasse `Globals` auszuführen.|  
|[Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Zeigt, wie verhindert wird, dass Microsoft Office Outlook einen Formularbereich für ein bestimmtes Element anzeigt.|  
|Zeigt, wie auf das Outlook\-Element zugegriffen wird, in dem ein Formularbereich angezeigt wird.|  
|[Benutzerdefinierte Aktionen in Outlook-Formularbereichen](../vsto/custom-actions-in-outlook-form-regions.md)|Beschreibt, wie es Benutzern ermöglicht wird, auf ein Outlook\-Element zu reagieren.|  
  
  