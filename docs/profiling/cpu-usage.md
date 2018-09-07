---
title: Analysieren der CPU-Auslastung in Visual Studio | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1409431b0cdaec775ecd420fb9b6ea1ded0868de
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "42627152"
---
# <a name="analyze-cpu-usage"></a>Analysieren der CPU-Auslastung
Wenn Sie Leistungsprobleme in Ihrer App untersuchen müssen, ist ein guter Ausgangspunkt die Untersuchung der CPU-Nutzung. Das Tool **CPU-Auslastung** zeigt Ihnen, wo die CPU Zeit für die Ausführung von Visual C++-, Visual C#/Visual Basic und JavaScript-Code verbringt. Ab Visual Studio 2015 Update 1 können Sie eine Aufteilung nach Funktion der CPU-Auslastung anzeigen, ohne den Debugger zu verlassen. Sie können die CPU-Profilerstellung während des Debuggens ein- und ausschalten und die Ergebnisse anzeigen, wenn die Ausführung angehalten wird, z. B. an einem Haltepunkt.  
  
Zum Ausführen und Verwalten Ihrer Diagnosesitzung stehen Ihnen mehrere Optionen zur Verfügung. Sie können z. B. das Tool **CPU-Auslastung** auf lokalen oder Remotecomputern oder in einem Simulator oder Emulator ausführen. Sie können die Leistung eines geöffneten Projekts in Visual Studio analysieren, eine Verbindung mit einer ausgeführten App herstellen oder eine App starten, die aus dem Microsoft Store installiert wurde. Weitere Informationen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Hier erfahren Sie, wie Sie die CPU-Auslastung mithilfe von Releasebuilds erfassen und analysieren. Informationen zur Analyse der CPU-Auslastung während des Debuggens finden Sie unter [Einführung in die Leistungsprofilerstellung](../profiling/beginners-guide-to-performance-profiling.md).

Für die Verwendung des in diesem Artikel veranschaulichten Profilerstellungstools, [Leistungsprofiler](../profiling/profiling-feature-tour.md), ist Windows 7 oder höher erforderlich.
  
##  <a name="collect-cpu-usage-data"></a>Erfassen von CPU-Auslastungsdaten  
  
1.  Legen Sie in Visual Studio die Konfiguration der Projektmappe auf **Release** fest, und wählen Sie das Bereitstellungsziel.  
  
     ![Version und lokalen Computer auswählen](../profiling/media/cpuuse_selectreleaselocalmachine.png "CPUUSE_SelectReleaseLocalMachine")  
  
    -   Durch das Ausführen der App im **Release** -Modus erhalten Sie eine bessere Übersicht über die tatsächliche Leistung Ihrer App.  
  
    -   Durch Ausführen der App auf dem lokalen Computer wird die Ausführung der installierten App am besten repliziert.  
  
    -   Wenn Sie Daten von einem Remotegerät sammeln, führen Sie die App direkt auf dem Gerät und nicht über eine Remotedesktopverbindung aus.  
  
    -   Bei Windows Phone-Apps bietet das Sammeln von Daten direkt auf dem **Gerät** die genauesten Daten.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Leistungsprofiler**.  
  
3.  Wählen Sie **CPU-Auslastung** , und klicken Sie dann auf **Starten**.  
  
     ![CPU-Auslastung auswählen](../profiling/media/cpuuse_lib_choosecpuusage.png "CPUUSE_LIB_ChooseCpuUsage")  
  
4.  Klicken Sie nach dem Start der App auf **Maximale Anzahl abrufen**. Warten Sie nach Anzeige der Ausgabe etwa eine Minute, und klicken Sie dann auf **Maximale Anzahl asynchron abrufen**. Das Warten zwischen Schaltflächenklicks vereinfacht das Isolieren der Schaltflächenklickroutinen im Diagnosebericht.  
  
