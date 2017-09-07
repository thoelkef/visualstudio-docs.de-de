---
title: "Suchen Sie ein Toolfenster hinzufügen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: ecaa03757b5b40e92d343fa9328f9d3f9e584ba3
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="adding-search-to-a-tool-window"></a>Hinzufügen von Suche zu einem Toolfenster
Beim Erstellen oder aktualisieren ein Toolfenster in der Erweiterung können Sie die gleiche Suche-Funktionalität, die an anderer Stelle angezeigt wird, in Visual Studio hinzufügen. Diese Funktionalität umfasst die folgenden Funktionen:  
  
-   Ein Suchfeld, die immer in einem benutzerdefinierten Bereich der Symbolleiste befindet.  
  
-   Eine Statusanzeige, die auf das Suchfeld selbst überlagert.  
  
-   Die Möglichkeit, Ergebnisse anzeigen, sobald Sie jedes Zeichen (instant suchen) eingeben oder nur, nachdem Sie die EINGABETASTE (Suchen Sie nach Bedarf) auswählen.  
  
-   Eine Liste, die Begriffe zeigt für die Sie zuletzt gesucht haben.  
  
-   Die Fähigkeit zum Suchen nach bestimmten Feldern oder Aspekte der Suche Ziele zu filtern.  
  
 Anhand dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:  
  
1.  Erstellen Sie ein VSPackage-Projekt.  
  
2.  Erstellen Sie ein Toolfenster, die ein Benutzersteuerelement mit einem schreibgeschützten Textfeld enthält.  
  
3.  Fügen Sie ein Suchfeld zum Toolfenster.  
  
4.  Fügen Sie die Search-Implementierung.  
  
5.  Aktivieren Sie instant suchen und Anzeigen einer Statusanzeige an.  
  
6.  Hinzufügen einer **Groß-/Kleinschreibung beachten** Option.  
  
7.  Hinzufügen einer **suchen nur gerade Linien** Filter.  
  
## <a name="to-create-a-vsix-project"></a>So erstellen Sie ein VSIX-Projekt  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `TestToolWindowSearch` mit ein Toolfenster namens **TestSearch**. Wenn Sie hierzu Unterstützung benötigen, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Zum Erstellen eines Toolfensters  
  
1.  In der `TestToolWindowSearch` Projekt, öffnen Sie die Datei TestSearchControl.xaml.  
  
