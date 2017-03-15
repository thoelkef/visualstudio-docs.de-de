---
title: "Hinzufügen der Suche auf ein Toolfenster | Microsoft-Dokumentation"
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
translationtype: Machine Translation
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>Hinzufügen von Suchfunktionen zu einem Toolfenster
Beim Erstellen oder aktualisieren ein Toolfenster in der Erweiterung können Sie die gleichen Suchfunktionalität, die an anderer Stelle angezeigt wird, in Visual Studio hinzufügen. Diese Funktionen umfassen die folgenden Funktionen:  
  
-   Ein Suchfeld, die immer in einem benutzerdefinierten Bereich der Symbolleiste befindet.  
  
-   Eine Statusanzeige, die auf das Suchfeld selbst überlagert.  
  
-   Die Möglichkeit, die Ergebnisse angezeigt, sobald Sie jedes Zeichen (Sofortsuche) eingeben, oder nur, nachdem Sie die EINGABETASTE (Suchen Sie nach Bedarf) auswählen.  
  
-   Eine Liste, die Begriffe anzeigt, für die Sie zuletzt gesucht haben.  
  
-   Die Fähigkeit zum Filtern der Suche auf bestimmte Felder oder Aspekte der Suchziele.  
  
 Anhand dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die folgenden Aufgaben ausführen:  
  
1.  Erstellen Sie ein VSPackage-Projekt.  
  
2.  Erstellen Sie ein Toolfenster, das ein Benutzersteuerelement mit einem schreibgeschützten Textfeld enthält.  
  
3.  Fügen Sie ein Suchfeld, um das Toolfenster.  
  
4.  Fügen Sie die Search-Implementierung.  
  
5.  Aktivieren Sie die Sofortsuche und Anzeigen einer Statusanzeige.  
  
6.  Hinzufügen einer **Groß-/Kleinschreibung** Option.  
  
7.  Hinzufügen einer **suchen nur gerade Linien** Filter.  
  
## <a name="to-create-a-vsix-project"></a>So erstellen Sie ein VSIX-Projekt  
  
1.  Erstellen Sie ein VSIX-Projekt namens `TestToolWindowSearch` mit einem Toolfenster mit der Bezeichnung **TestSearch**. Wenn Sie auf diese Weise Hilfe benötigen, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Erstellen Sie ein Toolfenster  
  
1.  In der `TestToolWindowSearch` Projekt, öffnen Sie die Datei TestSearchControl.xaml.  
  
2.  Ersetzen Sie die vorhandene `<StackPanel>` -Block mit den folgenden Block, eine schreibgeschützte Sicherheitsqualität <xref:System.Windows.Controls.TextBox>auf der <xref:System.Windows.Controls.UserControl>im Toolfenster.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  Fügen Sie in der Datei TestSearchControl.xaml.cs die folgende using-Anweisung:  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  Entfernen Sie die `button1_Click()` Methode.  
  
     In der **TestSearchControl** -Klasse verwenden, fügen Sie den folgenden Code.  
  
     Dieser Code Fügt eine öffentliche <xref:System.Windows.Controls.TextBox>Eigenschaft mit dem Namen **SearchResultsTextBox** und eine öffentliche Zeichenfolgeneigenschaft mit dem Namen **SearchContent**.</xref:System.Windows.Controls.TextBox> Im Konstruktor SearchResultsTextBox in das Textfeld festgelegt ist, und SearchContent wird initialisiert, um einen Zeilenumbruch getrennten Satz von Zeichenfolgen. Der Inhalt des Textfelds wird auch mit Zeichenfolgen initialisiert.  
  
    ```c#  
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
  
     [!code-cs[ToolWindowSearch&#1;](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch Nr.&1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz von Visual Studio wird angezeigt.  
  
6.  Wählen Sie auf der Menüleiste **Ansicht**, **Weitere Fenster**, **TestSearch**.  
  
     Das Toolfenster angezeigt, aber das Steuerelement für die Suche nicht noch angezeigt werden.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Das Toolfenster ein Suchfeld hinzu  
  
1.  Fügen Sie den folgenden Code in der Datei TestSearch.cs die `TestSearch` Klasse. Der Code überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>Eigenschaft so, dass der Get-Accessor gibt `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     Um die Suche zu aktivieren, müssen Sie überschreiben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>Eigenschaft.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>-Klasse implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>und bietet eine Standardimplementierung, die Suche aktivieren nicht.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
3.  Öffnen Sie in der experimentellen Instanz von Visual Studio **TestSearch**.  
  
     Im oberen Bereich des Toolfensters das Search-Steuerelement angezeigt wird, mit einem **Suche** Wasserzeichen und ein Symbol mit dem Vergrößern klicken. Suche funktioniert jedoch noch, da es sich bei der Suchvorgang nicht implementiert wurde.  
  