5.  Nachdem die zweite Ausgabezeile angezeigt wird, wählen Sie im Leistungs- und Diagnosehub **Auflistung beenden** aus.  
  
 ![Datenerfassung der CPU-Auslastung beenden](../profiling/media/cpu_use_wt_stopcollection.png "CPU_USE_WT_StopCollection")  
  
 Das CPU-Auslastungstool analysiert die Daten und zeigt den Bericht an.  
  
 ![CPU-Auslastungsbericht](../profiling/media/cpu_use_wt_report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a>Analysieren des CPU-Auslastungsberichts  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Die Aufrufstruktur der CPU-Auslastung  
 Um sich mit den Informationen in der Aufrufstruktur vertraut zu machen, wählen Sie zunächst `GetMaxNumberButton_Click` erneut aus, und sehen Sie sich dann die Aufrufstrukturdetails an.  
  
####  <a name="BKMK_Call_tree_structure"></a> Struktur der Aufrufstruktur  
 ![GetMaxNumberButton&#95;Click call tree](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid_1")|Der oberste Knoten in CPU-Auslastungsaufrufstrukturen ist ein Pseudoknoten.|  
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid_2")|Wenn die Option **Externen Code anzeigen** deaktiviert ist, ist in den meisten Apps der Knoten der zweiten Ebene ein **[External Code]** -Knoten, der den System- und Frameworkcode enthält, der die App startet und beendet, die Benutzeroberfläche zeichnet, die Threadplanung steuert und andere Dienste der unteren Ebene für die App bereitstellt.|  
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid_3")|Die untergeordneten Elemente des Knotens der zweiten Ebene sind die Benutzercodemethoden und asynchronen Routinen, die vom System- und Frameworkcode der zweiten Ebene aufgerufen oder erstellt werden.|  
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid_4")|Untergeordnete Knoten einer Methode enthalten Daten nur für die Aufrufe der übergeordneten Methode. Wenn **Externen Code anzeigen** deaktiviert ist, können App-Methoden auch den Knoten **[Externer Code]** enthalten.|  
  
####  <a name="BKMK_External_Code"></a> Externer Code  
 Externer Code umfasst Funktionen in System- und Frameworkkomponenten, die vom Code ausgeführt werden, den Sie schreiben. Externer Code umfasst Funktionen, die die App starten und beenden, die Benutzeroberfläche zeichnen, das Threading steuern und der App andere hardwarenahe Dienste bereitstellen. In den meisten Fällen sind Sie nicht an externem Code interessiert, weshalb die Aufrufstruktur „CPU-Auslastung“ die externen Funktionen einer Benutzermethode im Knoten **[Externer Code]** sammelt.  
  
 Wenn Sie die Aufrufpfade von externem Code anzeigen möchten, wählen Sie aus der Liste **Ansicht filtern** die Option **Externen Code anzeigen** und dann **Übernehmen**aus.  
  
 ![Filteransicht auswählen, dann „Externen Code anzeigen“](../profiling/media/cpu_use_wt_filterview.png "CPU_USE_WT_FilterView")  
  
 Achten Sie darauf, dass viele externe Codeaufrufketten tief verschachtelt sind, sodass die Breite der Spalte mit dem Funktionsnamen die Anzeigebreite aller außer sehr großer Computerbildschirme überschreiten kann. In diesem Fall werden Funktionsnamen als **[…]** angezeigt:  
  
 ![Geschachtelter externer Code in der Aufrufstruktur](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Verwenden Sie das Suchfeld, um nach einem gewünschten Knoten zu suchen, und verwenden Sie dann die horizontale Bildlaufleiste, um die Daten sichtbar zu machen:  
  
 ![Suche nach geschachteltem externen Code](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Spalten mit Aufrufstrukturdaten  
  
|||  
|-|-|  
|**Gesamt-CPU (%)**|![Gesamt % Datengleichung](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Der Prozentsatz der CPU-Aktivität der App im ausgewählten Zeitraum durch Aufrufe der Funktion und die von der Funktion aufgerufenen Funktionen. Beachten Sie, dass sich dieser Wert vom Zeitachsendiagramm **CPU-Auslastung** unterscheidet, das die Gesamtaktivität der App in einem Zeitraum mit der insgesamt verfügbaren CPU-Kapazität vergleicht.|  
|**Eigen-CPU (%)**|![Eigen % Gleichung](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Der Prozentsatz der CPU-Aktivität der App im ausgewählten Zeitraum durch Aufrufe der Funktion ohne die Aktivität der von der Funktion aufgerufenen Funktionen.|  
|**Gesamt-CPU (ms)**|Die Anzahl der Millisekunden für Aufrufe an die Funktion im ausgewählten Zeitraum und die von der Funktion aufgerufenen Funktionen.|  
|**Eigen-CPU (ms)**|Die Anzahl der Millisekunden für Aufrufe an die Funktion im ausgewählten Zeitraum und die von der Funktion aufgerufenen Funktionen, mit Ausnahme der Aktivität von Funktionen, die von der Funktion aufgerufen wurden.|  
|**Modul**|Der Name des Moduls mit der Funktion oder die Anzahl der Module, die die Funktionen in einem Knoten vom Typ [Externer Code] enthalten.|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Asynchrone Funktionen in der Aufrufstruktur der CPU-Auslastung  
 Wenn der Compiler auf eine asynchrone Methode trifft, erstellt er eine versteckte Klasse zum Steuern der Ausführung der Methode. Grundsätzlich ist die Klasse ein Zustandsautomat mit einer Liste vom Compiler generierter Funktionen, die Vorgänge der ursprünglichen Methode asynchron aufrufen, und den Rückrufen, dem Scheduler und den Iteratoren, die für deren ordnungsgemäße Ausführung erforderlich sind. Wenn die ursprüngliche Methode von einer übergeordneten Methode aufgerufen wird, entfernt die Runtime die Methode aus dem Ausführungskontext der übergeordneten Methode und führt die Methode der ausgeblendeten Klasse im Kontext des System- und Frameworkcodes durch, der die Ausführung der App steuert. Die asynchronen Methoden werden oft, jedoch nicht immer, in einem oder mehreren verschiedenen Threads ausgeführt. Dieser Code wird in der Aufrufstruktur der CPU-Auslastung als untergeordnete Elemente des Knotens **[Externer Code]** direkt unter dem obersten Knoten der Struktur gezeigt.  
  
 Um dies in unserem Beispiel zu sehen, wählen Sie erneut das Segment `GetMaxNumberAsyncButton_Click` in der Zeitachse aus.  
  
 ![GetMaxNumberAsyncButton&#95;Click Auswahl Bericht](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Die ersten zwei Knoten unter **[External Code]** sind die vom Compiler generierten Methoden der Zustandsautomatklasse. Der dritte ist der Aufruf der ursprünglichen Methode. Wenn Sie die generierte Methoden erweitern, sehen Sie, was passiert.  
  
 ![Erweitert GetMaxNumberAsyncButton&#95;Aufrufstruktur anklicken](../profiling/media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` macht sehr wenig, nämlich Verwalten einer Liste von Aufgabenwerten, Berechnen des Maximums der Ergebnisse und Anzeigen der Ausgabe.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zeigt die erforderliche Aktivität zum Planen und Starten der 48 Aufgaben, die den Aufruf von `GetNumberAsync`umschließen.  
  
-   `MainPage::<GetNumberAsync>b__b` zeigt die Aktivität der Aufgaben, die `GetNumber`aufrufen.
