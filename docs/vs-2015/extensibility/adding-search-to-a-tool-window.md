---
title: Hinzufügen von Suchfunktionen zu einem Toolfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d0f89d02d0fcccc66ddd1f66b411f6b3f542cff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939266"
---
# <a name="adding-search-to-a-tool-window"></a>Hinzufügen von Suchfunktionen zu einem Toolfenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Erstellen oder ein Toolfensters in Ihrer Erweiterung aktualisieren, können Sie die gleichen Suchfunktionen, die an anderer Stelle angezeigt wird, in Visual Studio hinzufügen. Diese Funktionalität umfasst die folgenden Funktionen:  
  
- Ein Suchfeld, die immer in einem benutzerdefinierten Bereich der Symbolleiste befindet.  
  
- Eine Statusanzeige, die in das Suchfeld selbst überlagert wird.  
  
- Die Möglichkeit, Ergebnisse angezeigt werden, sobald Sie jedes Zeichen (Sofortsuche) eingeben, oder nur nach der Auswahl der EINGABETASTE (Suchen Sie nach Bedarf).  
  
- Eine Liste, die Begriffe anzeigt, für die Sie zuletzt gesucht haben.  
  
- Die Fähigkeit zum Suchen nach bestimmten Feldern oder Aspekte der Ziele für die Suche zu filtern.  
  
  Anhand dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:  
  
1.  Erstellen Sie ein VSPackage-Projekt.  
  
2.  Erstellen Sie ein Toolfenster, die ein Steuerelement mit einem schreibgeschützten Textfeld enthält.  
  
3.  Hinzufügen eines Suchfelds zum Toolfenster an.  
  
4.  Fügen Sie die Search-Implementierung.  
  
5.  Aktivieren Sie die Sofortsuche und der Anzeige einer Statusanzeige dar.  
  
6.  Hinzufügen einer **Groß-/Kleinschreibung** Option.  
  
7.  Hinzufügen einer **suchen nur gerade Zeilen** Filter.  
  
## <a name="to-create-a-vsix-project"></a>So erstellen Sie ein VSIX-Projekt  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TestToolWindowSearch` mit einem Toolfenster mit dem Namen **TestSearch**. Wenn Sie hierzu Unterstützung benötigen, lesen Sie [Creating an Extension with a Tool Window](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Zum Erstellen eines Toolfensters  
  
1.  In der `TestToolWindowSearch` Projekt, öffnen Sie die Datei TestSearchControl.xaml.  
  
