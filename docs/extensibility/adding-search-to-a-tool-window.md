---
title: Hinzufügen der Suche zu einem Toolfenster | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740137"
---
# <a name="add-search-to-a-tool-window"></a>Suchen zu einem Toolfenster hinzufügen
Wenn Sie ein Toolfenster in Ihrer Erweiterung erstellen oder aktualisieren, können Sie dieselbe Suchfunktion hinzufügen, die an anderer Stelle in Visual Studio angezeigt wird. Diese Funktionalität umfasst die folgenden Funktionen:

- Ein Suchfeld, das sich immer in einem benutzerdefinierten Bereich der Symbolleiste befindet.

- Ein Fortschrittsindikator, der auf dem Suchfeld selbst überlagert ist.

- Die Möglichkeit, Ergebnisse anzuzeigen, sobald Sie jedes Zeichen eingeben (Sofortsuche) oder erst, nachdem Sie den **Eingabeschlüssel** ausgewählt haben (Suche bei Bedarf).

- Eine Liste, die Begriffe anzeigt, nach denen Sie zuletzt gesucht haben.

- Die Möglichkeit, Suchen nach bestimmten Feldern oder Aspekten der Suchziele zu filtern.

Anhand dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:

1. Erstellen Sie ein VSPackage-Projekt.

2. Erstellen Sie ein Toolfenster, das ein UserControl mit einer schreibgeschützten TextBox enthält.

3. Fügen Sie dem Toolfenster ein Suchfeld hinzu.

4. Fügen Sie die Suchimplementierung hinzu.

5. Aktivieren Sie die sofortige Suche und Anzeige einer Fortschrittsleiste.

6. Fügen Sie eine **Match-Fall-Option** hinzu.

7. Fügen Sie einen **Such-Geraden-Linien-Filter hinzu.**

## <a name="to-create-a-vsix-project"></a>So erstellen Sie ein VSIX-Projekt

