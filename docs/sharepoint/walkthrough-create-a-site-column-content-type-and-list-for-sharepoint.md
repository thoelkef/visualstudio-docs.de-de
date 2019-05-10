---
title: 'Exemplarische Vorgehensweise: Erstellen einer Websitespalte, Inhaltstyp und die Liste für SharePoint | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e39ea4041ab9806c7ca857680af5c5c04510eba9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430697"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint
  Die folgenden Prozeduren veranschaulichen, wie Sie benutzerdefinierte SharePoint-Websitespalten erstellen – oder *Felder*– sowie einen Inhaltstyp, der die Websitespalten verwendet. Es wird gezeigt, wie eine Liste zu erstellen, die den neuen Inhaltstyp verwendet.

 Diese exemplarische Vorgehensweise umfasst die folgenden Aufgaben:

- [Erstellen Sie benutzerdefinierte Websitespalten](#create-custom-site-columns).

- [Erstellen Sie einen benutzerdefinierten Inhaltstyp](#create-a-custom-content-type).

- [Erstellen Sie eine Liste](#create-a-list).

- [Testen Sie die Anwendung](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von Windows und SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Erstellen Sie benutzerdefinierte Websitespalten
 Dieses Beispiel erstellt eine Liste für die Verwaltung von Patienten in einem Krankenhaus. Erstellen Sie zuerst, eine SharePoint-Projekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und Websitespalten, wie folgt hinzufügen.

#### <a name="to-create-the-project"></a>So erstellen Sie das Projekt

1. Auf der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Datei** Menü wählen **neu** > **Projekt**.

2. In der **neues Projekt** im Dialogfeld unter entweder **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann auf **2010**.

3. In der **Vorlagen** Bereich wählen **SharePoint 2010-Projekt**, ändern Sie den Namen des Projekts, das **Clinic**, und wählen Sie dann die **OK** Schaltfläche ".

     Die SharePoint 2010-Projektvorlage wird ein leeres Projekt, das in diesem Beispiel verwendet wird, enthält die Websitespalten und andere Projektelemente, die später hinzugefügt werden.

4. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite Geben Sie die URL für die lokale SharePoint-Website, zu dem Sie das neue Element für benutzerdefiniertes Feld hinzufügen möchten, oder verwenden Sie den Standardspeicherort (`http://<`*SystemName* `>/)`.

5. In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt können Sie den Standardwert **als sandkastenlösung bereitstellen**.

     Weitere Informationen zu sandkastenlösungen und farmlösungen, finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).

6. Wählen Sie die **Fertig stellen** Schaltfläche. Das Projekt wird jetzt aufgeführt, **Projektmappen-Explorer**.

#### <a name="to-add-site-columns"></a>Websitespalten hinzufügen

1. Fügen Sie eine neue Websitespalte hinzu. Klicken Sie hierzu in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für **Clinic**, und wählen Sie dann **hinzufügen** > **neues Element**.

2. In der **neues Element hinzufügen** Dialogfeld wählen **Websitespalte**, ändern Sie den Namen in **Patient Name**, und wählen Sie dann die **hinzufügen** Schaltfläche.

3. In der Websitespalte *"Elements.xml"* Datei, lassen Sie die **Typ** festlegen als **Text**, und ändern Sie die **Gruppe** auf  **Technologieüberblick Websitespalten**. Wenn Sie fertig sind, der Websitespalte *"Elements.xml"* Datei sollte wie im folgenden Beispiel aussehen.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="Clinic - Patient Name"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

4. Verwenden das gleiche Verfahren an, fügen Sie zwei zusätzliche Websitespalten zum Projekt hinzu: **Patienten-ID** (Type = "Integer") und **Doktor Namen** (Type = "Text"). Legen Sie den Wert ihrer Gruppe **Clinic Websitespalten**.

## <a name="create-a-custom-content-type"></a>Erstellen Sie einen benutzerdefinierten Inhaltstyp
 Als Nächstes erstellen Sie einen Inhaltstyp, basierend auf den Inhaltstyp der Kontakte –, enthält die Websitespalten, die Sie im vorherigen Verfahren erstellt haben. Von einem Inhaltstyp auf einem vorhandenen Inhaltstyp basieren, können Sie Zeit sparen, da vom grundlegende Inhaltstyp für die Verwendung in den neuen Inhaltstyp stellt mehrere Websitespalten bereit.

#### <a name="to-create-a-custom-content-type"></a>Um einen benutzerdefinierten Inhaltstyp zu erstellen.

1. Fügen Sie dem Projekt einen Inhaltstyp hinzu. Klicken Sie hierzu in **Projektmappen-Explorer**, wählen Sie den Knoten des Projekts

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

4. In der **Vorlagen** Bereich Wählen Sie die **Inhaltstyp** Vorlage ändern den Namen in **Patientendaten**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Die **SharePoint Customization Wizard** wird geöffnet.

5. In der **welche Basisinhaltstyp soll dieser Inhaltstyp erben** wählen **wenden Sie sich an** als Inhaltstyp auf der Basis des neuen Inhaltstyps, und wählen Sie dann die **Fertig stellen**Schaltfläche.

     Dadurch erhalten Sie Zugriff auf andere möglicherweise nützlicher Websitespalten in den Inhaltstyp "Kontakt", zusätzlich zu den Websitespalten, die Sie zuvor definiert.

6. Nach dem Inhaltstyp-Designer angezeigt wird, in der **Spalten** Registerkarte, fügen Sie die drei Spalten, die Sie zuvor definiert site hinzu: **Name des Patienten**, **Patienten-ID**, und **Doktor Namen**. Um diese Spalten hinzuzufügen, wählen Sie das erste Listenfeld in der Liste der Spalten Site unter **Anzeigenamen**, und wählen Sie dann jede Spalte in der Liste eine zu einem Zeitpunkt.

    > [!TIP]
    > Um die Websitespalten schneller auswählen, wird die Liste durch die ersten paar Buchstaben des Namens der Spalte Eingabe gefiltert.

7. Zusätzlich zu den drei benutzerdefinierte Websitespalten hinzufügen, die **Kommentare** Websitespalte aus der Liste der Site-Spalten.

8. Wählen Sie die **erforderlichen** Kontrollkästchen für die **Patient Name** und **Patienten-ID** Websitespalten, um sie zu machen, erforderliche Felder.

9. Auf der **Inhaltstyp** Registerkarte, stellen Sie sicher, dass der Content-Type-Name ist **Patientendaten**, und ändern Sie dann auf die Beschreibung, **Patienten Informationskarte**.

10. Änderung **Gruppenname** zu **Clinic Inhaltstypen**, und lassen Sie die anderen Einstellungen die Standardwerte bei.

11. Wählen Sie auf der Menüleiste **Datei** > **Alles speichern**, und schließen Sie dann den Content-Type-Designer.

## <a name="create-a-list"></a>Erstellen Sie eine Liste
 Erstellen Sie jetzt eine Liste, die die neuen Typ und Standort Inhaltsspalten verwendet.

#### <a name="to-create-a-list"></a>Um eine Liste erstellen

1. Fügen Sie eine Liste, um das Projekt. Klicken Sie hierzu in **Projektmappen-Explorer**, wählen Sie den Projektknoten aus.

2. Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.

3. Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

4. In der **Vorlagen** Bereich, wählen Sie die **Liste** Vorlage ändern den Namen in **Patienten**, und wählen Sie dann die **hinzufügen** Schaltfläche.

5. Lassen Sie die **Anpassen der Liste auf der Grundlage** als **Standardwert (leer)**, und wählen Sie dann die **Fertig stellen** Schaltfläche.

6. Wählen Sie im Designer Liste der **Inhaltstypen** anzuzeigenden Schaltfläche die **Inhaltseinstellungen Typ** im Dialogfeld.

7. Wählen Sie die neue Zeile, wählen Sie die **Patientendaten** Inhaltstyp in der Liste der Inhaltstypen aus, und wählen Sie dann die **OK** Schaltfläche.

     Dies fügt alle hinzu, die Websitespalten aus der **Patientendaten** Inhaltstyp in der Liste.

8. Löschen Sie alle Websitespalten in der Liste mit Ausnahme der folgenden:

    - Patienten-ID

    - Name des Patienten

    - Telefon (privat)

    - E-Mail

    - Doktor-Name

    - Kommentare

9. Klicken Sie unter **Anzeigename der Spalte**, wählen Sie eine leere Zeile, fügen Sie eine benutzerdefinierte Liste-Spalte, und nennen sie **Krankenhaus**. Lassen Sie den Datentyp als **einzelne Textzeile**.

     Die der benutzerdefinierten Listenspalte gilt nur für diese Liste. Wenn Sie eine der benutzerdefinierten Listenspalte zu einer Liste hinzufügen, ein neuen Listeninhaltstyp, einschließlich aller Spalten in der Liste hinzugefügt erstellt und als die Standardliste festgelegt.

    > [!TIP]
    > Wenn Sie eine Spalte aus der Liste der Websitespalten auswählen, wird eine bestehende Websitespalte verwendet. Jedoch wenn Sie einen Spalte Name-Wert eingeben, ohne alle Spalten in der Liste auswählen, wird eine benutzerdefinierte Liste-Spalte erstellt, selbst wenn eine Spalte mit dem gleichen Namen bereits in der Liste vorhanden ist.

     Optional, statt den Datentyp für die benutzerdefinierte Listenspalte **einzelne Textzeile**, Sie können den Datentyp für diese Spalte stattdessen für die Suche festlegen und ihre Werte aus einer Tabelle oder einer anderen Liste abgerufen werden sollen. Informationen über die Suchspalten, finden Sie unter [Liste-Beziehungen in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) und [Suchvorgänge und Liste Beziehungen](http://go.microsoft.com/fwlink/?LinkID=224995).

10. Neben der **Patienten-ID** und **Patient Name** Dialogfelder, wählen die **erforderlich** Kontrollkästchen.

11. Auf der **Ansichten** Registerkarte, und wählen Sie eine leere Zeile, um eine Sicht erstellen. Geben Sie **Patientendetails**.

     Auf der **Ansichten** Registerkarte, Sie können die Spalten angeben, die Sie in der SharePoint-Liste angezeigt werden soll.

12. Wählen Sie den neuen **Patienten Details** Zeile aus, und wählen Sie dann die **als Standard festlegen** Schaltfläche.

     Die neue Ansicht ist jetzt die Standardansicht für die Liste.

13. Fügen Sie die folgenden Spalten auf die **Selected Columns** Liste in der folgenden Reihenfolge:

    - Patienten-ID

    - Name des Patienten

    - Telefon (privat)

    - E-Mail

    - Doktor-Name

    - Krankenhaus

    - Kommentare

14. In der **Eigenschaften** wählen die **sortieren und Gruppieren von** -Eigenschaft, und wählen Sie dann die Schaltfläche mit den Auslassungspunkten ![Symbol "Ellipse"](../sharepoint/media/ellipsisicon.gif "Symbol \"Ellipse\"")zum Anzeigen der **sortieren und Gruppieren von** Dialogfeld.

15. In der **Spaltenname** wählen **Patient Name**, stellen Sie sicher, dass die **Sortierung** Spalte **aufsteigend**, und wählen Sie dann die  **OK** Schaltfläche.

## <a name="test-the-application"></a>Testen der Anwendung
 Nun, dass die benutzerdefinierte Websitespalten, Inhaltstyp und Liste bereit sind, auf SharePoint bereitzustellen Sie, und führen Sie die Anwendung testen.

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Klicken Sie in der Menüleiste auf **Datei** > **Alle speichern**.

2. Wählen Sie die **F5** Taste, um die Anwendung auszuführen.

     Die Anwendung kompiliert wird, und klicken Sie dann die Funktionen in SharePoint bereitgestellt und aktiviert werden.

3. Wählen Sie auf der Navigationsleiste schnell die **Patienten** Link zum Anzeigen der **Patienten** Liste.

     Die Spaltennamen in der Liste sollte übereinstimmen, die Sie eingegeben haben, auf die **Ansichten** Registerkarte [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

4. Wählen Sie die **neues Element hinzufügen** Link zum Erstellen einer Karte Patientendaten.

5. Geben Sie die Informationen in die Felder aus, und wählen Sie dann die **speichern** Schaltfläche.

     Der neue Datensatz wird in der Liste angezeigt.

## <a name="see-also"></a>Siehe auch
- [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Vorgehensweise: Erstellen eines benutzerdefinierten Feldtyps](http://go.microsoft.com/fwlink/?LinkId=192079)
- [Inhaltstypen](http://go.microsoft.com/fwlink/?LinkId=192080)
- [Spalten](http://go.microsoft.com/fwlink/?LinkId=192081)