2.  Ersetzen Sie die vorhandene `<StackPanel>` Block mit den folgenden Block an, das ein schreibgeschütztes hinzufügt <xref:System.Windows.Controls.TextBox> auf die <xref:System.Windows.Controls.UserControl> im Toolfenster.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  Fügen Sie in der Datei TestSearchControl.xaml.cs die folgenden using-Anweisung:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Entfernen Sie die `button1_Click()` Methode.  
  
     In der **TestSearchControl** Klasse, fügen Sie den folgenden Code hinzu.  
  
     Dieser Code Fügt eine öffentliche <xref:System.Windows.Controls.TextBox> Eigenschaft mit dem Namen **SearchResultsTextBox** und eine öffentliche Zeichenfolgeneigenschaft mit dem Namen **SearchContent**. Klicken Sie im Konstruktor SearchResultsTextBox festgelegt ist, in das Textfeld, und SearchContent wird initialisiert, um eine neue Zeile getrennte Reihe von Zeichenfolgen. Der Inhalt des Textfelds wird auch auf den Satz von Zeichenfolgen initialisiert.  
  
    ```csharp  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-csharp[ToolWindowSearch#1](../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs#1)]
     [!code-vb[ToolWindowSearch#1](../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb#1)]  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
6.  Wählen Sie auf der Menüleiste **Ansicht**, **Other Windows**, **TestSearch**.  
  
     Das Toolfenster angezeigt wird, aber das Steuerelement für die Suche nicht noch angezeigt.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Das Fenster ein Suchfeld hinzu  
  
1.  Fügen Sie den folgenden Code hinzu, in der Datei TestSearch.cs der `TestSearch` Klasse. Der Code überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft so, dass der Get-Accessor gibt `true`.  
  
     Um die Suche zu aktivieren, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft. Die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> -Klasse implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> und stellt eine Standardimplementierung, die Suche nicht ermöglicht.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
3.  Öffnen Sie in der experimentellen Instanz von Visual Studio **TestSearch**.  
  
     Am oberen Rand des Toolfensters, ein Steuerelement für die Suche wird angezeigt, mit einem **Suche** Wasserzeichen und ein vergrößern Glass-Symbol. Suche funktioniert jedoch noch nicht, da der Suchprozess nicht implementiert wurde.  
  
## <a name="to-add-the-search-implementation"></a>Die suchimplementierung hinzufügen  
 Wenn Sie die Suche auf Aktivieren einer <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, wie im vorherigen Verfahren, das Fenster einen Search-Host erstellt. Dieser Host eingerichtet und verwaltet die Suche, die stets in einem Hintergrundthread auftreten. Da die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasse verwaltet die Erstellung von Search-Host und die Einstellung von der Suche, die Sie erstellen eine suchenaufgabe und geben Sie die Search-Methode. Die Suche erfolgt in einem Hintergrundthread und Aufrufe an das Tool Window-Steuerelement im UI-Thread auftreten. Aus diesem Grund müssen Sie verwenden die <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> Methode, um alle Aufrufe zu verwalten, die Sie im Zusammenhang mit dem Steuerelement vornehmen.  
  
1.  Fügen Sie die folgenden, in der Datei TestSearch.cs `using` Anweisungen:  
  
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
  
2.  In der `TestSearch` -Klasse verwenden, fügen Sie den folgenden Code, in der folgenden Aktionen ausgeführt:  
  
    -   Überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Methode zum Erstellen einer suchenaufgabe.  
  
    -   Überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Methode, um den Zustand des Textfelds wiederherzustellen. Diese Methode wird aufgerufen, wenn ein Benutzer abbricht, einer suchenaufgabe, und wenn ein Benutzer legt fest, oder hebt die Festlegung Optionen oder Filter. Beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> im UI-Thread aufgerufen werden. Aus diesem Grund müssen nicht im Textfeld von Zugriff auf die <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> Methode.  
  
    -   Erstellt eine Klasse mit dem Namen `TestSearchTask` von erbt <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, die bietet einer Standardimplementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         In `TestSearchTask`, der Konstruktor legt ein privates Feld, das im Toolfenster verweist. Um die Search-Methode bereitzustellen, die Sie überschreiben die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> und <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> Methoden. Die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Methode ist, in dem Sie den Suchvorgang implementieren. Dieser Prozess umfasst die Suche, Anzeige der Suchergebnisse in das Textfeld und das Aufrufen der basisklassenimplementierung dieser Methode zum melden, dass die Suche abgeschlossen ist.  
  
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
  
3.  Testen Sie Ihre suchimplementierung, indem Sie die folgenden Schritte ausführen:  
  
    1.  Das Projekt neu, und starten Sie das Debuggen.  
  
    2.  Öffnen Sie in der experimentellen Instanz von Visual Studio das Fenster erneut, geben Sie Suchtext Sie im Suchfenster und drücken Sie die EINGABETASTE.  
  
         Die richtigen Ergebnisse sollte angezeigt werden.  
  
## <a name="to-customize-the-search-behavior"></a>Das Suchverhalten anpassen  
 Ändern Sie die sucheinstellungen, können Sie eine Reihe von Änderungen vornehmen, wie das Nachschlagesteuerelement angezeigt wird und wie die Suche durchgeführt wird. Beispielsweise können Sie ändern das Wasserzeichen (der Standardtext, der in das Suchfeld angezeigt wird), die minimale und maximale Breite des Suchsteuerelements und angibt, ob eine Statusanzeige angezeigt. Sie können auch ändern, dass der Punkt, an die Suchergebnisse starten (bei Bedarf oder auf die Sofortsuche) angezeigt werden und angibt, ob eine Liste von Begriffen angezeigt, für die Sie zuletzt gesucht haben. Sie finden die vollständige Liste der Einstellungen in der <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> Klasse.  
  
1.  Fügen Sie den folgenden Code hinzu, in der Datei TestSearch.cs der `TestSearch` Klasse. Dieser Code ermöglicht die Sofortsuche anstelle der Suche bei Bedarf (d. h., die der Benutzer keine Eingabe). Der Code überschreibt die `ProvideSearchSettings` -Methode in der die `TestSearch` -Klasse, die zum Ändern der Standardeinstellungen erforderlich ist.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testen Sie die neue Einstellung durch Neuerstellen der Projektmappe, und starten Sie den Debugger erneut.  
  
     Suchergebnisse werden jedes Mal, dass Sie ein Zeichen in das Suchfeld eingeben.  
  
3.  In der `ProvideSearchSettings` -Methode, fügen die folgende Zeile, die die Anzeige einer Statusanzeige ermöglicht.  
  
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
  
     Für die Statusanzeige angezeigt werden muss der Status gemeldet werden. Um den Status zu melden, kommentieren Sie den folgenden Code in die `OnStartSearch` Methode der `TestSearchTask` Klasse:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Zu einer Verlangsamung Verarbeitungsstatus kompakt, dass die Befehlsleiste sichtbar ist, heben Sie die auskommentierung der folgenden Zeile in der `OnStartSearch` Methode der `TestSearchTask` Klasse:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Testen Sie die neuen Einstellungen durch Neuerstellen der Projektmappe und Debugb wird gestartet.  
  
     Die Statusanzeige wird im Suchfenster (als eine blaue Linie unterhalb des Suchfelds für Text) jedes Mal, dass Sie eine Suche durchführen.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>So aktivieren Sie Benutzern die Suche zu verfeinern.  
 Sie können Benutzern die Suche mithilfe von Optionen wie z. B. optimieren **Groß-/Kleinschreibung** oder **Nur ganzes Wort suchen**. Optionen können Boolesch, sein, die angezeigt werden, als Sie die Kontrollkästchen oder Befehle, die als Schaltflächen angezeigt werden. In dieser exemplarischen Vorgehensweise erstellen Sie eine boolesche Option.  
  
1.  Fügen Sie den folgenden Code hinzu, in der Datei TestSearch.cs der `TestSearch` Klasse. Der Code überschreibt die `SearchOptionsEnum` -Methode, die kann die suchimplementierung zu erkennen, ob eine gegebene Option aktiviert oder deaktiviert ist. Der Code in `SearchOptionsEnum` Fügt eine Option entsprechend der Fall, um eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> Enumerator. Die Möglichkeit, die Groß-und Kleinschreibung übereinstimmen, wird auch als zur Verfügung gestellt der `MatchCaseOption` Eigenschaft.  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
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
  
2.  In der `TestSearchTask` -Klasse, heben Sie die auskommentierung MatchCase Zeile in der `OnStartSearch` Methode:  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
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
  
3.  Testen Sie die Option:  
  
    1.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
    2.  Wählen Sie im Toolfenster den Pfeil nach unten auf der rechten Seite des Textfelds.  
  
         Die **Groß-/Kleinschreibung** Kontrollkästchen angezeigt wird.  
  
    3.  Wählen Sie die **Groß-/Kleinschreibung** Kontrollkästchen, und führen Sie einige suchen.  
  
## <a name="to-add-a-search-filter"></a>Um einen Suchfilter hinzufügen  
 Sie können die Suchfilter hinzufügen, mit die Benutzer zu die Suchziele filtern können. Beispielsweise können Sie Dateien im Datei-Explorer filtern, indem Sie die Datumsangaben, die auf denen die zuletzt geändert wurden und die Dateinamenerweiterungen. In dieser exemplarischen Vorgehensweise fügen Sie einen Filter für nur gerade Zeilen. Wenn der Benutzer, dass der Filter wählt, wird die Suchabfrage von Search-Host die Zeichenfolgen, die Sie angeben, hinzugefügt. Sie können diese Zeichenfolgen in eine Suchmethode identifizieren und entsprechend zu die Suchziele filtern.  
  
1.  Fügen Sie den folgenden Code hinzu, in der Datei TestSearch.cs der `TestSearch` Klasse. Der Code implementiert `SearchFiltersEnum` durch Hinzufügen einer <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> festlegt, dass die Suchergebnisse zu filtern, sodass nur gerade Zeilen angezeigt werden.  
  
    ```csharp  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Jetzt das Suchsteuerelement Suchfilter zeigt `Search even lines only`. Wenn der Benutzer wählt den Filter, die Zeichenfolge `lines:"even"` in das Suchfeld angezeigt wird. Andere Suchkriterien können zur gleichen Zeit wie die Filter angezeigt werden. Durchsuchen von Zeichenfolgen möglicherweise vor dem Filter, nach der Filter oder beides angezeigt werden.  
  