2.  Ersetzen Sie die vorhandene `<StackPanel>` Block mit den folgenden Block, das einen schreibgeschützten hinzufügt <xref:System.Windows.Controls.TextBox> auf die <xref:System.Windows.Controls.UserControl> im Toolfenster.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  Fügen Sie in der Datei TestSearchControl.xaml.cs die folgende Anweisung:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Entfernen Sie die `button1_Click()` Methode.  
  
     In der **TestSearchControl** Klasse, fügen Sie den folgenden Code hinzu.  
  
     Dieser Code Fügt einen öffentlichen <xref:System.Windows.Controls.TextBox> Eigenschaft mit dem Namen **SearchResultsTextBox** und eine öffentliche Eigenschaft mit dem Namen **SearchContent**. Im Konstruktor SearchResultsTextBox in das Textfeld festgelegt ist, und SearchContent wird initialisiert, um einen Zeilenumbruch getrennten Satz von Zeichenfolgen. Der Inhalt des Textfelds wird auch auf den Satz von Zeichenfolgen initialisiert.  
  
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
  
     [!code-csharp[ToolWindowSearch Nr. 1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)][!code-vb[ToolWindowSearch Nr. 1  ](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
6.  Wählen Sie in der Menüleiste **Ansicht**, **Weitere Fenster**, **TestSearch**.  
  
     Das Toolfenster angezeigt, aber das Steuerelement für die Suche wird nicht noch angezeigt.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>So fügen Sie ein Suchfeld zum Toolfenster hinzu  
  
1.  Fügen Sie in der Datei TestSearch.cs den folgenden Code, der `TestSearch` Klasse. Der Code überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft so, dass die "Get"-Zugriffsmethode zurückgegeben `true`.  
  
     Um die Suche zu aktivieren, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Eigenschaft. Die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> -Klasse implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> und stellt eine Standardimplementierung, die Suche zu aktivieren, ist nicht bereit.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
3.  Öffnen Sie in der experimentellen Instanz von Visual Studio **TestSearch**.  
  
     Am oberen Rand des Toolfensters, ein Steuerelement für die Suche wird angezeigt, mit einem **Suche** Wasserzeichen und ein Symbol "Vergrößern Glas". Suche funktioniert jedoch noch nicht, da die Search-Prozess nicht implementiert wurde.  
  
## <a name="to-add-the-search-implementation"></a>So fügen Sie die Implementierung für die Suche hinzu  
 Wenn Sie die Suche auf Aktivieren einer <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, wie im vorherigen Verfahren im Toolfenster einen Host für die Suche erstellt. Dieser Host eingerichtet und verwaltet Prozesse suchen, die stets in einem Hintergrundthread auftreten. Da die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Klasse verwaltet die Erstellung des Hosts suchen und die Einstellung von der Suche, Sie müssen nur Erstellen einer Aufgabe suchen, und geben Sie die Search-Methode. Die Suche erfolgt in einem Hintergrundthread, und Aufrufe an das Tool Window-Steuerelement für den UI-Thread ausgeführt. Deshalb müssen Sie verwenden die <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> Methode, um alle Aufrufe zu verwalten, die Sie beim Umgang mit dem Steuerelement vornehmen.  
  
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
  
    -   Überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Methode zum Erstellen einer Aufgabe suchen.  
  
    -   Überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Methode, um den Status des Textfelds wiederherzustellen. Diese Methode wird aufgerufen, wenn ein Benutzer abgebrochen wird, eine Aufgabe für die Suche und wenn ein Benutzer legt fest, oder hebt die Festlegung Optionen oder Filter. Beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> im UI-Thread aufgerufen werden. Daher keine müssen Sie das Textfeld anhand der Zugriff auf die <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> Methode.  
  
    -   Erstellt eine Klasse mit dem Namen `TestSearchTask` von erbt <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, stellt eine Standardimplementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         In `TestSearchTask`, des Konstruktors legt ein privates Feld, das das Toolfenster verweist. Um die Search-Methode bereitzustellen, überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> und <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> Methoden. Die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Methode ist, in dem Sie den Suchvorgang implementieren. Dieser Prozess umfasst die Suche und Anzeige der Suchergebnisse in das Textfeld Aufrufen die basisklassenimplementierung dieser Methode, um zu melden, dass die Suche abgeschlossen ist.  
  
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
  
3.  Testen Sie die Suche-Implementierung, indem Sie die folgenden Schritte ausführen:  
  
    1.  Das Projekt neu, und starten Sie das Debuggen.  
  
    2.  Öffnen Sie in der experimentellen Instanz von Visual Studio erneut das Toolfenster, geben Sie Suche Text in das Suchfenster und klicken Sie auf die EINGABETASTE.  
  
         Die richtigen Ergebnisse sollte angezeigt werden.  
  
## <a name="to-customize-the-search-behavior"></a>Zum Anpassen des Verhaltens für die Suche  
 Durch eine Änderung der sucheinstellungen, können Sie eine Reihe von Änderungen vornehmen, wie das Steuerelement für die Suche angezeigt wird und wie die Suche durchgeführt wird. Beispielsweise können Sie ändern das Wasserzeichen (der Standardtext, der in das Suchfeld angezeigt wird), die minimale und maximale Breite des suchen-Steuerelements und, ob eine Statusanzeige angezeigt. Sie können auch ändern, dass Punktes in die Suchergebnisse start (bei Bedarf oder auf schnelle Suche) angezeigt werden und ob zum Anzeigen einer Liste von Begriffen, für die Sie zuletzt gesucht. Sie finden die vollständige Liste der Einstellungen in der <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> Klasse.  
  
1.  Fügen Sie in der Datei TestSearch.cs den folgenden Code, der `TestSearch` Klasse. Dieser Code ermöglicht instant Suche anstelle einer bedarfsgesteuerten suchen (d. h., die der Benutzer besitzt, auf die EINGABETASTE). Der Code überschreibt die `ProvideSearchSettings` Methode in der `TestSearch` -Klasse, die die Standardeinstellungen geändert werden muss.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testen der neuen festlegen, indem Sie beim erneuten Erstellen der Projektmappe, und der Debugger neu gestartet.  
  
     Suchergebnisse werden jedes Mal, dass Sie ein Zeichen in das Suchfeld eingeben.  
  
3.  In der `ProvideSearchSettings` -Methode, fügen Sie die folgende Zeile, dadurch kann die Anzeige einer Statusanzeige.  
  
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
  
     Für die Statusanzeige angezeigt werden muss der Status gemeldet. Um den Fortschritt zu melden, kommentieren Sie den folgenden Code in die `OnStartSearch` Methode der `TestSearchTask` Klasse:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Kommentieren Sie verlangsamen Verarbeitungsstatus, dass die Leiste sichtbar ist, wird die folgende Zeile in der `OnStartSearch` Methode der `TestSearchTask` Klasse:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Beim erneuten Erstellen der Projektmappe und deren Debugb, um die neuen Einstellungen zu testen.  
  
     Die Statusanzeige wird angezeigt, in das Fenster "Suche" (als blaue Linie unterhalb des Textfelds Suche) jedes Mal, dass Sie eine Suche durchzuführen.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>So aktivieren Sie die Benutzer, um die Suche zu verfeinern.  
 Sie können Benutzern Benutzersuche mittels Optionen optimieren, wie z. B. **Groß-/Kleinschreibung beachten** oder **Nur ganzes Wort suchen**. Optionen können boolean sein, die angezeigt werden, als Kontrollkästchen oder Befehle, die als Schaltflächen angezeigt werden. In dieser exemplarischen Vorgehensweise erstellen Sie eine boolesche-Option.  
  
1.  Fügen Sie in der Datei TestSearch.cs den folgenden Code, der `TestSearch` Klasse. Der Code überschreibt die `SearchOptionsEnum` Methode, die ermöglicht die Suche Implementierung zu ermitteln, ob eine angegebene Option aktiviert oder deaktiviert ist. Der Code in `SearchOptionsEnum` Fügt eine Option aus, um die Groß-/Kleinschreibung zu übereinstimmen ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> Enumerator. Die Option aus, um die Groß-/Kleinschreibung übereinstimmen, wird auch als verfügbar gemacht die `MatchCaseOption` Eigenschaft.  
  
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
  
2.  In der `TestSearchTask` -Klasse, kommentieren Sie MatchCase Zeile in der `OnStartSearch` Methode:  
  
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
  
    2.  Wählen Sie im Toolfenster die nach-unten auf der rechten Seite des Textfelds aus.  
  
         Die **Groß-/Kleinschreibung beachten** Kontrollkästchen angezeigt wird.  
  
    3.  Wählen Sie die **Groß-/Kleinschreibung beachten** Kontrollkästchen, und klicken Sie dann einige Suchvorgänge ausführen.  
  
## <a name="to-add-a-search-filter"></a>Zum Hinzufügen eines Filters für die Suche  
 Sie können Suchfilter hinzufügen, mit die Benutzer den Satz der Ziele Suche optimieren können. Sie können z. B. Dateien im Datei-Explorer filtern, indem die Daten auf denen sie zuletzt geändert wurden und die Dateinamenerweiterungen. In dieser exemplarischen Vorgehensweise fügen Sie einen Filter für nur geraden Zeilen. Wenn der Benutzer diesen Filter auswählt, mit der Search-Host die Suchabfrage die Zeichenfolgen, die Sie angeben, hinzugefügt. Sie können diese Zeichenfolgen in Ihre Suchmethode identifizieren und die Suchziele entsprechend zu filtern.  
  
1.  Fügen Sie in der Datei TestSearch.cs den folgenden Code, der `TestSearch` Klasse. Der Code implementiert `SearchFiltersEnum` durch Hinzufügen einer <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> festlegt, dass die Suchergebnisse zu filtern, sodass nur gerade Linien angezeigt werden.  
  
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
  
     Jetzt das Steuerelement für die Suche Suchfilter zeigt `Search even lines only`. Wenn der Benutzer wählt den Filter, die Zeichenfolge `lines:"even"` in das Suchfeld angezeigt wird. Andere Suchkriterien können zur gleichen Zeit wie die Filter angezeigt werden. Suchzeichenfolgen möglicherweise vor dem Filter nach dem Filter oder beides angezeigt.  
  
2.  Fügen Sie in der Datei TestSearch.cs die folgenden Methoden auf die `TestSearchTask` Klasse, die in der `TestSearch` Klasse. Diese Methoden unterstützen die `OnStartSearch` -Methode, die Sie im nächsten Schritt ändern müssen.  
  
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
  
3.  In der `TestSearchTask` Klasse, aktualisieren Sie die `OnStartSearch` -Methode durch folgenden Code. Diese Änderung aktualisiert den Code, um den Filter zu unterstützen.  
  
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
  
4.  Testen Sie den Code ein.  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Öffnen Sie in der experimentellen Instanz von Visual Studio das Toolfenster, und wählen Sie dann auf den Pfeil nach unten auf das Steuerelement für die Suche.  
  
     Die **Groß-/Kleinschreibung beachten** Kontrollkästchen und **suchen nur gerade Linien** Filter angezeigt.  
  
6.  Wählen Sie den Filter aus.  
  
     Das Suchfeld enthält **Linien: "selbst"**, und die folgenden Ergebnisse angezeigt werden:  
  
     gute 2  
  
     4 funktionierende  
  
     6 goodbye  
  
7.  Löschen Sie `lines:"even"` wählen Sie in das Suchfeld der **Groß-/Kleinschreibung beachten** Kontrollkästchen und geben Sie dann `g` in das Suchfeld.  
  
     Die folgenden Ergebnisse angezeigt werden:  
  
     1 wechseln  
  
     gute 2  
  
     5 goodbye  
  
8.  Wählen Sie das "X" rechts neben dem Suchfeld aus.  
  
     Die Suche deaktiviert ist, und die ursprünglichen Inhalte angezeigt werden. Allerdings die **Groß-/Kleinschreibung beachten** Kontrollkästchen aktiviert ist.
