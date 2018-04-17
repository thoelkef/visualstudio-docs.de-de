---
title: 'Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a6fc193ba73c040042e7d19d5b86f0acf61e69ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint
  Die folgenden Verfahren veranschaulichen, wie Sie benutzerdefinierte Websitespalten in SharePoint erstellen – oder *Felder*– sowie einen Inhaltstyp, der die Websitespalten verwendet. Es wird gezeigt, wie eine Liste zu erstellen, die den neuen Inhaltstyp verwendet, werden.  
  
 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:  
  
-   [Erstellen benutzerdefinierte Websitespalten](#BKMK_CreatingCustSiteCols).  
  
-   [Erstellen einen benutzerdefinierten Inhaltstyp](#BKMK_CreateCustContType).  
  
-   [Erstellen eine Liste](#BKMK_CreateList).  
  
-   [Erstellen eine Liste](#BKMK_CreateList).  
  
-   [Testen der Anwendung](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Erstellen benutzerdefinierte Websitespalten  
 In diesem Beispiel wird eine Liste für die Verwaltung von Patienten, die in einem Krankenhaus erstellt. Sie müssen zunächst in einer SharePoint-Projekt erstellen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und Hinzufügen von Websitespalten, wie folgt.  
  
#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt  
  
1.  Auf der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Datei** Menü wählen **neu**, **Projekt**.  
  
2.  In der **neues Projekt** im Dialogfeld unter entweder **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann **2010**.  
  
3.  In der **Vorlagen** Bereich auswählen **SharePoint 2010-Projekt**, ändern Sie den Namen des Projekts, um **Clinic**, und wählen Sie dann die **OK** Schaltfläche ".  
  
     Die SharePoint 2010-Projektvorlage wird ein leeres Projekt, das in diesem Beispiel verwendet wird, enthalten, Websitespalten sowie andere Projektelemente, die später hinzugefügt werden.  
  
4.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite Geben Sie die URL für die lokale SharePoint-Website, die Sie die neue benutzerdefinierte Feldelement hinzufügen möchten, oder verwenden den Standardspeicherort (`http://<`*SystemName* `>/)`.  
  
5.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt, verwenden Sie den Standardwert **bereitstellen als sandkastenlösung**.  
  
     Weitere Informationen zu Sandbox und farmlösungen, finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Wählen Sie die **Fertig stellen** Schaltfläche. Das Projekt sollte nun aufgelistet werden **Projektmappen-Explorer**.  
  
#### <a name="to-add-site-columns"></a>Websitespalten hinzufügen  
  
1.  Fügen Sie eine neue Websitespalte hinzu. Klicken Sie hierzu in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Clinic**, und wählen Sie dann **hinzufügen**, **neues Element**.  
  
2.  In der **neues Element hinzufügen** Dialogfeld Wählen Sie **Websitespalte**, ändern Sie den Namen in **Patient Name**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
3.  Lassen Sie in der Datei "Elements.xml" der Websitespalte, den **Typ** festlegen als **Text**, und ändern Sie die **Gruppe** festlegen auf **Clinic Websitespalten**. Nach Abschluss des Vorgangs sollte die Websitespalte "Elements.xml"-Datei im folgenden Beispiel ähneln.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Dieselbe Prozedur, mit dem Projekt zwei weitere Websitespalten hinzugefügt: **Patienten-ID** (Typ = "Integer") und **Doctor Namen** (Type = "Text"). Legen Sie deren Wert Gruppe **Clinic Websitespalten**.  
  
##  <a name="BKMK_CreateCustContType"></a> Erstellen einen benutzerdefinierten Inhaltstyp  
 Als Nächstes erstellen Sie einen Inhaltstyp – basierend auf den Inhaltstyp Kontakte –, enthält der Websitespalten, die Sie im vorherigen Verfahren erstellt haben. Durch einen Inhaltstyp auf einen vorhandenen Inhaltstyp basieren, können Sie Zeit sparen, da die grundlegende Inhaltstyp für die Verwendung in der neue Inhaltstyp mehrere Websitespalten bereitstellt.  
  
#### <a name="to-create-a-custom-content-type"></a>So erstellen einen benutzerdefinierten Inhaltstyp  
  
1.  Fügen Sie dem Projekt einen Inhaltstyp hinzu. Klicken Sie hierzu in **Projektmappen-Explorer**, wählen Sie den Projektknoten aus  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
3.  Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  In der **Vorlagen** Bereich, wählen Sie die **Inhaltstyp** Vorlage, ändern Sie den Namen in **Patientendaten**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** wird geöffnet.  
  
5.  In der **welche grundlegenden Inhaltstyp sollten diesen Inhaltstyp Vererben** wählen Sie **wenden Sie sich an** als den Inhaltstyp auf dem den neuen Inhaltstyp basieren, und wählen Sie dann die **Fertig stellen**Schaltfläche.  
  
     Auf diese Weise erhalten Sie Zugriff auf andere potenziell nützliche Websitespalten in den Inhaltstyp "Kontakt", zusätzlich zu den Websitespalten, die Sie zuvor definiert.  
  
6.  Nach dem Inhaltstyp-Designer wird angezeigt, in der **Spalten** Registerkarte, die drei Spalten, die Sie zuvor definierten site hinzufügen: **Patient Name**, **Patienten-ID**, und **Doctor Namen**. Um diese Spalten hinzuzufügen, wählen Sie im Listenfeld erste in der Liste der Spalten Website unter **Anzeigenamen**, und wählen Sie dann jede Spalte in der Liste einen zu einem Zeitpunkt.  
  
    > [!TIP]  
    >  Filtern Sie die Liste der Websitespalten schneller aus, durch die ersten Buchstaben des Namens der Spalte eingeben.  
  
7.  Zusätzlich zu den drei benutzerdefinierte Websitespalten, Hinzufügen der **Kommentare** Websitespalte aus der Liste der Site-Spalten.  
  
8.  Wählen Sie die **erforderlich** Kontrollkästchen für die **Patient Name** und **Patienten-ID** Pflichtfelder für Websitespalten zu machen.  
  
9. Auf der **Inhaltstyp** Registerkarte, stellen Sie sicher, dass der Content-Type-Name ist **Patientendaten**, und ändern Sie die Beschreibung **Patienteninformationen Karte**.  
  
10. Änderung **Gruppenname** auf **Clinic Inhaltstypen**, und behalten Sie die Standardwerte für die anderen Einstellungen.  
  
11. Wählen Sie in der Menüleiste **Datei**, **alle speichern**, und schließen Sie den Content-Type-Designer.  
  
##  <a name="BKMK_CreateList"></a> Erstellen einer Liste  
 Erstellen Sie jetzt eine Liste, die die neuen Typ und Standort Inhaltsspalten verwendet.  
  
#### <a name="to-create-a-list"></a>Um eine Liste erstellen  
  
1.  Fügen Sie eine Liste, um das Projekt. Klicken Sie hierzu in **Projektmappen-Explorer**, wählen Sie den Projektknoten aus.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
3.  Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  In der **Vorlagen** Bereich, wählen Sie die **Liste** Vorlage, ändern Sie den Namen in **Patienten**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
5.  Lassen Sie die **passen Sie die Liste basierend auf** festlegen als **Standard (leer)**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
6.  Wählen Sie in der Liste-Designer die **Inhaltstypen** Schaltfläche zum Anzeigen der **Inhaltseinstellungen für den Typ** (Dialogfeld).  
  
7.  Wählen Sie die neue Zeile, wählen Sie die **Patientendaten** Inhaltstyp in die Liste der Inhaltstypen, und wählen Sie dann die **OK** Schaltfläche.  
  
     Dies fügt alle Standort Spalten aus der **Patientendaten** Inhaltstyp in die Liste.  
  
8.  Löschen Sie alle Websitespalten in der Liste mit Ausnahme der folgenden:  
  
    -   Patienten-ID  
  
    -   Name des Patienten  
  
    -   Telefon privat  
  
    -   -E-Mail  
  
    -   Doctor Name  
  
    -   Kommentare  
  
9. Klicken Sie unter **Spalte Anzeigename**, wählen Sie eine leere Zeile, fügen Sie eine benutzerdefinierte Liste-Spalte, und nennen Sie sie **Krankenhaus**. Lassen Sie die Angabe des Datentyps als **Textzeile**.  
  
     Die benutzerdefinierte Listenspalte gilt nur für diese Liste. Wenn Sie eine benutzerdefinierte Listenspalte zu einer Liste hinzufügen, wird ein neue Listeninhaltstyp, einschließlich der Spalten, die in der Liste hinzugefügt erstellt und als die Standardliste festlegen.  
  
    > [!TIP]  
    >  Wenn Sie eine Spalte aus der Liste der Websitespalten auswählen, wird eine vorhandene Websitespalte verwendet. Jedoch wenn Sie einen Wert aus der Namen eingeben, ohne alle Spalten in der Liste auswählen, wird eine benutzerdefinierte Listenspalte erstellt, selbst wenn eine Spalte mit dem gleichen Namen bereits in der Liste vorhanden ist.  
  
     Optional, anstatt den Datentyp für die benutzerdefinierte Listenspalte festlegen **Textzeile**, konnte Sie stattdessen den Datentyp für diese Spalte festlegen, für die Suche und seine Werte aus einer Tabelle oder einer anderen Liste abgerufen werden. Informationen zu Suchspalten finden Sie unter [Liste Beziehungen in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) und [Suchvorgänge und Liste Beziehungen](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Neben den **Patienten-ID** und **Patient Name** Dialogfelder, wählen die **erforderlich** Kontrollkästchen.  
  
11. Auf der **Ansichten** Registerkarte, und wählen Sie eine leere Zeile, um eine Ansicht zu erstellen. Geben Sie **Patientendetails**.  
  
     Auf der **Ansichten** Registerkarte können Sie die Spalten, die in der SharePoint-Liste angezeigt werden sollen angeben.  
  
12. Wählen Sie das neue **Patienten Details** Zeile aus, und wählen Sie dann die **als Standard festlegen** Schaltfläche.  
  
     Die neue Ansicht wird nun die Standardansicht für die Liste.  
  
13. Fügen Sie die folgenden Spalten auf die **ausgewählte Spalten** Liste in der folgenden Reihenfolge:  
  
    -   Patienten-ID  
  
    -   Name des Patienten  
  
    -   Telefon privat  
  
    -   -E-Mail  
  
    -   Doctor Name  
  
    -   Krankenhaus  
  
    -   Kommentare  
  
14. In der **Eigenschaften** wählen Sie die **sortieren und Gruppieren** -Eigenschaft, und wählen Sie dann die Schaltfläche mit den Auslassungspunkten ![Symbol "Ellipse"](../sharepoint/media/ellipsisicon.gif "Symbol "Ellipse"")zum Anzeigen der **sortieren und Gruppieren** (Dialogfeld).  
  
15. In der **Spaltenname** wählen Sie **Patient Name**, stellen Sie sicher, dass die **sortieren** Spalte **aufsteigend**, und wählen Sie dann die  **OK** Schaltfläche.  
  
##  <a name="BKMK_TestApp"></a> Testen der Anwendung  
 Nun, dass die benutzerdefinierte Websitespalten, Inhaltstyp und Liste bereit sind, für SharePoint bereitstellen Sie, und führen Sie die Anwendung testen.  
  
#### <a name="to-test-the-application"></a>So testen Sie die Anwendung  
  
1.  Wählen Sie in der Menüleiste die Option **Datei**, **Alle speichern** aus.  
  
2.  Drücken Sie die Taste F5, um die Anwendung auszuführen.  
  
     Die Anwendung kompiliert wird, und klicken Sie dann die Funktionen für SharePoint bereitgestellt und aktiviert sind.  
  
3.  Wählen Sie auf der Navigationsleiste schnell die **Patienten** Link zum Anzeigen der **Patienten** Liste.  
  
     Die Spaltennamen in der Liste übereinstimmen, die Sie eingegeben haben, auf die **Ansichten** Registerkarte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Wählen Sie die **neues Element hinzufügen** Link zu eine Karte Patienteninformationen zu erstellen.  
  
5.  Geben Sie Informationen in die Felder aus, und wählen Sie dann die **speichern** Schaltfläche.  
  
     Der neue Datensatz wird in der Liste angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Vorgehensweise: erstellen ein benutzerdefinierten Felds vom Typ](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Inhaltstypen](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Spalten](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  