2.  Fügen Sie die folgenden Methoden hinzu, in der Datei TestSearch.cs der `TestSearchTask` -Klasse, die in der `TestSearch` Klasse. Diese Methoden unterstützen die `OnStartSearch` -Methode, die Sie im nächsten Schritt ändern werden.  
  
    ```csharp  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  In der `TestSearchTask` -Klasse, aktualisieren Sie die `OnStartSearch` Methode durch den folgenden Code. Diese Änderung wird den Code zur Unterstützung des Filters aktualisiert.  
  
    ```csharp  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
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
  
4.  Testen Sie Ihres Codes.  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Klicken Sie in der experimentellen Instanz von Visual Studio öffnen Sie das Toolfenster, und wählen Sie dann auf den Pfeil nach unten auf dem Suchsteuerelement.  
  
     Die **Groß-/Kleinschreibung** Kontrollkästchen und die **suchen nur gerade Zeilen** Filter angezeigt.  
  
6.  Wählen Sie den Filter ein.  
  
     Enthält das Suchfeld **Zeilen: "noch"**, und die folgenden Ergebnisse angezeigt werden:  
  
     gute 2  
  
     4 gute  
  
     6 goodbye  
  
7.  Löschen Sie `lines:"even"` wählen Sie im Suchfeld die **Groß-/Kleinschreibung** aus, und geben Sie dann `g` in das Suchfeld.  
  
     Die folgenden Ergebnisse angezeigt werden:  
  
     1 wechseln  
  
     gute 2  
  
     5 goodbye  
  
8.  Wählen Sie das X auf der Seite rechts neben dem Suchfeld ein.  
  
     Die Suche wird gelöscht, und die ursprünglichen Inhalte angezeigt werden. Allerdings die **Groß-/Kleinschreibung** das Kontrollkästchen aktiviert ist.

