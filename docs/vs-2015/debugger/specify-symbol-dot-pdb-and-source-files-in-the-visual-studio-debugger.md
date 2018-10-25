---
title: Angeben von Symbol-(PDB-) und Quelldateien im Visual Studio-Debugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21cc710be92b00e8faba56582a733a6372f01130
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878751"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Angeben von Symbol(PDB)- und Quelldateien im Visual Studio Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Programmdatenbankdatei (PDB-Datei), auch als Symboldatei bezeichnet, ordnet die Bezeichner zu, die Sie in Quelldateien für Klassen, Methoden und anderen Code für Bezeichner erstellen, die in den kompilierten ausführbaren Dateien des Projekts verwendet werden. Die PDB-Datei ordnet die Anweisungen im Quellcode auch den Ausführungsanweisungen in den ausführbaren Dateien zu. Der Debugger nutzt diese Informationen, um zwei wichtige Informationen zu bestimmen: die Quelldatei und die Zeilennummer, die in der Visual Studio-IDE und im Speicherort der ausführbaren Datei angezeigt werden, an denen angehalten wird, wenn Sie einen Haltepunkt festgelegt haben. Eine Symboldatei enthält auch den ursprünglichen Speicherort der Quelldateien und optional den Speicherort eines Quellservers, von dem die Quelldateien abgerufen werden können.  
  
 Wenn Sie ein Projekt in der Visual Studio-IDE debuggen, kennt der Debugger den Standartspeicherort für die PDB-Dateien und die Quelldateien für den Code. Wenn Sie den Code außerhalb des Projektquellcodes, wie den Windows-Code oder den Code eines Drittanbieters für die Projektaufrufe, debuggen möchten, müssen Sie den Speicherort der PDB-Dateien (und optional die Quelldateien des externen Codes) angeben. Diese Dateien müssen exakt mit dem Build der ausführbaren Dateien übereinstimmen.  
  
 Wenn Sie vor Visual Studio 2012 verwalteten Code auf einem Remotegerät debuggt haben, mussten Sie die Symboldateien auf dem Remotecomputer ablegen. Dies ist nun nicht mehr der Fall. Alle Symboldateien müssen sich auf dem lokalen Computer oder an einem Speicherort befinden, der auf der Seite **Extras &gt; Optionen &gt; Debugging &gt; Symbole** .  
  
##  <a name="BKMK_Find_symbol___pdb__files"></a> Durchsucht, in denen der Debugger nach PDB-Dateien  
  
1.  Der Speicherort, der in der DLL-Datei oder der ausführbaren Datei angegeben ist.  
  
     (Wenn Sie eine DLL-Datei oder eine ausführbare Datei auf dem Computer erstellt haben, platziert der Linker standardmäßig den vollständigen Pfad und Dateinamen der zugehörigen PDB-Datei in die DLL-Datei oder ausführbare Datei. Der Debugger überprüft zuerst, ob die Symboldatei am Speicherort vorhanden ist, der in der DLL-Datei oder der ausführbaren Datei angegeben ist. Dies ist hilfreich, da Sie immer über Symbole für den Code verfügen, den Sie auf dem Computer kompiliert haben.)  
  
2.  PDB-Dateien, die im gleichen Ordner wie die DLL-Datei oder die ausführbare Datei vorhanden sein können.  
  
3.  Alle lokalen Symbolcache-Ordner.  
  
4.  Alle Netzwerk-, Internet- oder lokale Symbolserver und Speicherorte, die zum Beispiel auf dem Microsoft-Symbolserver angegeben sind (sofern aktiviert).  
  
###  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Warum müssen die Symboldateien genau mit den ausführbaren Dateien übereinstimmen?  
 Der Debugger lädt nur eine PDB-Datei für eine ausführbare Datei, die genau mit der PDB-Datei übereinstimmt, die zum Zeitpunkt der Erstellung der ausführbaren Datei ebenfalls erstellt wurde (das heißt, die PDB-Datei muss die originale PDB-Datei oder eine Kopie der originalen PDB-Datei sein). Da der Compiler neben seiner Hauptaufgabe der Erstellung des richtigen und effizienten Codes für Kompilierungsgeschwindigkeit optimiert wurde, kann das tatsächliche Layout einer ausführbaren Datei geändert werden, auch wenn sich der Code selbst nicht geändert hat. Weitere Informationen finden unter [Why does Visual Studio require debugger symbol files to *exactly* match the binary files that they were built with?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)(Warum benötigt Visual Studio Debuggersymboldateien um die binären Dateien, mit denen sie gebaut wurden, *exakt* anzupassen).  
  
