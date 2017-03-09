---
title: "Analysieren der CPU-Auslastung in Store-Apps | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
robots: noindex,nofollow
---
# Analysieren der CPU-Auslastung in Store-Apps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Gilt für Windows und Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Ein guter Anfangspunkt für das Untersuchen von Leistungsproblemen in Ihrer App ist die Erkenntnis, wie die App die CPU nutzt.  Das Tool **CPU\-Auslastung** im Visual Studio\-Leistungs\- und Diagnosehub zeigt Ihnen, wo die CPU Zeit aufwendet, um C\+\+\-, C\#\-\/VB\- und JavaScript\-Code auszuführen.  Für eine Fokussierung auf bestimmte Szenarien kann das CPU\-Auslastungstool mit dem Tool [XAML\-UI\-Reaktionsfähigkeit](../Topic/Analyze%20UI%20responsiveness%20in%20Store%20apps%20\(XAML\).md), dem Tool [Energieverbrauch](../profiling/analyze-energy-use-in-store-apps.md) oder beiden in einer einzigen Diagnosesitzung verwendet werden.  Das CPU\-Auslastungstool ersetzt das CPU\-Samplingtool in Visual Studio 2013.  
  
> [!NOTE]
>  Das Tool **CPU\-Auslastung** kann nicht mit Windows Phone Silverlight 8.1\-Apps verwendet werden.  
  
 In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie die CPU\-Auslastung für eine einfache App erfassen und analysieren.  
  
 Sie verwenden die Standardverfahren des [Leistungs\- und Diagnosehubs](../Topic/Run%20analysis%20tools%20from%20the%20Performance%20and%20Diagnostic%20page.md), um die Daten zu erfassen. Der Leistungs\- und Diagnosehub bietet jedoch noch zahlreiche weitere Optionen für das Ausführen und Verwalten Ihrer Diagnosesitzungen.  Sie können das CPU\-Auslastungstool beispielsweise für Windows Phone\- oder Windows Store\-Apps ausführen und die Diagnosesitzung auf dem Visual Studio\-Computer, einem Windows Phone\- oder Windows Store\-Gerät oder einem der Visual Studio\-Emulatoren oder \-Simulatoren ausführen.  
  
 Dann werfen Sie einen ausführlichen Blick in den CPU\-Auslastungsdiagnosebericht.  
  
