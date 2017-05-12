---
title: "Debuggen von Office-Projekten"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Excel-Projekte [Office-Entwicklung in Visual Studio], Debuggen"
  - "Word-Projekte [Office-Entwicklung in Visual Studio], Debuggen"
  - "Outlook [Office-Entwicklung in Visual Studio], Debuggen"
  - "Debuggen [Office-Entwicklung in Visual Studio], Outlook-Projekte"
  - "Office-Projekte [Office-Entwicklung in Visual Studio], Debuggen"
  - "Outlook [Office-Entwicklung in Visual Studio], Projekte"
ms.assetid: e360b9e9-9f36-48f0-a0c5-a6980fb47a87
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Debuggen von Office-Projekten
  Sie können Office\-Projekte mit den gleichen Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Tools debuggen, die Sie auch für andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projekte verwenden.[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debuggerfunktionen, beispielsweise die Fähigkeit, Haltepunkte einzufügen und Variablen im Fenster **Lokal** anzuzeigen, stehen auch zur Verfügung, wenn Sie Office\-Projekte debuggen. Weitere Informationen zu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debugtools finden Sie unter [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
> [!TIP]  
>  Um das Debuggen zu vereinfachen, schließen Sie alle geöffneten Instanzen der Office\-Anwendung, bevor Sie sie erstellen und debuggen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Starten und Beenden des Debuggers  
 Um mit dem Debuggen eines Office\-Projekts zu beginnen, gehen Sie genauso vor wie bei einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projekt. Eine Möglichkeit besteht darin, die F5\-TASTE zu drücken. Wenn Sie mit dem Debuggen eines VSTO\-Add\-In\-Projekts beginnen, wird ein neuer Prozess für die entsprechende Office\-Anwendung gestartet, und das VSTO\-Add\-In wird geladen.  
  
 Wenn Sie mit dem Debuggen eines Projekts auf Dokumentebene beginnen, wird das Dokument oder die Arbeitsmappe in einem neuen Word\- oder Excel\-Prozess geöffnet.  
  
 Wenn Sie den Debugger beenden, bricht der Debugger den Anwendungsprozess abrupt ab oder trennt sich vom Prozess, sofern Sie dies festgelegt haben. Alle anderen Dokumente, die in einem beendeten Office\-Anwendungsprozess geöffnet sind, werden ohne Warnung ebenfalls geschlossen, wobei alle nicht gespeicherten Änderungen verloren gehen. Dazu können alle Dokumente oder Arbeitsmappen gehören, die geöffnet werden, während der Debugger ausgeführt wird.  
  
 Normalerweise empfiehlt es sich, den Prozess vor dem Beenden des Debuggers zu trennen. So können Sie die Office\-Anwendung normal beenden. Wenn Sie nach dem Beenden des Debuggers weiter in einem geöffneten Dokument oder Arbeitsblatt arbeiten möchten, können Sie den Prozess auch zuerst trennen.  
  
 Wenn Sie eine Anpassung auf Dokumentebene für Word debuggen, kann das wiederholte Beenden des Debuggers ein abruptes Schließen von Word zur Folge haben, wodurch die Normal\-Vorlage beschädigt werden kann. In diesem Fall können Sie die beschädigte Normal\-Vorlage löschen. Sie wird beim nächsten Öffnen von Word automatisch neu erstellt. In der Normal\-Vorlage gespeicherte Makros werden allerdings nicht neu erstellt.  
  
### Debuggen von Office 2013\-VSTO\-Add\-Ins mithilfe von Office 2013 oder Office 2016  
 Wenn Sie Visual Studio 2015 verwenden und beide Office\-Versionen nebeneinander installiert sind, startet Visual Studio Office 2016. Wenn Sie Visual Studio 2013 verwenden, startet Visual Studio Office 2013.  
  
 Wenn Sie Ihr VSTO\-Add\-In mithilfe einer anderen Office\-Version \(2013 oder 2016\) debuggen möchten, öffnen Sie den **Projekt\-Designer** und wählen auf der Registerkarte **Debuggen** die Optionsschaltfläche **Externes Programm starten** aus. Navigieren Sie dann zum Speicherort der ausführbaren Datei der entsprechenden Office\-Anwendung.  
  
## Verhalten von F10 und F11  
 Beim Starten des Debuggens eines Office\-Projekts haben F10 und F11 eine andere Funktion als beim Starten des Debuggens anderer Visual Basic\- oder C\#\-Projekte. In Visual Basic\- oder C\#\-Projekten wird der Debugger bei der main\-Funktion angehalten. In Office\-Projekten besitzt Visual Studio dagegen keine Kontrolle über die main\-Funktion der Office\-Anwendung. Während des Debuggens hingegen haben F10 und F11 dieselben Funktionen wie in Visual Basic\- und C\#\-Projekten.  
  
## Anzeigen von Ausnahmen  
 Durch die Art und Weise der Interaktion zwischen verwaltetem und nicht verwaltetem Code werden in Visual Studio keine Fehler angezeigt, die von Microsoft Office\-Anwendungen ausgelöst werden. Wenn ein mithilfe der Office\-Entwicklungstools in Visual Studio erstelltes VSTO\-Add\-In beispielsweise eine Ausnahme auslöst, wird die Ausführung der Microsoft Office\-Anwendung fortgesetzt, ohne dass ein Fehler angezeigt wird. Um diese Fehler anzuzeigen, konfigurieren Sie den Debugger so, dass er bei Ausnahmen der Common Language Runtime anhält. Weitere Informationen finden Sie unter [Gewusst wie: Unterbrechen bei ausgelöster Ausnahme](~/misc/how-to-break-when-an-exception-is-thrown.md).  
  
 Wenn Sie den Debugger so konfigurieren, dass er bei Ausnahmen der Common Language Runtime anhält, wird der Debugger bei jeder Ausnahme aufgerufen. Dazu gehören auch Ausnahmen, die Sie behandelt haben, sowie Ausnahmen \(erste Chance\), die von der Common Language Runtime selbst ausgelöst werden und für das Projekt nicht relevant sind. Fehler, in denen darauf Bezug genommen wird, dass msosec nicht gefunden werden kann, treten in jedem Projekt auf, können aber ignoriert werden. Diese msoec\-Ausnahmen haben keine Auswirkungen auf die Projektmappe.  
  
 Sie können für Methoden auch **Try...Catch**\-Anweisungen verwenden, um Ausnahmen abzufangen.  
  
 In der Standardeinstellung zeigt Visual Studio auch keine Just\-In\-Time\-Debugfehler für Office\-Projekte an. Sie können dieses Feature jedoch aktivieren, um die ausgelösten Fehler anzuzeigen. Weitere Informationen finden Sie unter [Just-In-Time-Debuggen in Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
## Befehlszeilenargumente  
 Wenn auf der Debugeigenschaftenseite die **Startaktion** auf **Projekt starten** festgelegt wird, werden beim Debuggen des Projekts von Visual Studio keine Befehlszeilenargumente verwendet. Dies ist auch dann der Fall, wenn Befehlszeilenargumente als Startoptionen angegeben wurden. Wenn Sie beim Debuggen Befehlszeilenargumente verwenden möchten, müssen Sie eine andere **Startaktion** als **Projekt starten** auswählen.  
  
## Quellcodeverwaltung  
 In der Quellcodeverwaltung werden Debugeigenschaften nicht für mehrere Benutzer gemeinsam verwendet. In Visual Basic\- und C\#\-Projekten werden die Debugeigenschaften in einer benutzerspezifischen Datei \(„*ProjectName*.vbproj.user“ oder „*ProjectName*.csproj.user“\) gespeichert, und diese Datei wird nicht in die Quellcodeverwaltung einbezogen. Wenn mehrere Personen debuggen, muss jede Person die Debugeigenschaften manuell eingeben.  
  
## Debuggen zwischengespeicherter Datasets in einem Projekt auf Dokumentebene  
 Bei jeder Erstellung eines Projekts wird das Dataset geleert und neu erstellt. Wenn Sie ein zwischengespeichertes Dataset debuggen möchten, müssen Sie das Dokument außerhalb von Visual Studio öffnen und dann den Debugger anfügen.  
  
## Debuggen von Word\-Dokumentprojekten auf Grundlage des Dokumentformats für Word 97\-2003 \(\*.doc\).  
 Zum Debuggen eines Word\-Dokumentprojekts, das auf dem Dokumentformat für Word 97\-2003 \(\*.doc\) basiert, müssen Sie den Projektordner der Liste vertrauenswürdiger Ordner hinzufügen. Weitere Informationen hierzu finden Sie unter [Gewähren von Vertrauenswürdigkeit für Dokumente](../vsto/granting-trust-to-documents.md).  
  
## Debuggen deaktivierter Add\-Ins  
 VSTO\-Add\-Ins, die ein unerwartetes Verhalten aufweisen, können von Microsoft Office\-Anwendungen deaktiviert werden. Solche VSTO\-Add\-Ins werden von der Microsoft Office\-Anwendung deaktiviert, um zu verhindern, dass bei jedem Start der Anwendung problematischer Code geladen wird. Aber auch beim typischen Debuggen kann es zu unerwartetem Verhalten kommen. Informationen zum erneuten Aktivieren von VSTO\-Add\-Ins finden Sie unter [Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Es gibt zwei Arten der Deaktivierung von VSTO\-Add\-Ins in Microsoft Office\-Anwendungen: harte Deaktivierung und weiche Deaktivierung.  
  
### Harte Deaktivierung  
 Die harte Deaktivierung kann auftreten, wenn ein VSTO\-Add\-In zur unerwarteten Beendigung einer Anwendung führt. Sie kann auch auf dem Entwicklungscomputer auftreten, wenn Sie den Debugger beenden, während der <xref:Microsoft.Office.Tools.AddIn.Startup>\-Ereignishandler im VSTO\-Add\-In ausgeführt wird. Wenn ein VSTO\-Add\-In hart deaktiviert wird, wird es in der Liste **Deaktivierte Elemente** in der Anwendung angezeigt.  
  
 Wenn eine Office\-Anwendung ein VSTO\-Add\-In hart deaktiviert, das mit den Office\-Entwicklungstools in Visual Studio erstellt wurde, deaktiviert die Anwendung nur das VSTO\-Add\-In, das den Fehler verursacht hat. Andere VSTO\-Add\-Ins, die mit den Office\-Entwicklungstools in Visual Studio für diese Office\-Anwendung erstellt wurden, werden weiterhin geladen.  
  
### Weiche Deaktivierung  
 Die weiche Deaktivierung kann auftreten, wenn ein VSTO\-Add\-In einen Fehler erzeugt, der nicht zur unerwarteten Beendigung der Anwendung führt. Ein VSTO\-Add\-In kann von einer Anwendung z. B. weich deaktiviert werden, wenn es einen Ausnahmefehler auslöst, während der <xref:Microsoft.Office.Tools.AddIn.Startup>\-Ereignishandler ausgeführt wird. Wenn ein VSTO\-Add\-In weich deaktiviert wird, wird es in der Liste **Inaktive Anwendungs\-Add\-Ins** in der Anwendung angezeigt, und die Anwendung ändert den Wert des Registrierungseintrags **LoadBehavior** für das VSTO\-Add\-In, um anzugeben, dass es entladen wurde. Weitere Informationen zum Registrierungseintrag **LoadBehavior** finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Problembehandlung von Installationsfehlern mithilfe der Ereignisanzeige  
 Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] schreibt Meldungen für alle Ausnahmen, die beim Installieren oder Deinstallieren von Office\-Projektmappen ausgelöst werden, in die Ereignisanzeige in Windows. Anhand dieser Meldungen können Sie Installations\- und Bereitstellungsprobleme beheben.  
  
## Problembehandlung von Startfehlern mithilfe einer Protokolldatei und Fehlermeldungen  
 Alle beim Start auftretenden Fehler können von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] in eine Protokolldatei geschrieben oder in einem Meldungsfeld angezeigt werden. Standardmäßig werden diese Optionen deaktiviert. Durch das Erstellen von Umgebungsvariablen können Sie diese Optionen aktivieren.  
  
 Um jeden Fehler in einem Meldungsfeld anzuzeigen, erstellen Sie eine Umgebungsvariable mit dem Namen `VSTO_SUPPRESSDISPLAYALERTS`, die Sie auf 0 \(null\) festlegen. Sie können die Meldungen unterdrücken, indem Sie die Umgebungsvariable löschen oder auf 1 \(eins\) festlegen.  
  
 Um die Fehler in eine Protokolldatei zu schreiben, erstellen Sie eine Umgebungsvariable mit dem Namen `VSTO_LOGALERTS`, die Sie auf 1 \(eins\) festlegen. Die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] erstellt die Protokolldatei in dem Ordner, der das Bereitstellungsmanifest für das VSTO\-Add\-In enthält, bzw. dem Ordner, der das Dokument oder die Arbeitsmappe enthält, das bzw. die der Anpassung zugeordnet ist. Wenn dieser Vorgang fehlschlägt, erstellt die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] die Protokolldatei im lokalen Ordner "%TEMP%". Für VSTO\-Add\-Ins auf Anwendungsebene lautet der Standardname „*Add\-In\-Name*.vsto.log“. Für Projekte auf Dokumentebene lautet der Name der Protokolldatei „*Dokumentname*.*Erweiterung*.log“; Beispiel: „ExcelWorkbook1.xlsx.log“. Um die Fehlerprotokollierung zu beenden, löschen Sie die Umgebungsvariable, oder legen Sie sie auf 0 \(null\) fest.  
  
## Siehe auch  
 [Aktualisieren von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Gewusst wie: Erneutes Aktivieren eines VSTO-Add-Ins, das deaktiviert wurde](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  