###  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Angeben der symboldateispeicherorte und des Ladeverhaltens  
 Wenn Sie ein Projekt in der VS IDE debuggen, lädt der Debugger automatisch Symboldateien, die sich im Projektverzeichnis befinden. Sie können die alternativen Suchpfade und Symbolserver für Microsoft, Windows oder Komponenten von Drittanbietern in **Extras &gt; Optionen &gt; Debugging &gt; Symbole**angeben. Sie können ebenso bestimmte Module angeben, für die der Debugger automatisch Symbole laden soll. Sie können diese Einstellungen dann manuell ändern, während Sie aktiv debuggen.  
  
1. Öffnen Sie in Visual Studio die Seite **Extras &gt; Optionen &gt; Debugging &gt; Symbole** .  
  
    ![Tools &#45; Optionen &#45; Debuggen &#45; Seite "Symbole"](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")  
  
2. Wählen Sie den Ordner ![Tools&#47; Optionen&#47; Debuggen&#47;symbolordnersymbol](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") Symbol. Im Feld **Orte für Symboldateien (.pdb)** wird Text angezeigt, der bearbeitet werden kann.  
  
3. Geben Sie die URL oder den Verzeichnispfad des Symbolservers oder des Symbolspeicherorts ein. Durch Anweisungsvervollständigung wird Ihnen die Bestimmung des richtigen Formats erleichtert.  
  
4. Um die Ladeleistung von Symbolen zu verbessern, geben Sie im Feld **Symbole in diesem Verzeichnis zwischenspeichern** den Pfad eines lokalen Verzeichnisses ein, in das Symbole von Symbolservern kopiert werden können.  
  
   > [!NOTE]
   >  Platzieren Sie den Symbolcache nicht in einem geschützten Ordner (z. B. im C:\Windows-Ordner oder einem Unterordner). Verwenden Sie stattdessen einen Ordner mit Lese-/Schreibzugriff.  
  
   **Angeben des symbolladeverhaltens**  
  
   Sie können die Dateien angeben, die von den im Feld **Orte für Symboldateien (.pdb)** angegebenen Speicherorten automatisch geladen werden sollen, wenn Sie das Debugging starten. Symboldateien im Projektverzeichnis werden immer geladen.  
  
5. Wählen Sie **Alle nicht ausgeschlossenen Module** , um alle Symbole für alle Module zu laden, außer die Module, die Sie beim Auswählen des Links **Ausgeschlossene Module angeben** festlegen.  
  
6. Wählen Sie die Option **Nur angegebene Module** , und klicken Sie dann auf **Module angeben** , um die Module aufzulisten, die automatisch in die Symboldateien geladen werden sollen. Die Symboldateien für andere Module werden ignoriert.  
  
   **Geben zusätzlicher Symboloptionen an**  
  
   Sie können auch die folgenden Optionen auf der Seite **Extras &gt; Optionen &gt; Debugging &gt; Symbole** festlegen:  
  
   **Warnhinweis anzeigen Sie, wenn keine Symbole beim Starten (nur systemeigen)**  
  
   Wenn Sie diese Option wählen, wird eine Warnmeldung angezeigt, wenn Sie ein Programm debuggen, für das der Debugger keine Symbolinformationen hat.  
  
   **DLL‑Exporte laden**  
  
   Wenn Sie diese Option wählen, werden DLL‑Exporttabellen geladen. Symbolinformationen aus DLL-Exporttabellen sind hilfreich, wenn Sie mit Windows-Meldungen, Windows-Prozeduren (WindowProcs), COM-Objekten, Marshalling oder DLLs arbeiten, für die Sie keine Symbole haben. Durch das Lesen von DLL-Exportinformationen fällt etwas Verwaltungsaufwand an. Deshalb ist diese Funktion standardmäßig deaktiviert.  
  
   Verwenden Sie `dumpbin /exports`, um festzustellen, welche Symbole in der Exporttabelle einer DLL verfügbar sind. Symbole sind für alle 32-Bit-System-DLLs verfügbar. In der Ausgabe von `dumpbin /exports` wird der genaue Funktionsname angezeigt, einschließlich nicht alphanumerischer Zeichen. Dies erleichtert das Setzen eines Haltepunktes in einer Funktion. Funktionsnamen aus DLL-Exporttabellen können an anderen Stellen des Debuggers abgeschnitten angezeigt werden. Die Aufrufe werden in der Reihenfolge des Aufrufs angezeigt, wobei die aktuelle Funktion (die, die sich in der Schachtelungshierarchie auf der untersten Ebene befindet) ganz oben angezeigt wird. Weitere Informationen hierzu finden Sie unter [dumpbin /exports](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Verwenden Sie Symbolserver, um Symboldateien zu suchen, die sich nicht auf dem lokalen Computer befinden.  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kann Debugsymboldateien von Symbolservern herunterladen, die das symsrv-Protokoll implementieren. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) und [Debugtools für Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) sind zwei Tools, die Symbolserver implementieren können. Geben Sie die zu verwendenden Symbolserver im VS-Dialogfeld **Optionen** an.  
  
 Folgende Symbolserver können verwendet werden:  
  
 **Öffentliche Microsoft-Symbolserver**  
  
 Um einen Absturz zu debuggen, der beim Aufruf einer System-DLL oder der Bibliothek eines Drittanbieters auftritt, benötigen Sie oftmals PDB-Systemdateien, die Symbole für DLL-Dateien, EXE-Dateien und Gerätetreiber von Windows enthalten. Sie können diese Symbole von den öffentlichen Microsoft-Symbolservern abrufen. Die öffentlichen Microsoft-Symbolserver, die zusätzlich zu MDAC, IIS, ISA und [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Symbole für Windows-Betriebssysteme bereitstellen.  
  
 Um die Microsoft-Symbolserver zu verwenden, wählen Sie im Menü **Debuggen** das Menüelement **Optionen und Einstellungen** , und klicken Sie dann auf **Symbole**. Wählen Sie **Microsoft-Symbolserver**aus.  
  
 **Symbolserver auf einem internen Netzwerk oder auf dem lokalen Computer**  
  
 Ihr Team oder Ihr Unternehmen kann Symbolserver für eigene Produkte und als Cache für Symbole aus externen Quellen erstellen. Sie haben möglicherweise einen Symbolserver auf dem eigenen Computer. Sie können im VS-Dialogfeld **Optionen**/**Symbole** / **Symbole**(Warum benötigt Visual Studio Debuggersymboldateien um die binären Dateien, mit denen sie gebaut wurden, *exakt* anzupassen).  
  
 **Symbolserver von Drittanbietern**  
  
 Drittanbieter von Windows-Anwendungen und Bibliotheken können Zugriff auf Symbolserver im Internet gewähren. Sie können die URL dieser Symbolserver auch auf der Seite **Optionen**/**Symbole** eingeben.  
  
> [!NOTE]
>  Wenn Sie einen anderen Symbolserver als die öffentlichen Microsoft-Symbolserver verwenden, vergewissern Sie sich, dass der Symbolserver und der zugehörige Pfad vertrauenswürdig sind. Da Symboldateien beliebigen ausführbaren Code enthalten können, können Sie möglicherweise Sicherheitsbedrohungen ausgesetzt sein.  
  
###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Suchen und Laden von Symbolen beim Debuggen  
 Wenn sich der Debugger im Unterbrechungsmodus befindet, können Sie Symbole für ein Modul laden, das vorher durch Debuggeroptionen ausgeschlossen wurde oder das der Compiler nicht finden konnte. Sie können Symbole von den Kontextmenüs in den Fenstern "Aufrufliste", "Module", "Lokal" und "Auto" sowie in allen Überwachungsfenstern laden. Wenn der Debugger einen Code unterbricht, der keine verfügbaren Symbol- oder Quelldateien hat, wird ein Dokumentfenster geöffnet. Hier können Sie Informationen zu fehlenden Dateien suchen und Aktionen ausführen, um sie zu finden und zu laden.  
  
 **Suchen von Symbolen mit der Dokumentseite "Keine Symbole geladen"**  
  
 Es gibt mehrere Methoden, damit der Debugger im Code unterbrochen wird, der keine verfügbaren Symbole hat:  
  
1. Ausführen von Code in Einzelschritten  
  
2. Unterbrechen im Code von einem Haltepunkt oder einer Ausnahme  
  
3. Wechseln zu einem anderen Thread  
  
4. Ändern des Stapelrahmens durch Doppelklicken auf einen Rahmen im Aufruflistenfenster  
  
   Wenn eines dieser Ereignisse eintritt, wird im Debugger die Seite **Keine Symbole geladen** angezeigt, auf der Sie die erforderlichen Symbole suchen und laden können.  
  
   ![Keine Symbole geladen Seite](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")  
  
- Um die Suchpfade zu ändern, wählen Sie einen nicht markierten Pfad aus, oder wählen Sie **Neu** aus und geben einen neuen Pfad ein. Wählen Sie **Laden** , um die Pfade erneut zu suchen und die Symboldatei zu laden, sofern sie gefunden wurde.  
  
- Wählen Sie **Durchsuchen nach**_Name der ausführbaren Datei_**...** aus, um alle Symboloptionen zu überschreiben und die Suchpfade erneut zu versuchen. Die Symboldatei wird geladen, sofern sie gefunden wird, oder der Datei-Explorer wird geöffnet, in dem Sie die Symboldatei manuell auswählen können.  
  
- Wählen Sie **Symboleinstellungen ändern...** , um die Seite **Optionen** / **Symbole** im VS-Dialogfeld "Optionen" anzuzeigen.  
  
- Wählen Sie **Disassembly anzeigen** , um die Disassembly einmal in einem neuen Fenster anzuzeigen.  
  
- Um die Disassembly immer anzuzeigen, wenn die Quell- oder Symboldateien nicht gefunden werden, klicken Sie auf den Link **Optionsdialogfeld** , und wählen Sie die Optionen **Debugging auf Adressebene aktivieren** und **Disassembly anzeigen, wenn die Quelle nicht verfügbar ist**aus.  
  
   ![Optionen &#47; Debuggen &#47; allgemeine disassemblyoptionen](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")  
  
  **Ändern der Symboloptionen im Kontextmenü**  
  
  Wenn Sie sich im Unterbrechungsmodus befinden, können Sie Symbole für Elemente suchen und laden, die in den Fenstern "Aufrufliste", "Module", "Lokal" und "Auto" sowie in allen Überwachungsfenstern angezeigt werden. Wählen Sie ein Element im Fenster aus, öffnen Sie das Kontextmenü, und wählen Sie eine der folgenden Optionen:  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Symbole laden**|Lädt Symbole von den Speicherorten, die auf der Seite **Optionen** / **Symbole** des Dialogfelds **Optionen** an. Wenn die Symboldatei nicht gefunden werden kann, wird der Datei-Explorer gestartet, in dem Sie einen neuen zu suchenden Speicherort angeben können.|  
|**Symbolladeinformationen**|Bietet Informationen, die auf den Speicherort einer geladenen Symboldatei oder auf die Speicherorte hinweisen, die durchsucht wurden, wenn der Debugger die Datei nicht finden kann.|  
|**Symboleinstellungen...**|Öffnet die Seite **Optionen** / **Symbole** / **Optionen** an.|  
|**Immer automatisch laden**|Fügt die Symboldatei zur Liste der Dateien hinzu, die automatisch vom Debugger geladen werden.|  
  
###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Festlegen der Compileroptionen für Symboldateien  
 Wenn Sie das Projekt aus der VS IDE erstellen und die standardmäßige **Debug** -Buildkonfiguration verwenden, erstellen die Compiler für C++-Code und verwalteten Code die entsprechenden Symboldateien für den Code. Sie können Compileroptionen auch in der Befehlszeile festlegen, um Symboldateien zu erstellen.  
  
 **C++-Optionen**  
  
 Eine Programmdatenbankdatei (PDB-Datei) enthält Debug- und Projekstatusinformationen, die die inkrementelle Verknüpfung einer Debugkonfiguration des Programms ermöglichen. Eine PDB-Datei wird bei einem Build mit [/ZI oder /Zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (für C/C++) erstellt.  
  
 In [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]wird die vom Compiler erstellte PDB-Datei von der [/Fd](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) -Option benannt. Wenn Sie in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ein Projekt mithilfe von Assistenten erstellen, wird durch die **/Fd** -Option eine PDB-Datei mit dem Namen *project*.pdb erstellt.  
  
 Wird Sie die C/C++-Anwendung mithilfe einer Makefile erstellen und **/ZI** oder **/Zi** ohne **/Fd**angegeben, erhalten Sie zwei PDB-Dateien:  
  
- VC*x*.pdb, wobei *x* die Visual C++-Version darstellt, beispielsweise VC11.pdb. In dieser Datei werden alle Debuginformationen für die einzelnen OBJ-Dateien gespeichert; sie wird im selben Verzeichnis wie das Projektmakefile abgelegt.  
  
- project.pdb   In dieser Datei werden alle Debuginformationen für die EXE-Datei gespeichert. Bei C/C++ befindet sich die Datei im Unterverzeichnis \debug.  
  
  Wenn eine OBJ-Datei erstellt wird, führt der C/C++-Compiler Debuginformationen mit VC*x*.pdb zusammen. Die eingefügten Informationen umfassen zwar Typinformationen, jedoch keine Symbolinformationen, wie Funktionsdefinitionen. Selbst wenn jede Quelldatei allgemeine Headerdateien enthält, wie beispielsweise \<windows.h >, die Typdefinitionen aus diesen Headerdateien nur einmal anstatt in jeder OBJ-Datei gespeichert.  
  
  Der Linker erstellt die Datei "project.pdb", die Debuginformationen für die EXE-Datei des Projekts enthält. Die Datei "project.pdb" enthält nicht nur die in VC*x*.pdb gespeicherten Typinformationen, sondern alle Debuginformationen, einschließlich der Funktionsprototypen. Beide PDB-Dateien unterstützen inkrementelle Aktualisierungen. Der Linker bettet den Pfad zur PDB-Datei in die erstellte EXE- bzw. DLL-Datei ein.  
  
  Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Debugger verwendet den Pfad zur PDB-Datei in der EXE- bzw. DLL-Datei, um die Datei "project.pdb" zu finden. Wenn die PDB-Datei nicht vom Debugger am angegebenen Speicherort gefunden wird oder der Pfad ungültig ist (z. B. weil das Projekt auf einen anderen Computer verschoben wurde), durchsucht der Debugger den Pfad mit der EXE-Datei sowie die Symbolpfade, die im Dialogfeld **Optionen** (Ordner**Debugging** , Knoten **Symbole** ) angegeben sind. Der Debugger lädt keine PDB-Datei, die nicht mit der debuggten, ausführbaren Datei übereinstimmt. Wenn der Debugger keine PDB-Datei finden kann, wird das Dialogfeld **Symbole suchen** angezeigt, in dem Sie nach Symbolen suchen oder zusätzliche Speicherorte zum Suchpfad hinzufügen können.  
  
  **.NET Framework-Optionen**  
  
  Eine Programmdatenbankdatei (PDB-Datei) enthält Debug- und Projekstatusinformationen, die die inkrementelle Verknüpfung einer Debugkonfiguration des Programms ermöglichen. Eine PDB-Datei wird während des Buildvorgangs mit **/debug**erstellt. Sie können Anwendungsentwicklung mit **/debug:full** oder **/debug:pdbonly**erstellen. Beim Erstellen mit **/debug:full** wird debugfähiger Code generiert. Beim Erstellen mit **/debug:pdbonly** werden PDB-Dateien generiert, nicht jedoch das `DebuggableAttribute` -Attribut. Dieses Attribut zeigt dem JIT-Compiler sonst an, dass Debuginformationen verfügbar sind. Verwenden Sie **/debug:pdbonly** , wenn Sie PDB-Dateien für einen Releasebuild generieren möchten, der nicht debugfähig sein soll. Weitere Informationen finden Sie unter [/debug (C# Compiler Options)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) oder [/debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).  
  
  Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Debugger verwendet den Pfad zur PDB-Datei in der EXE- bzw. DLL-Datei, um die Datei "project.pdb" zu finden. Wenn die PDB-Datei vom Debugger nicht am angegebenen Speicherort gefunden wird oder der Pfad ungültig ist, durchsucht der Debugger den Pfad mit der EXE-Datei und anschließend die Symbolpfade, die im Dialogfeld **Optionen** angegeben sind. Dieser Pfad ist im Allgemeinen der Ordner **Debuggen** im Knoten **Symbole** . Der Debugger lädt keine PDB-Datei, die nicht mit der debuggten, ausführbaren Datei übereinstimmt. Wenn der Debugger keine PDB-Datei finden kann, wird das Dialogfeld **Symbole suchen** angezeigt, in dem Sie nach Symbolen suchen oder zusätzliche Speicherorte zum Suchpfad hinzufügen können.  
  
  **Webanwendungen**  
  
  In der Konfigurationsdatei der Anwendung (Web.config) muss der Debugmodus festgelegt sein. Der Debugmodus veranlasst ASP.NET zum Erstellen von Symbolen für dynamisch generierte Dateien und ermöglicht dem Debugger das Anfügen an die ASP.NET-Anwendung. VS legt dies beim Starten des Debugvorgangs automatisch fest, wenn Sie das Projekt anhand der Webprojekte-Vorlage erstellt haben.  
  
##  <a name="BKMK_Find_source_files"></a> Suchen der Quelldateien  
  
###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Speicherort, an dem der Debugger nach Quelldateien sucht  
 Der Debugger sucht an den folgenden Speicherorten nach Quelldateien:  
  
1.  Die in der Visual Studio-Instanz der IDE geöffneten Dateien, die der Debugger gestartet hat.  
  
2.  Dateien in der Projektmappe, die in der Visual Studio-Instanz geöffnet sind.  
  
3.  Verzeichnisse, die auf der Seite **Allgemeine Eigenschaften** / **Quelldateien debuggen** in den Eigenschaften der Projektmappe angegeben sind. (Wählen Sie im **Projektmappen-Explorer**den Projektmappenknoten aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Eigenschaften**aus. )  
  
4.  Die Quellinformationen der PDB-Datei des Moduls. Dies kann der Speicherort der Quelldatei sein, als das Modul erstellt wurde, oder es kann ein Befehl für einen Quellserver sein.  
  
###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Suchen und Laden von Quelldateien mit der Seite für "Keine Quelle geladen"/"Keine Symbole geladen"  
 Wenn der Debugger die Ausführung an einem Speicherort unterbricht, an dem die Quelldatei nicht verfügbar ist, wird die Seite für **Keine Quelle geladen** oder die Seite **Keine Symbole geladen** geöffnet, auf der Sie die Quelldatei suchen können. Die Seite **Keine Symbole geladen** wird angezeigt, wenn der Debugger eine Symboldatei (PDB-Datei) für die ausführbare Datei nicht finden kann, um die Suche abzuschließen. Die Seite "Keine Symbole geladen" enthält Optionen zur Suche nach der Datei. Wenn die PDB-Datei gefunden wird, nachdem Sie eine der Optionen ausgeführt haben und der Debugger die Quelldatei mithilfe der Informationen in der Symboldatei abrufen kann, wird die Quelldatei angezeigt. Andernfalls wird die Seite für **Keine Quelle geladen** angezeigt, auf der das Problem beschrieben wird. Die Seite enthält Optionslinks zum Ausführen von Aktionen, mit denen das Problem möglicherweise behoben wird.  
  
###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Hinzufügen von Quelldateisuchpfaden zu einer Projektmappe  
 Sie können ein Netzwerk oder lokale Verzeichnisse angeben, in denen nach Quelldateien gesucht werden soll.  
  
1. Wählen Sie die Projektmappe im Projektmappen-Explorer aus, und klicken Sie dann im Kontextmenü auf **Eigenschaften** .  
  
2. Wählen Sie unter dem Knoten **Allgemeine Eigenschaften** die Option **Quelldateien debuggen**aus.  
  
3. Klicken Sie auf den Ordner ![Tools&#47; Optionen&#47; Debuggen&#47;symbolordnersymbol](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") Symbol. Bearbeitbarer Text wird in der Liste **Verzeichnisse mit Quellcode** angezeigt.  
  
4. Fügen Sie den Pfad ein, den Sie durchsuchen möchten.  
  
   Beachten Sie, dass nur das angegebene Verzeichnis durchsucht wird. Sie müssen Einträge für alle Unterverzeichnisse hinzufügen, die durchsucht werden sollen.  
  
###  <a name="BKMK_Use_source_servers"></a> Verwenden von Quellservern  
 Wenn es auf dem lokalen Computer keinen Quellcode gibt oder die PDB-Datei nicht mit dem Quellcode übereinstimmt, können Sie eine Anwendung mithilfe des Quellservers debuggen. Der Quellserver nimmt Dateianforderungen entgegen und gibt die entsprechenden Dateien zurück. Quellserver wird mittels einer DLL-Datei mit der Bezeichnung srcsrv.dll ausgeführt. Der Quellserver liest die PDB-Datei der Anwendung. Diese Datei enthält Verweise auf das Quellcoderepository sowie Befehle zum Abrufen von Quellcode aus dem Repository. Sie können einschränken, welche Befehle aus der PDB-Datei der Anwendung ausgeführt werden dürfen, indem Sie die zulässigen Befehle in der Datei "srcsrv.ini" auflisten. Diese Datei muss sich im selben Verzeichnis befinden wie die Dateien "srcsrv.dll" und "devenv.exe".  
  
> [!IMPORTANT]
>  In der PDB-Datei der Anwendung können beliebige Befehle eingebettet sein. Deshalb sollten Sie sicherstellen, dass Sie der Datei "srcsrv.ini" nur die Befehle hinzufügen, die ausführt werden dürfen. Beim Versuch, einen nicht in der Datei srcsvr.ini enthaltenen Befehl auszuführen, wird ein Bestätigungsdialogfeld geöffnet. Weitere Informationen finden Sie unter [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Es wird keine Validierung für Befehlsparameter durchgeführt, seien Sie deshalb bei vertrauenswürdigen Befehlen vorsichtig. Beispielsweise kann bei Vertrauenswürdigkeit für den Befehl cmd.exe ein böswilliger Benutzer Parameter angeben, die den Befehl gefährlich machen.  
  
 **So aktivieren Sie die Verwendung eines Quellservers**  
  
1.  Stellen Sie sicher, dass Sie die im vorherigen Abschnitt beschriebenen Sicherheitsmaßnahmen ergriffen haben.  
  
2.  Wählen Sie im Menü **Extras** den Befehl **Optionen**.  
  
     Das Dialogfeld **Optionen** wird angezeigt.  
  
3.  Wählen Sie im Knoten **Debugging** die Option **Allgemein**aus.  
  
4.  Aktivieren Sie das Kontrollkästchen **Quellserverunterstützung aktivieren** .  
  
     ![Quellserveroptionen aktivieren](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")  
  
5.  (Optional) Wählen Sie die gewünschten untergeordneten Optionen aus.  
  
     Beachten Sie, dass die Option **Quellserver für teilweise vertrauenswürdige Assemblys (nur verwaltet) zulassen** und die Option **Alle nicht vertrauenswürdigen Quellserverbefehle ohne Aufforderung ausführen** die oben erläuterten Sicherheitsrisiken erhöhen können.  
  
## <a name="see-also"></a>Siehe auch  
 [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)