## Inhalt  
 [Erstellen des CpuUseDemo-Projekts](#BKMK_Create_the_CpuUseDemo_project)  
  
 [Was ist CpuUseDemo?](#BKMK_What_is_CpuUseDemo_)  
  
 [Erfassen von CPU-Auslastungsdaten](#BKMK_Collect_CPU_usage_data)  
  
 [Analysieren des CPU-Auslastungsberichts](#BKMK_Analyze_the_CPU_Usage_report)  
  
 [Nächste Schritte](#BKMK_Next_steps)  
  
 [MainPage.xaml](#BKMK_MainPage_xaml)  
  
 [MainPage.xaml.cs](#BKMK_MainPage_xaml_cs)  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a> Erstellen des CpuUseDemo\-Projekts  
  
1.  Erstellen Sie ein neues Windows Store\-C\#\-App\-Projekt mit dem Namen **CpuUseDemo** über die Vorlage **BlankApp**.  
  
2.  Ersetzen Sie MainPage.xaml durch [den folgenden Code](#BKMK_MainPage_xaml).  
  
3.  Ersetzen Sie MainPage.xaml.cs durch [den folgenden Code](#BKMK_MainPage_xaml_cs).  
  
##  <a name="BKMK_What_is_CpuUseDemo_"></a> Was ist CpuUseDemo?  
 **CpuUseDemo** ist eine App, die erstellt wurde, um zu zeigen, wie Sie CPU\-Auslastungsdaten erfassen und analysieren.  Die Schaltflächen generieren eine Zahl, indem sie eine Methode aufrufen, die den maximalen Wert aus mehreren Aufrufen an eine Funktion auswählt.  Die aufgerufene Funktion erstellt eine sehr große Anzahl zufälliger Werte und gibt dann den letzten zurück.  Die Daten werden in einem Textfeld angezeigt.  Erstellen Sie die App, und probieren Sie es aus.  
  
 Die App ist nicht sehr spannend, und die Methoden von CpuUseDemo sind nicht besonders interessant, aber der Vorgang ist einfach genug, um Ihnen einige typische Fälle für die Datenanalyse der CPU\-Auslastung zu zeigen.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Erfassen von CPU\-Auslastungsdaten  
  
1.  Legen Sie das Bereitstellungsziel in Visual Studio auf **Simulator** und die Lösungskonfiguration auf **Retail** fest.  
  
    -   Wenn Sie die App im Simulator ausführen, können Sie einfach zwischen der App und der Visual Studio IDE wechseln.  
  
    -   Die Ausführung dieser App im **Release**\-Modus gibt Ihnen eine bessere Ansicht der tatsächlichen Leistung Ihrer App.  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Leistung und Diagnose** aus.  
  
3.  Wählen Sie im Leistungs\- und Diagnosehub **CPU\-Auslastung** und dann **Starten** aus.  
  
4.  Wenn die App gestartet wurde, wählen Sie **Maximale Anzahl abrufen** aus.  Warten Sie etwa eine Minute, nachdem die Ausgabe angezeigt wird, und wählen Sie dann **Maximale Anzahl asynchron abrufen** aus.  Wenn Sie zwischen dem Klicken auf die Schaltfläche warten, ist es einfacher, die Schaltflächenklickroutinen im Diagnosebericht zu isolieren.  
  
5.  Nachdem die zweite Ausgabezeile angezeigt wird, wählen Sie im Leistungs\- und Diagnosehub **Auflistung beenden** aus.  
  
 Das CPU\-Auslastungstool analysiert die Daten und zeigt den Bericht an.  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analysieren des CPU\-Auslastungsberichts  
 [Diagramm der CPU-Auslastungszeitachse](#BKMK_CPU_utilization_timeline_graph) **&#124;** [Auswählen von Zeitachsensegmenten zum Anzeigen von Details](#BKMK_Select_timeline_segments_to_view_details) **&#124;** [Die CPU-Auslastungsaufrufstruktur](#BKMK_The_CPU_Usage_call_tree) **&#124;** [Struktur der Aufrufstruktur](#BKMK_Call_tree_structure) **&#124;** [Externer Code](#BKMK_External_Code) **&#124;** [Spalten mit Aufrufstrukturdaten](#BKMK_Call_tree_data_columns) **&#124;** [Asynchrone Funktionen in der CPU-Auslastungsaufrufstruktur](#BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree)  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a> Diagramm der CPU\-Auslastungszeitachse  
 Im CPU\-Auslastungsdiagramm wird die CPU\-Aktivität der App als Prozentsatz der gesamten CPU\-Zeit von allen Prozessorkernen auf dem Gerät angezeigt.  Die Daten dieses Berichts wurden auf einem Computer mit zwei Kernen erfasst.  Die zwei großen Spitzen stellen die CPU\-Aktivität der zwei Schaltflächenklicks dar.  `GetMaxNumberButton_Click` wird synchron auf einem einzigen Kern ausgeführt, sodass es Sinn macht, dass die Diagrammhöhe der Methode nie über 50 % hinausgeht.  `GetMaxNumberAsycButton_Click` wird asynchron über beide Kerne ausgeführt, deshalb sieht es auch hier richtig aus, dass die Spitze näher an die Nutzung aller CPU\-Ressourcen auf beiden Kernen herankommt.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a> Auswählen von Zeitachsensegmenten zum Anzeigen von Details  
 Verwenden Sie die Auswahlleisten in der Zeitachse **Diagnosesitzung**, um sich auf die GetMaxNumberButton\_Click\-Daten zu konzentrieren:  
  
 In der Zeitachse **Diagnosesitzung** wird jetzt die Zeit angezeigt, die in dem ausgewählten Segment verbracht wurde \(etwas mehr als 2 Sekunden in diesem Bericht\). Außerdem wird die Aufrufstruktur nach den Methoden gefiltert, die in der Auswahl ausgeführt wurden.  
  
 Wählen Sie jetzt das Segment `GetMaxNumberAsyncButton_Click` aus.  
  
 Diese Methode wird rund eine Sekunde schneller abgeschlossen als `GetMaxNumberButton_Click`, aber die Bedeutung der Aufrufstruktureinträge ist weniger offensichtlich.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Die CPU\-Auslastungsaufrufstruktur  
 Um zu beginnen, die Aufrufstrukturinformationen zu verstehen, wählen Sie das Segment `GetMaxNumberButton_Click` erneut aus, und sehen Sie sich die Aufrufstrukturdetails an.  
  
####  <a name="BKMK_Call_tree_structure"></a> Struktur der Aufrufstruktur  
  
|||  
|-|-|  
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid\_1")|Der oberste Knoten in CPU\-Auslastungsaufrufstrukturen ist ein Pseudoknoten.|  
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid\_2")|Wenn die Option **Externen Code anzeigen** deaktiviert ist, ist in den meisten Apps der Knoten der zweiten Ebene ein **\[External Code\]**\-Knoten, der den System\- und Frameworkcode enthält, der die App startet und beendet, die Benutzeroberfläche zeichnet, die Threadplanung steuert und andere Dienste der unteren Ebene für die App bereitstellt.|  
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid\_3")|Die untergeordneten Elemente des Knotens der zweiten Ebene sind die Benutzercodemethoden und asynchronen Routinen, die vom System\- und Frameworkcode der zweiten Ebene aufgerufen oder erstellt werden.|  
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid\_4")|Untergeordnete Knoten einer Methode enthalten Daten nur für die Aufrufe der übergeordneten Methode.  Wenn **Externen Code anzeigen** deaktiviert ist, können App\-Methoden auch einen **\[External Code\]**\-Knoten enthalten.|  
  
####  <a name="BKMK_External_Code"></a> Externer Code  
 Externer Code umfasst Funktionen in System\- und Frameworkkomponenten, die von dem von Ihnen geschriebenen Code ausgeführt werden.  Externer Code beinhaltet Funktionen, die die App starten und beenden, die Benutzeroberfläche zeichnen, das Threading steuern und andere Dienste niedriger Ebene für die App bereitstellen.  In den meisten Fällen ist externer Code für Sie nicht interessant, deshalb erfasst die CPU\-Auslastungsaufrufstruktur die externen Funktionen einer Benutzermethode in einem **\[External Code\]**\-Knoten.  
  
 Wenn Sie die Aufrufpfade von externem Code anzeigen möchten, wählen Sie aus der Liste **Ansicht filtern** die Option **Externen Code anzeigen** und dann **Übernehmen** aus.  
  
 Achten Sie darauf, dass viele externe Codeaufrufketten tief verschachtelt sind, sodass die Breite der Spalte mit dem Funktionsnamen die Anzeigebreite aller außer sehr großer Computerbildschirme überschreiten kann.  In diesem Fall werden Funktionsnamen als **\[…\]** angezeigt:  
  
 Verwenden Sie das Suchfeld, um nach einem gewünschten Knoten zu suchen, und verwenden Sie dann die horizontale Bildlaufleiste, um die Daten sichtbar zu machen:  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Spalten mit Aufrufstrukturdaten  
  
|||  
|-|-|  
|**Gesamt\-CPU \(%\)**|Der Prozentsatz der CPU\-Aktivität der App im ausgewählten Zeitbereich, der von Aufrufen an die Funktion und den von der Funktion aufgerufenen Funktionen verwendet wurde.  Beachten Sie, dass sich dies vom Zeitachsendiagramm **CPU\-Auslastung** unterscheidet, in dem die Gesamtaktivität der App in einem Zeitraum mit der insgesamt verfügbaren CPU\-Kapazität verglichen wird.|  
|**Selbst\-CPU \(%\)**|Der Prozentsatz der CPU\-Aktivität der App im ausgewählten Zeitraum, der von den Aufrufen an die Funktion verwendet wurde, ausschließlich der Aktivität der von der Funktion aufgerufenen Funktionen.|  
|**Gesamt\-CPU \(ms\)**|Die Anzahl der Millisekunden, die im ausgewählten Zeitraum mit Aufrufen an die Funktion und die von der Funktion aufgerufenen Funktionen verbracht wurde.|  
|**Selbst\-CPU \(ms\)**|Die Anzahl der Millisekunden, die im ausgewählten Zeitraum mit Aufrufen an die Funktion und die von der Funktion aufgerufenen Funktionen verbracht wurde.|  
|**Modul**|Der Name des Moduls, das die Funktion enthält, oder die Anzahl von Modulen, die die Funktionen in einem \[External Code\]\-Knoten enthalten.|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Asynchrone Funktionen in der CPU\-Auslastungsaufrufstruktur  
 Wenn der Compiler auf eine asynchrone Methode trifft, erstellt er eine ausgeblendete Klasse, um die Ausführung der Methode zu steuern.  Begrifflich ist die Klasse ein Zustandsautomat mit einer Liste von vom Compiler generierten Funktionen, die Vorgänge der ursprünglichen Methode asynchron aufrufen, und den für sie erforderlichen korrekten Rückrufen, Planern und Iteratoren.  Wenn die ursprüngliche Methode von einer übergeordneten Methode aufgerufen wird, entfernt die Runtime die Methode aus dem Ausführungskontext der übergeordneten Methode und führt die Methode der ausgeblendeten Klasse im Kontext des System\- und Frameworkcodes durch, der die Ausführung der App steuert.  Die asynchronen Methoden werden oft, aber nicht immer, auf einem oder mehreren Threads ausgeführt.  Dieser Code wird in der CPU\-Auslastungsaufrufstruktur als untergeordnetes Element des **\[External Code\]**\-Knotens direkt unterhalb des oberen Knotens der Struktur angezeigt.  
  
 Um dies in unserem Beispiel zu sehen, wählen Sie erneut das Segment `GetMaxNumberAsyncButton_Click` in der Zeitachse aus.  
  
 Die ersten zwei Knoten unter **\[External Code\]** sind die vom Compiler generierten Methoden der Zustandsautomatklasse.  Der dritte ist der Aufruf an die ursprüngliche Methode.  Wenn Sie die generierte Methoden erweitern, sehen Sie, was passiert.  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` tut sehr wenig: Es verwaltet eine Liste der Aufgabenwerte, berechnet den maximalen Wert der Ergebnisse und zeigt die Ausgabe an.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zeigt Ihnen die Aktivität, die erforderlich ist, um die 48 Aufgaben auszuführen, die den Aufruf mit `GetNumberAsync` umschließen.  
  
-   `MainPage::<GetNumberAsync>b__b` zeigt die Aktivität der Aufgaben, die `GetNumber` aufrufen.  
  
##  <a name="BKMK_Next_steps"></a> Nächste Schritte  
 Die CpuUseDemo\-App ist kein Meisterwerk, aber Sie können die Nützlichkeit erweitern, indem Sie sie verwenden, um mit asynchronen Vorgängen und anderen Tools im Leistungs\- und Diagnosehub zu experimentieren.  
  
-   Beachten Sie, dass `MainPage::<GetNumberAsync>b__b` mehr Zeit in \[External Code\] als mit der Ausführung der GetNumber\-Methode verbringt.  Ein großer Teil dieser Zeit ist der Mehraufwand der asynchronen Vorgänge.  Versuchen Sie, die Anzahl der Aufgaben \(festgelegt in der `NUM_TASKS`\-Konstante von MainPage.xaml.cs\) zu erhöhen und die Anzahl der Iterationen in `GetNumber` zu verringern \(ändern Sie den Wert `MIN_ITERATIONS`\).  Führen Sie das Erfassungsszenario aus, und vergleichen Sie die CPU\-Aktivität von `MainPage::<GetNumberAsync>b__b` mit der in der ursprünglichen CPU\-Auslastungsdiagnosesitzung.  Versuchen Sie, die Aufgaben zu verringern und die Iterationen zu erhöhen.  
  
-   Benutzern ist die tatsächliche Leistung Ihrer App oft egal, ihnen ist die wahrgenommene Leistung und Reaktionsfähigkeit der App wichtig.  Mit dem Tool zur XAML\-UI\-Reaktionsfähigkeit können Sie die Details der Aktivität im UI\-Thread anzeigen, die sich auf die wahrgenommene Reaktionsfähigkeit auswirkt.  
  
     Erstellen Sie eine neue Sitzung im Leistungs\- und Diagnosehub, und fügen Sie die Tools XAML\-UI\-Reaktionsfähigkeit und CPU\-Auslastung hinzu.  Führen Sie das Erfassungsszenario aus.  Wenn Sie bis hierher gelesen haben, teilt der Bericht Ihnen wahrscheinlich nicht mehr mit, als Sie bereits wussten, aber die Unterschiede im Zeitachsendiagramm **UI\-Threadauslastung** für die zwei Methoden sind frappierend.  In komplexen realen Apps kann die Kombination der Tools sehr hilfreich sein.  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```c#  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```