## <a name="to-add-the-search-implementation"></a>Der Search-Implementierung hinzufügen  
 Wenn Sie die Suche auf Aktivieren einer <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, wie im vorherigen Verfahren, das Toolfenster einen Search-Host erstellt.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Dieser Host eingerichtet und verwaltet Prozesse suchen, die stets in einem Hintergrundthread auftreten. Da die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>Klasse verwaltet die Erstellung von den Search-Host und die Einstellung von der Suche, Sie müssen nur Erstellen einer Aufgabe suchen und bieten die Suchmethode.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Die Suche erfolgt in einem Hintergrundthread, und Aufrufe des Steuerelements im Fenster auf den UI-Thread auftreten. Sie müssen daher verwenden die <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>Methode, um alle Aufrufe zu verwalten, die Sie im Umgang mit dem Steuerelement vornehmen.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  Fügen Sie in der Datei TestSearch.cs die folgenden `using` Anweisungen:  
  
    ```c#  
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
  
2.  In der `TestSearch` -Klasse verwenden, fügen Sie den folgenden Code, die folgenden Aktionen ausgeführt:  
  
    -   Überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>Methode zum Erstellen einer Aufgabe suchen.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   Überschreibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>Methode, um den Status des Textfeldes wiederherzustellen.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Diese Methode wird aufgerufen, wenn ein Benutzer abbricht, eine Aufgabe für die Suche und wenn ein Benutzer legt fest, oder hebt die Festlegung Optionen oder Filter. Beide <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>und <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>UI-Thread aufgerufen werden.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Daher müssen keine Zugriff auf das Textfeld mit der die <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>-Methode.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   Erstellt eine Klasse mit dem Namen `TestSearchTask` erbt, <xref:Microsoft.VisualStudio.Shell.VsSearchTask>stellt eine Standardimplementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> </xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         In `TestSearchTask`, der Konstruktor legt ein privates Feld, das im Toolfenster verweist. Um die Search-Methode bereitzustellen, überschreiben Sie die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>und <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>Methoden.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Die <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>Methode ist, in dem Sie den Suchvorgang implementieren.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Dieser Prozess umfasst die Suche, die Ergebnisse der Suche in das Textfeld anzeigen und Aufrufen der basisklassenimplementierung dieser Methode meldet, dass die Suche abgeschlossen ist.  
  
    ```c#  
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
  
3.  Testen Sie die suchimplementierung, indem Sie die folgenden Schritte ausführen:  
  
    1.  Das Projekt neu, und starten Sie das Debuggen.  
  
    2.  Öffnen Sie in der experimentellen Instanz von Visual Studio erneut das Toolfenster, geben Sie Suchtext Sie im Fenster Suche und drücken Sie die EINGABETASTE.  
  
         Das richtige Ergebnis sollte angezeigt werden.  
  
## <a name="to-customize-the-search-behavior"></a>Zum Anpassen des Verhaltens der Suche  
 Ändern Sie die Suchkriterien, können Sie eine Reihe von Änderungen vornehmen, wie das Steuerelement für die Suche angezeigt wird und wie die Suche durchgeführt wird. Beispielsweise können Sie ändern das Wasserzeichen (den Standardtext, der in das Suchfeld angezeigt wird), die minimale und maximale Breite des Steuerelements suchen und, ob eine Statusanzeige angezeigt. Sie können auch den Punkt, an welche Suchergebnisse starten (bei Bedarf oder Sofortsuche) angezeigt werden und ob zum Anzeigen einer Liste von Begriffen, für das Sie zuletzt gesucht, ändern. Sie finden eine vollständige Liste der Einstellungen in der <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>Klasse.</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>  
  
1.  Fügen Sie den folgenden Code in der Datei TestSearch.cs die `TestSearch` Klasse. Mit diesem Code kann die Sofortsuche statt Suche bei Bedarf (d. h., die der Benutzer keine Eingabe). Der Code überschreibt die `ProvideSearchSettings` -Methode in der `TestSearch` -Klasse, die die Standardeinstellungen geändert werden.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testen der neuen Einstellungen durch erneuten Erstellung der Projektmappe und der Debugger neu gestartet.  
  
     Suchergebnisse werden jedes Mal, dass Sie ein Zeichen in das Suchfeld eingeben.  
  
