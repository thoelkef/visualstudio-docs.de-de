---
title: "Verbessern der Leistung eines VSTO-Add-Ins | Microsoft Docs"
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
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Verbessern der Leistung eines VSTO-Add-Ins
  Sie können die Benutzererfahrung verbessern, indem Sie VSTO\-Add\-Ins optimieren, die Sie für Office\-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente schnell geöffnet und andere Aufgaben rasch ausgeführt werden können. Wenn das VSTO\-Add\-In für Outlook bestimmt ist, können Sie das Risiko senken, dass das VSTO\-Add\-In aufgrund schwacher Leistung deaktiviert wird. Sie können die Leistung des VSTO\-Add\-Ins mithilfe der folgenden Strategien steigern:  
  
-   [Bedarfsgesteuertes Laden von VSTO\-Add\-Ins](#Load).  
  
-   [Office\-Projektmappen mit Windows Installer veröffentlichen](#Publish).  
  
-   [Menübandreflektion umgehen](#Bypass).  
  
-   [Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen](#Perform).  
  
 Weitere Informationen zur Optimierung eines VSTO\-Add\-Ins finden Sie im Abschnitt zu den [Leistungskriterien zur kontinuierlichen Aktivierung von VSTO\-Add\-Ins](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Bedarfsgesteuertes Laden von VSTO\-Add\-Ins  
 Sie können ein VSTO\-Add\-In so konfigurieren, dass es nur unter folgenden Umständen geladen wird:  
  
-   Beim ersten Start der Anwendung nach Installation des VSTO\-Add\-Ins.  
  
-   Bei der ersten Interaktion des Benutzers mit dem VSTO\-Add\-In nach weiteren Starts der Anwendung.  
  
 Beispielsweise füllt das VSTO\-Add\-In unter Umständen ein Arbeitsblatt mit Daten aus, wenn der Benutzer eine benutzerdefinierte Schaltfläche mit der Bezeichnung **Meine Daten abrufen** auswählt. Die Anwendung muss das VSTO\-Add\-In mindestens einmal laden, damit die Schaltfläche **Meine Daten abrufen** im Menüband angezeigt werden kann. Das VSTO\-Add\-In wird jedoch beim nächsten Starten der Anwendung nicht erneut geladen. Das VSTO\-Add\-In wird nur geladen, wenn der Benutzer die Schaltfläche **Meine Daten abrufen** auswählt.  
  
#### So konfigurieren Sie eine ClickOnce\-Projektmappe, um VSTO\-Add\-Ins bedarfsgesteuert zu laden  
  
1.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten aus.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.  
  
3.  Wählen Sie auf der Registerkarte **Veröffentlichen** die Schaltfläche **Optionen** aus.  
  
4.  Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** das Listenelement **Office\-Einstellungen**. Wählen Sie die Option **Bedarfsgesteuert laden** und anschließend die Schaltfläche **OK** aus.  
  
#### So konfigurieren Sie eine Windows Installer\-Projektmappe, um VSTO\-Add\-Ins bedarfsgesteuert zu laden  
  
1.  Legen Sie in der Registrierung den Eintrag `LoadBehavior` unter dem Schlüssel *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* auf **0x10** fest.  
  
     Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### So konfigurieren Sie eine Projektmappe so, dass VSTO\-Add\-Ins beim Debuggen der Projektmappe bedarfsgesteuert geladen werden  
  
1.  Erstellen Sie ein Skript, mit dem der Eintrag `LoadBehavior` unter dem Schlüssel *Root*\\Software\\Microsoft\\Office\\*ApplicationName*\\Addins\\*Add\-in ID* auf **0x10** festgelegt wird.  
  
     Der folgende Code ist ein Beispiel für ein solches Skript.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn] "Description"="MyAddIn" "FriendlyName"="MyAddIn" "LoadBehavior"=dword:00000010 "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Erstellen Sie ein Postbuildereignis, das die Registrierung mithilfe des Skripts aktualisiert.  
  
     Der folgende Code veranschaulicht eine Befehlszeichenfolge, die Sie einem Postbuildereignis hinzufügen können.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Informationen zum Erstellen eines Postbuildereignisses in einem C\#\-Projekt finden Sie unter [Gewusst wie: Angeben von Buildereignissen &#40;C&#35;&#41;](../Topic/How%20to:%20Specify%20Build%20Events%20(C%23).md).  
  
     Weitere Informationen zum Erstellen eines Postbuildereignisses in einem Visual Basic\-Projekt finden Sie unter [Gewusst wie: Angeben von Buildereignissen &#40;C&#35;&#41;](../Topic/How%20to:%20Specify%20Build%20Events%20(C%23).md).  
  
##  <a name="Publish"></a> Office\-Projektmappen mit Windows Installer veröffentlichen  
 Wenn Sie die Projektmappe mit Windows Installer veröffentlichen, umgeht Visual Studio 2010\-Tools für Office\-Laufzeit beim Laden des VSTO\-Add\-Ins die folgenden Schritte.  
  
-   Überprüfen des Manifestschemas.  
  
-   Automatische Überprüfung auf Updates.  
  
-   Überprüfen der digitalen Signaturen der Bereitstellungsmanifeste.  
  
    > [!NOTE]  
    >  Dieser Ansatz ist nicht erforderlich, wenn Sie das VSTO\-Add\-In an einem sicheren Ort auf den Computern der Benutzer bereitstellen.  
  
 Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Menübandreflektion umgehen  
 Wenn Sie eine Projektmappe mithilfe von [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] erstellen, stellen Sie sicher, dass beim Bereitstellen der Projektmappe die neueste Version von Visual Studio 2010\-Tools für Office\-Laufzeit auf den Benutzercomputern installiert ist. Ältere Versionen dieser Laufzeit reflektierten in Projektmappenassemblys, um Menübandanpassungen zu suchen. Dieser Prozess kann zur Folge haben, dass das VSTO\-Add\-In langsamer geladen wird.  
  
 Alternativ können Sie für jede Version von Visual Studio 2010\-Tools für Office\-Laufzeit festlegen, dass keine Reflektion zum Identifizieren von Menübandanpassungen verwendet wird. Überschreiben Sie dazu die `CreateRibbonExtensibility`\-Methode, und geben Sie explizit Menübandobjekte zurück. Wenn das VSTO\-Add\-In keine Menübandanpassungen enthält, geben Sie `null` innerhalb der Methode zurück.  
  
 Im folgenden Beispiel wird ein Menübandobjekt basierend auf dem Wert eines Felds zurückgegeben.  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
##  <a name="Perform"></a> Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen  
 Erwägen Sie, zeitintensive Aufgaben \(z. B. Aufgaben mit langer Ausführungsdauer, Datenbankverbindungen oder andere Arten von Netzwerkaufrufen\) in einem separaten Thread auszuführen. Weitere Informationen finden Sie unter [Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Der gesamte Code, der das Office\-Objektmodell aufruft, muss im Hauptthread ausgeführt werden.  
  
## Siehe auch  
 [Bedarfsgesteuertes Laden von VSTO\-Add\-Ins](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Verzögertes Laden der CLR in Office\-Add\-Ins](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [VSTO\-Leistung: Verzögertes Laden und der Entwickler \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Leistungsverbesserungen, die in Kürze für ein Service\-Pack in Ihrer Nähe verfügbar sind \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO\-Leistung: Menübandreflektion \(Stephen Peters\)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  