1. Erstellen Sie ein `TestToolWindowSearch` VSIX-Projekt mit dem Namen mit einem Toolfenster mit dem Namen **TestSearch**. Wenn Sie Hilfe benötigen, finden Sie weitere Informationen unter [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>So erstellen Sie ein Toolfenster

1. Öffnen `TestToolWindowSearch` Sie im Projekt die Datei *TestSearchControl.xaml.*

2. Ersetzen Sie `<StackPanel>` den vorhandenen Block durch den folgenden <xref:System.Windows.Controls.TextBox> Block, der dem <xref:System.Windows.Controls.UserControl> im Werkzeugfenster schreibgeschützt hinzufügt.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Fügen Sie in der *Datei TestSearchControl.xaml.cs* die folgende Direktive hinzu:

    ```csharp
    using System.Text;
    ```

4. Entfernen `button1_Click()` Sie die Methode.

     Fügen Sie in der **TestSearchControl-Klasse** den folgenden Code hinzu.

     Dieser Code fügt <xref:System.Windows.Controls.TextBox> eine öffentliche Eigenschaft mit dem Namen **SearchResultsTextBox** und eine öffentliche Zeichenfolgeneigenschaft mit dem Namen **SearchContent**hinzu. Im Konstruktor wird SearchResultsTextBox auf das Textfeld festgelegt, und SearchContent wird in einen Zeilenumlagesatz von Zeichenfolgen initialisiert. Der Inhalt des Textfelds wird auch in den Satz von Zeichenfolgen initialisiert.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.

6. Wählen Sie in **View** > der Menüleiste Andere**Windows-Testsuche****Other Windows** > anzeigen aus.

     Das Toolfenster wird angezeigt, aber das Suchsteuerelement wird noch nicht angezeigt.

## <a name="to-add-a-search-box-to-the-tool-window"></a>So fügen Sie dem Toolfenster ein Suchfeld hinzu

1. Fügen *TestSearch.cs* Sie in `TestSearch` der TestSearch.cs Datei der Klasse den folgenden Code hinzu. Der Code überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft, `true`sodass der Get-Accessor zurückgibt.

     Um die Suche zu aktivieren, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft überschreiben. Die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasse <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> implementiert und stellt eine Standardimplementierung bereit, die die Suche nicht aktiviert.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

3. Öffnen Sie in der experimentellen Instanz von Visual Studio **TestSearch**.

     Oben im Werkzeugfenster wird ein Suchsteuerelement mit einem **Suchwasserzeichen** und einem Lupensymbol angezeigt. Die Suche funktioniert jedoch noch nicht, da der Suchvorgang nicht implementiert wurde.

## <a name="to-add-the-search-implementation"></a>So fügen Sie die Suchimplementierung hinzu
 Wenn Sie die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>Suche auf einem aktivieren, wie im vorherigen Verfahren, erstellt das Toolfenster einen Suchhost. Dieser Host richtet Suchprozesse ein und verwaltet diese, die immer in einem Hintergrundthread auftreten. Da <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> die Klasse die Erstellung des Suchhosts und die Einrichtung der Suche verwaltet, müssen Sie nur eine Suchaufgabe erstellen und die Suchmethode bereitstellen. Der Suchvorgang findet in einem Hintergrundthread statt, und Aufrufe des Werkzeugfenstersteuerelements erfolgen im UI-Thread. Daher müssen Sie die [ThreadHelper.Invoke*-Methode](https://msdn.microsoft.com/data/ee197798(v=vs.85)) verwenden, um alle Aufrufe zu verwalten, die Sie im Umgang mit dem Steuerelement tätigen.

1. Fügen Sie in der `using` Datei *TestSearch.cs* die folgenden Direktiven hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Fügen `TestSearch` Sie in der Klasse den folgenden Code hinzu, der die folgenden Aktionen ausführt:

    - Überschreibt <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> die Methode zum Erstellen einer Suchaufgabe.

    - Überschreibt <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> die Methode zum Wiederherstellen des Status des Textfelds. Diese Methode wird aufgerufen, wenn ein Benutzer eine Suchaufgabe abbricht und wenn ein Benutzer Optionen oder Filter festlegt oder aufhebt. Beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> und werden im UI-Thread aufgerufen. Daher müssen Sie nicht über die [ThreadHelper.Invoke*-Methode](https://msdn.microsoft.com/data/ee197798(v=vs.85)) auf das Textfeld zugreifen.

    - Erstellt eine Klasse mit `TestSearchTask` dem Namen <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, die von erbt, die eine Standardimplementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>bereitstellt.

         In `TestSearchTask`legt der Konstruktor ein privates Feld fest, das auf das Werkzeugfenster verweist. Um die Suchmethode bereitzustellen, <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> überschreiben Sie die und-Methoden. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> Die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Methode ist, wo Sie den Suchprozess implementieren. Dieser Prozess umfasst das Ausführen der Suche, das Anzeigen der Suchergebnisse im Textfeld und das Aufrufen der Basisklassenimplementierung dieser Methode, um zu melden, dass die Suche abgeschlossen ist.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. Testen Sie die Suchimplementierung, indem Sie die folgenden Schritte ausführen:

    1. Erstellen Sie das Projekt neu, und starten Sie das Debuggen.

    2. Öffnen Sie in der experimentellen Instanz von Visual Studio das Toolfenster erneut, geben Sie Suchtext in das Suchfenster ein, und klicken Sie auf **ENTER**.

         Die richtigen Ergebnisse sollten angezeigt werden.

## <a name="to-customize-the-search-behavior"></a>So passen Sie das Suchverhalten an
 Durch Ändern der Sucheinstellungen können Sie eine Vielzahl von Änderungen daran vornehmen, wie das Suchsteuerelement angezeigt wird und wie die Suche ausgeführt wird. Sie können z. B. das Wasserzeichen (den Standardtext, der im Suchfeld angezeigt wird), die minimale und maximale Breite des Suchsteuerelements und die Anzeige einer Fortschrittsleiste ändern. Sie können auch den Punkt ändern, an dem Suchergebnisse angezeigt werden (bei Bedarf oder sofort) und ob eine Liste von Begriffen angezeigt werden soll, nach denen Sie kürzlich gesucht haben. Sie finden die vollständige Liste <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> der Einstellungen in der Klasse.

1. Fügen Sie der Klasse in `TestSearch` der Datei* TestSearch.cs* den folgenden Code hinzu. Dieser Code ermöglicht die sofortige Suche anstelle der Bedarfssuche (d. h., der Benutzer muss nicht auf **ENTER**klicken). Der Code überschreibt `ProvideSearchSettings` die `TestSearch` Methode in der Klasse, die zum Ändern der Standardeinstellungen erforderlich ist.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Testen Sie die neue Einstellung, indem Sie die Lösung neu erstellen und den Debugger neu starten.

     Suchergebnisse werden jedes Mal angezeigt, wenn Sie ein Zeichen in das Suchfeld eingeben.

3. Fügen `ProvideSearchSettings` Sie in der Methode die folgende Zeile hinzu, die die Anzeige eines Fortschrittsbalkens ermöglicht.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     Damit die Fortschrittsleiste angezeigt wird, muss der Fortschritt gemeldet werden. Um den Fortschritt zu melden, entkommentieren Sie den folgenden Code in der `OnStartSearch` Methode der `TestSearchTask` Klasse:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Um die Verarbeitung so zu verlangsamen, dass die Fortschrittsleiste sichtbar ist, entfällt die Kommentarzeile der folgenden Zeile in der `OnStartSearch` Methode der `TestSearchTask` Klasse:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Testen Sie die neuen Einstellungen, indem Sie die Lösung neu erstellen und mit dem Debuggen beginnen.

     Die Fortschrittsleiste wird jedes Mal, wenn Sie eine Suche durchführen, im Suchfenster (als blaue Zeile unter dem Suchtextfeld) angezeigt.

## <a name="to-enable-users-to-refine-their-searches"></a>So ermöglichen Sie Es Benutzern, ihre Suchvorgänge zu verfeinern
 Sie können Benutzern erlauben, ihre Suchvorgänge mithilfe von Optionen wie **Match Case** oder Match **Whole Word**zu verfeinern. Optionen können boolesch sein, die als Kontrollkästchen angezeigt werden, oder Befehle, die als Schaltflächen angezeigt werden. Für diese exemplarische Vorgehensweise erstellen Sie eine boolesche Option.

1. Fügen *TestSearch.cs* Sie in `TestSearch` der TestSearch.cs Datei der Klasse den folgenden Code hinzu. Der Code überschreibt die `SearchOptionsEnum` Methode, wodurch die Suchimplementierung erkennen kann, ob eine bestimmte Option aktiviert oder deaktiviert ist. Der Code `SearchOptionsEnum` in fügt eine Option <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> hinzu, um die Anfrage einem Enumerator zu entsprechen. Die Option zum Abgleichen von `MatchCaseOption` Gehäusen wird auch als Eigenschaft zur Verfügung gestellt.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. Entkommentieren `TestSearchTask` Sie in der Klasse `OnStartSearch` die folgende Zeile in der Methode:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Testen Sie die Option:

    1. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

    2. Wählen Sie im Werkzeugfenster den Pfeil Nach unten auf der rechten Seite des Textfelds aus.

         Das Kontrollkästchen **Match-Fall** wird angezeigt.

    3. Aktivieren Sie das Kontrollkästchen **Groß-/Kleinschreibung abgleichen,** und führen Sie dann einige Suchvorgänge durch.

## <a name="to-add-a-search-filter"></a>So fügen Sie einen Suchfilter hinzu
 Sie können Suchfilter hinzufügen, mit denen Benutzer den Satz von Suchzielen verfeinern können. Sie können z. B. Dateien im Datei-Explorer nach den Datumsangaben filtern, an denen sie zuletzt geändert wurden, und nach ihren Dateinamenerweiterungen. In dieser exemplarischen Vorgehensweise fügen Sie einen Filter nur für gerade Linien hinzu. Wenn der Benutzer diesen Filter auswählt, fügt der Suchhost die Zeichenfolgen hinzu, die Sie der Suchabfrage angeben. Sie können diese Zeichenfolgen dann innerhalb Der Suchmethode identifizieren und die Suchziele entsprechend filtern.

1. Fügen *TestSearch.cs* Sie in `TestSearch` der TestSearch.cs Datei der Klasse den folgenden Code hinzu. Der Code `SearchFiltersEnum` wird durch <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> Hinzufügen eines implementiert, das angibt, die Suchergebnisse so zu filtern, dass nur gerade Zeilen angezeigt werden.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Jetzt zeigt das Suchsteuerelement `Search even lines only`den Suchfilter an. Wenn der Benutzer den Filter `lines:"even"` auswählt, wird die Zeichenfolge im Suchfeld angezeigt. Andere Suchkriterien können gleichzeitig mit dem Filter angezeigt werden. Suchzeichenfolgen können vor dem Filter, nach dem Filter oder beidem angezeigt werden.

2. Fügen Sie in der *TestSearch.cs* Datei `TestSearchTask` die folgenden Methoden `TestSearch` zur Klasse hinzu, die sich in der Klasse befindet. Diese Methoden `OnStartSearch` unterstützen die Methode, die Sie im nächsten Schritt ändern.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Aktualisieren `TestSearchTask` Sie in `OnStartSearch` der Klasse die Methode mit dem folgenden Code. Durch diese Änderung wird der Code aktualisiert, um den Filter zu unterstützen.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. Testen Sie Ihren Code.

5. Erstellen Sie das Projekt, und starten Sie das Debugging. Öffnen Sie in der experimentellen Instanz von Visual Studio das Toolfenster, und wählen Sie dann den Pfeil nach unten im Suchsteuerelement aus.

     Das Kontrollkästchen **Groß-/Kleinschreibung anpassen** und nur den Filter **"Gerade Suchen"** werden angezeigt.

6. Wählen Sie den Filter aus.

     Das Suchfeld enthält **Zeilen:"even"**, und die folgenden Ergebnisse werden angezeigt:

     2 gut

     4 Gut

     6 Auf Wiedersehen

7. Löschen `lines:"even"` Sie aus dem Suchfeld, aktivieren Sie `g` das Kontrollkästchen **Groß-/Kleinschreibung abgleichen,** und geben Sie dann in das Suchfeld ein.

     Folgende Ergebnisse werden angezeigt:

     1 go

     2 gut

     5 Auf Wiedersehen

8. Wählen Sie das X auf der rechten Seite des Suchfeldes aus.

     Die Suche wird gelöscht, und der ursprüngliche Inhalt wird angezeigt. Das Kontrollkästchen **Groß-/Kleinschreibung abgleichen** ist jedoch weiterhin aktiviert.
