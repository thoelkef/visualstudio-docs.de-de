---
title: "Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste f&#252;r SharePoint"
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
  - "VS.SharePointTools.ListDesigner.GeneralMessageHelp"
  - "Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping"
  - "VS.SharePointTools.ListDesigner.SortingGrouping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Inhaltstypen"
  - "SharePoint-Entwicklung in Visual Studio, Felder"
  - "SharePoint-Entwicklung in Visual Studio, Listendefinitionen"
  - "SharePoint-Entwicklung in Visual Studio, Listeninstanzen"
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste f&#252;r SharePoint
  Die folgenden Prozeduren veranschaulichen, wie benutzerdefinierte Spalte\- oder SharePoint\-Website *Feld\-wie* optimal als Inhaltstyp erstellt, der die Websitespalten verwendet.  Es zeigt auch, wie eine Liste erstellt, die den neuen Inhaltstyp verwendet.  
  
 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:  
  
-   [Erstellen benutzerdefinierter Websitespalten](#BKMK_CreatingCustSiteCols).  
  
-   [Erstellen eines benutzerdefinierten Inhaltstyps](#BKMK_CreateCustContType).  
  
-   [Erstellen einer Liste](#BKMK_CreateList).  
  
-   [Erstellen einer Liste](#BKMK_CreateList).  
  
-   [Testen der Anwendung](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Erstellen benutzerdefinierter Websitespalten  
 Dieses Beispiel erstellt eine Liste für das Verwalten von Patienten in ein Krankenhaus.  Zuerst müssen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein SharePoint\-Projekt erstellen und Websitespalten hinzufügen, wie folgt.  
  
#### So erstellen Sie das Projekt  
  
1.  Klicken Sie im Menü [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**Datei** wählen Sie **Projekt**, **Neu** aus.  
  
2.  Im Dialogfeld **Neues Projekt** entweder unter **Visual C\#** oder **Visual Basic**, erweitern Sie den Knoten **SharePoint**, und wählen Sie dann **2010** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie **SharePoint 2010\-Projekt** aus, ändern Sie den Namen des Projekts zur Klinik, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     In SharePoint 2010\-Projektvorlage ist ein leeres Projekt, in diesem Beispiel verwendet wird, um Websitespalten und andere Projektelemente enthalten, die später hinzugefügt werden.  
  
4.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie die URL für die lokale SharePoint\-Standardwebsite, der Sie das neue benutzerdefinierte Feldelement hinzufügen möchten, oder verwenden Sie den Standardspeicherort \(`http://<`*SystemName*`>/)`.  
  
5.  Verwenden Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** den Standardwert **Als Sandkastenlösung bereitstellen**.  
  
     Weitere Informationen zu Sandkastenlösungen und Farmlösungen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Wählen Sie die Schaltfläche **Fertig stellen** aus.  Das Projekt sollte im **Projektmappen\-Explorer** jetzt aufgeführt werden.  
  
#### So Websitespalten hinzufügen  
  
1.  Fügen Sie eine neue Websitespalte hinzu.  Dazu, **Projektmappen\-Explorer** auszuführen, öffnen das Kontextmenü **Klinik** und wählen dann, **HinzufügenNeues Element** aus.  
  
2.  Im Dialogfeld **Neues Element hinzufügen** wählen Sie **Websitespalte** aus, ändern Sie den Namen in geduldigen Namen, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
3.  In der Datei Elements.xml der Websitespalte belassen Sie die Einstellung **Typ** als **Text**, und ändern Sie die Einstellung **Gruppe** zu den Klinik\-Websitespalten.  Wenn vollständig, sollte die Datei Elements.xml der Websitespalte, wie im folgenden Beispiel entsprechen.  
  
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
  
4.  Verwenden derselben Prozedur fügen Sie zwei anderen Websitespalten dem Projekt hinzu: Geduldige ID \(Typ \= "Integer"\) und Doctor Name \(Typ \= "Text"\).  Legen Sie ihre Gruppenwert auf Klinik\-Websitespalten fest.  
  
##  <a name="BKMK_CreateCustContType"></a> Erstellen eines benutzerdefinierten Inhaltstyps  
 Erstellen Sie anschließend einen Inhalt, der auf dem Kontaktinhalt Typ\-dass gehören die typbasiert Websitespalten ist, die Sie in der vorherigen Prozedur erstellt haben.  Indem Sie einen Inhaltstyp auf einem vorhandenen Inhaltstyp basieren, können Sie Zeit sparen, da der Basisinhaltstyp einige Websitespalten zur Verwendung in neuen Inhaltstyp.  
  
#### So erstellen Sie einen benutzerdefinierten Inhaltstyp  
  
1.  Fügen Sie dem Projekt einen Inhaltstyp hinzu.  Hierzu, **Projektmappen\-Explorer** auszuführen, wählen Sie den Projektknoten  
  
2.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
3.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie den Knoten **2010** aus.  
  
4.  Im Bereich **Vorlagen** wählen Sie die Vorlage **Inhaltstyp** aus, ändern Sie den Namen den geduldigen Informationen, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     **Assistent zum Anpassen von SharePoint** wird geöffnet.  
  
5.  In der Liste **Von welchem Basisinhaltstyp soll dieser Inhaltstyp erben** wählen Sie als Inhaltstyp **Kontakt** auf den neuen Inhaltstyp basieren, und die Schaltfläche **Fertig stellen** auswählen.  
  
     Hierdurch erhalten Sie Zugriff auf nützliche Websitespalten anderen möglicherweise im Kontaktinhaltstyp, neben den Websitespalten, die Sie vorher definiert haben.  
  
6.  Nachdem der Inhaltstypdesigner, auf der Registerkarte **Spalten** angezeigt wird, fügen Sie die drei Websitespalten hinzu, die Sie vorher definiert haben: **Patientenname**, **Patienten\-ID** und **Name des Arztes**.  Um diese Spalten hinzuzufügen, wählen Sie das erste Listenfeld in der Websitespaltenliste unter **Anzeigename**, und wählen Sie dann alle berichtenden Websitespalte in der Liste nacheinander aus.  
  
    > [!TIP]  
    >  Um der Websitespalten schneller auszuwählen, filtern Sie die Liste mit dem ersten Buchstaben des Namens der Spalte eingeben.  
  
7.  Neben den drei benutzerdefinierten Websitespalten Fügen Sie der **Kommentare** von der Websitespaltenliste Websitespalte hinzu.  
  
8.  Aktivieren Sie das Kontrollkästchen **Erforderlich** damit die **Patientenname** und **Patienten\-ID** Websitespalten sie Pflichtfelder machen.  
  
9. Auf der Registerkarte **Inhaltstyp**, überprüfen Sie, ob der Name des Inhaltstyps **Patienteninfo** ist, und ändern Sie dann die Beschreibung der geduldigen Informationskarte.  
  
10. Ändern Sie **Gruppenname** in den Klinik\-Inhaltstypen, und lassen Sie die Standardwerte für die anderen Einstellungen.  
  
11. Wählen Sie in der Menüleiste, **Alle speichern**, **Datei** aus und schließen Sie dann den Inhaltstypdesigner.  
  
##  <a name="BKMK_CreateList"></a> Erstellen einer Liste  
 Jetzt erstellen Sie eine Liste, die den neuen Inhaltstyp und die Websitespalten verwendet.  
  
#### Um eine Liste erstellen  
  
1.  Hinzufügen einer Liste hinzu.  Hierzu, **Projektmappen\-Explorer** auszuführen, wählen Sie den Projektknoten.  
  
2.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
3.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie den Knoten **2010** aus.  
  
4.  Im Bereich **Vorlagen** wählen Sie die Vorlage **Liste** aus, ändern Sie den Namen für Patienten, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
5.  Übernehmen Sie die Einstellung **Liste anpassen anhand von** als **Standard \(leer\)**, und wählen Sie die Schaltfläche **Fertig stellen** aus.  
  
6.  Im Listen\-Designer wählen Sie die Schaltfläche **Inhaltstypen**, um das Dialogfeld **Inhaltstypeinstellungen** anzuzeigen.  
  
7.  Wählen Sie die neue Zeile, wählen den Inhaltstyp **Patienteninfo** in der Liste von Inhaltstypen, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Das transitive, fügt alle Websitespalten vom Inhaltstyp **Patienteninfo** in der Liste hinzu.  
  
8.  Löschen Sie alle Websitespalten in der Liste mit Ausnahme des folgenden:  
  
    -   Patienten\-ID  
  
    -   Patientenname  
  
    -   Privat Telefon  
  
    -   E\-Mail  
  
    -   Name des Arztes  
  
    -   Kommentare  
  
9. Wählen Sie unter **Anzeigename der Spalte** eine leere Zeile aus, fügen Sie eine benutzerdefinierte Listenspalte hinzu, und benennen Sie sie Krankenhaus.  Lassen Sie dessen Datentyp als **Eine Textzeile**.  
  
     Die benutzerdefinierte Listenspalte gilt nur für diese Liste zu.  Wenn Sie eine benutzerdefinierte Listenspalte einer Liste hinzufügen, wird ein neuer Listeninhaltstyp, einschließlich aller Spalten, die in der Liste hinzugefügt werden, während der Standardliste erstellt und festgelegt.  
  
    > [!TIP]  
    >  Wenn Sie eine Spalte aus der Liste der Websitespalten auswählen, wird eine vorhandene Websitespalte verwendet.  Wenn Sie jedoch einen Spaltennamenwert eingeben, ohne Spalten in der Liste auszuwählen, wird eine benutzerdefinierte Listenspalte erstellt, wenn eine Spalte mit dem gleichen Namen bereits in der Liste vorhanden ist.  
  
     Optional, anstatt den Datentyp für die benutzerdefinierte Listenspalte auf **Eine Textzeile** festgelegt wird, können Sie den Datentyp für diese Spalte auf Suchen stattdessen festlegen, und die Werte werden aus einer Tabelle oder aus anderen Liste abgerufen.  Informationen über keine Suchspalten, finden Sie und [Listen\-Beziehungen in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) [Suchen und Listen\-Beziehungen](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Neben den Feldern **Patienten\-ID** und **Patientenname** aktivieren Sie das Kontrollkästchen **Erforderlich**.  
  
11. Auf der Registerkarte **Ansichten** wählen Sie eine leere Zeile, eine Ansicht zu erstellen.  Geben Sie geduldigen Informationen ein.  
  
     Auf der Registerkarte **Ansichten** können Sie die Spalten angeben, dass Sie in der SharePoint\-Liste angezeigt werden sollen.  
  
12. Wählen Sie die neue Zeile **Patientendetails**, und wählen Sie dann die Schaltfläche **Als Standard** aus.  
  
     Die neue Ansicht ist nun die Standardansicht für die Liste.  
  
13. Fügen Sie den folgenden Spalten der Liste **Ausgewählte Spalten** in der folgenden Reihenfolge hinzu:  
  
    -   Patienten\-ID  
  
    -   Patientenname  
  
    -   Privat Telefon  
  
    -   E\-Mail  
  
    -   Name des Arztes  
  
    -   Krankenhaus  
  
    -   Kommentare  
  
14. In der Liste **Eigenschaften** wählen Sie die Eigenschaft **Sortieren und gruppieren** aus, und wählen Sie die Schaltfläche mit den ![Symbol "Ellipse"](~/sharepoint/media/ellipsisicon.gif "Symbol "Ellipse"") Auslassungszeichen, um das Dialogfeld **Sortieren und gruppieren** anzuzeigen.  
  
15. In der Liste **Spaltenname** wählen Sie **Patientenname** aus, überprüfen Sie, ob die Spalte, **Sortieren** auf **Aufsteigend** festgelegt ist, und wählen Sie dann die Schaltfläche **OK** aus.  
  
##  <a name="BKMK_TestApp"></a> Testen der Anwendung  
 Da die benutzerdefinierte Websitespalten, Inhaltstyp und die Liste bereit sind, stellen Sie sie in SharePoint bereit, und führen Sie die Anwendung aus, sie zu testen.  
  
#### So testen Sie die Anwendung  
  
1.  Wählen Sie in der Menüleiste die Option **Datei**, **Alle speichern** aus.  
  
2.  Drücken Sie die Taste F5, um die Anwendung auszuführen.  
  
     Die Anwendung wurde kompiliert und anschließend werden deren Funktionen für SharePoint bereitgestellt und aktiviert.  
  
3.  Auf der Entwicklungszeit Navigationsleiste wählen Sie den Link **Patienten**, um die Liste **Patienten** anzuzeigen.  
  
     Die Spaltennamen in der Liste sollten die übereinstimmen, die Sie auf der Registerkarte **Ansichten** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eingeben.  
  
4.  Wählen Sie den Link **Neues Element hinzufügen**, um eine geduldige Informationskarte zu erstellen.  
  
5.  Geben Sie Informationen in die Felder ein, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
     Der neue Datensatz wird in der Liste.  
  
## Siehe auch  
 [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Gewusst wie: Erstellen Sie einen benutzerdefinierten Feldtyp](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Inhaltstypen](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Columns](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  