3.  In der `ProvideSearchSettings` -Methode, fügen Sie folgende Zeile, wodurch das Anzeigen einer Statusanzeige.  
  
    ```c#  
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
  
     Bei der Statusanzeige angezeigt werden muss der Status gemeldet werden. Um den Fortschritt zu melden, kommentieren Sie den folgenden Code in die `OnStartSearch` Methode der `TestSearchTask` Klasse:  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Verlangsamt Verarbeitungsstatus genug, damit die Statusleiste sichtbar ist, kommentieren Sie die folgende Zeile in der `OnStartSearch` Methode der `TestSearchTask` Klasse:  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Testen Sie die neuen Einstellungen, indem Sie beim erneuten Erstellen der Projektmappe und deren Debugb.  
  
     Die Statusanzeige wird im Fenster Suche (als eine blaue Linie unterhalb des Textfelds suchen) jedes Mal, dass Sie eine Suche durchführen.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Damit Benutzer ihre Suche können  
 Sie können Benutzer ihre mit Optionen wie z. B. Suche **Groß-/Kleinschreibung** oder **Nur ganzes Wort suchen**. Optionen können boolean sein, die angezeigt werden, als Kontrollkästchen oder Befehle, die als Schaltflächen angezeigt werden. In dieser exemplarischen Vorgehensweise erstellen Sie eine boolean-Option.  
  
1.  Fügen Sie den folgenden Code in der Datei TestSearch.cs die `TestSearch` Klasse. Der Code überschreibt die `SearchOptionsEnum` -Methode können die Search-Implementierung zu erkennen, ob eine angegebene Option aktiviert oder deaktiviert ist. Der Code in `SearchOptionsEnum` fügt die Möglichkeit, um die Groß-ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>Enumerator.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> Die Option Groß-als auch stehen die `MatchCaseOption` Eigenschaft.  
  
    ```c#  
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
  
2.  In der `TestSearchTask` -Klasse, kommentieren Sie MatchCase Zeile in die `OnStartSearch` Methode:  
  
    ```c#  
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
  
    2.  Wählen Sie im Toolfenster die nach-unten auf der rechten Seite des Textfelds.  
  
         Die **Groß-/Kleinschreibung** Kontrollkästchen angezeigt wird.  
  
    3.  Wählen Sie die **Groß-/Kleinschreibung** , und führen Sie dann einige suchen.  
  
## <a name="to-add-a-search-filter"></a>Hinzufügen eines Suchfilters  
 Sie können Filter hinzufügen, mit die Benutzer die Suchziele filtern können. Beispielsweise können Sie Dateien im Datei-Explorer filtern, die Datumsangaben, an denen sie zuletzt geändert wurden, und die Dateinamenerweiterungen. In dieser exemplarischen Vorgehensweise fügen Sie einen Filter für nur gerade Linien. Wenn der Benutzer diesen Filter, mit der Search-Host die Suchabfrage die Zeichenfolgen, die Sie angeben, hinzugefügt. Dann können Sie identifizieren diese Zeichenfolgen in der Search-Methode und die Suchziele entsprechend zu filtern.  
  
1.  Fügen Sie den folgenden Code in der Datei TestSearch.cs die `TestSearch` Klasse. Der Code implementiert `SearchFiltersEnum` durch Hinzufügen einer <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>festlegt, dass die Ergebnisse der Suche filtern, sodass nur gerade Linien angezeigt werden.</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
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
  
     Nachdem das Steuerelement für die Suche den Filter zeigt `Search even lines only`. Wenn der Benutzer wählt den Filter, die Zeichenfolge `lines:"even"` in das Suchfeld angezeigt wird. Andere Suchkriterien können zur gleichen Zeit wie die Filter angezeigt werden. Suchzeichenfolgen können vor dem Filter nach der Filter oder beides angezeigt werden.  
  
2.  Fügen Sie in der Datei TestSearch.cs die folgenden Methoden, die `TestSearchTask` -Klasse, die in der `TestSearch` Klasse. Diese Methoden unterstützen die `OnStartSearch` -Methode, die Sie im nächsten Schritt ändern können.  
  
    ```c#  
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
  
3.  In der `TestSearchTask` Klasse, aktualisieren Sie die `OnStartSearch` -Methode durch den folgenden Code. Diese Änderung wird der Code zur Unterstützung des Filters aktualisiert.  
  
    ```c#  
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
  
4.  Testen Sie den Code.  
  
5.  Erstellen Sie das Projekt, und starten Sie das Debugging. Öffnen Sie in der experimentellen Instanz von Visual Studio das Toolfenster, und wählen Sie dann auf den Pfeil nach unten auf das Steuerelement für die Suche.  
  
     Die **Groß-/Kleinschreibung** Kontrollkästchen und **suchen nur gerade Linien** Filter angezeigt.  
  
6.  Wählen Sie den Filter.  
  
     Das Suchfeld enthält **Zeilen: "selbst"**, die folgenden Ergebnisse angezeigt:  
  
     gute&2;  
  
     4 gute  
  
     6 goodbye  
  
7.  Löschen `lines:"even"` das Suchfeld ein, wählen Sie in der **Groß-/Kleinschreibung** das Kontrollkästchen, und geben Sie `g` in das Suchfeld.  
  
     Die folgenden Ergebnisse angezeigt werden:  
  
     1 wechseln  
  
     gute&2;  
  
     5 goodbye  
  
8.  Wählen Sie das X rechts neben dem Suchfeld.  
  
     Die Suche ist deaktiviert, und der ursprüngliche Inhalt wird angezeigt. Allerdings die **Groß-/Kleinschreibung** das Kontrollkästchen aktiviert ist.
