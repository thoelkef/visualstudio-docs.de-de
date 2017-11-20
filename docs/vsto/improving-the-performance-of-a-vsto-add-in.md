---
title: Verbessern der Leistung eines VSTO-Add-Ins | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa8aba456e6912569480305922511f6ffebe674b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="improving-the-performance-of-a-vsto-add-in"></a>Verbessern der Leistung eines VSTO-Add-Ins
  Sie können die Benutzererfahrung verbessern, indem Sie VSTO-Add-Ins optimieren, die Sie für Office-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente schnell geöffnet und andere Aufgaben rasch ausgeführt werden können. Wenn das VSTO-Add-In für Outlook bestimmt ist, können Sie das Risiko senken, dass das VSTO-Add-In aufgrund schwacher Leistung deaktiviert wird. Sie können die Leistung des VSTO-Add-Ins mithilfe der folgenden Strategien steigern:  
  
-   [Bedarfsgesteuertes Laden von VSTO-Add-Ins](#Load).  
  
-   [Office-Projektmappen mit Windows Installer veröffentlichen](#Publish).  
  
-   [Menübandreflektion umgehen](#Bypass).  
  
-   [Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen](#Perform).  
  
 Weitere Informationen zur Optimierung eines VSTO-Add-Ins finden Sie im Abschnitt zu den [Leistungskriterien zur kontinuierlichen Aktivierung von VSTO-Add-Ins](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Bedarfsgesteuertes Laden von VSTO-Add-Ins  
 Sie können ein VSTO-Add-In so konfigurieren, dass es nur unter folgenden Umständen geladen wird:  
  
-   Beim ersten Start der Anwendung nach Installation des VSTO-Add-Ins.  
  
-   Bei der ersten Interaktion des Benutzers mit dem VSTO-Add-In nach weiteren Starts der Anwendung.  
  
 Angenommen, Ihr VSTO-Add-in füllt unter Umständen ein Arbeitsblatt mit Daten, wenn der Benutzer eine benutzerdefinierte Schaltfläche auswählt, die mit der Bezeichnung **Meine Daten abrufen**. Die Anwendung muss das VSTO-Add-In mindestens einmal laden, damit die Schaltfläche **Meine Daten abrufen** im Menüband angezeigt werden kann. Allerdings nicht das VSTO-Add-in erneut geladen Wenn der Benutzer die Anwendung das nächste Mal gestartet wird. Das VSTO-Add-In wird nur geladen, wenn der Benutzer die Schaltfläche **Meine Daten abrufen** auswählt.  
  
#### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine ClickOnce-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden  
  
1.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
2.  Wählen Sie in der Menüleiste **Ansicht**, **Eigenschaftenseiten**.  
  
3.  Wählen Sie auf der Registerkarte **Veröffentlichen** die Schaltfläche **Optionen** aus.  
  
4.  Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** das Listenelement **Office-Einstellungen** . Wählen Sie die Option **Bedarfsgesteuert laden** und anschließend die Schaltfläche **OK** aus.  
  
#### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine Windows Installer-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden  
  
1.  Legen Sie in der Registrierung der `LoadBehavior` Eintrag des der *Root*\Software\Microsoft\Office\\*Parameter "ApplicationName"*\Addins\\*Add-in ID*um **0 x 10**.  
  
     Weitere Informationen finden Sie unter [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>So konfigurieren Sie eine Projektmappe so, dass VSTO-Add-Ins beim Debuggen der Projektmappe bedarfsgesteuert geladen werden  
  
1.  Erstellen Sie ein Skript, das `LoadBehavior` Eintrag des der *Root*\Software\Microsoft\Office\\*Parameter "ApplicationName"*\Addins\\*Add-in-ID* um **0 x 10**.  
  
     Der folgende Code ist ein Beispiel für ein solches Skript.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Erstellen Sie ein Postbuildereignis, das die Registrierung mithilfe des Skripts aktualisiert.  
  
     Der folgende Code veranschaulicht eine Befehlszeichenfolge, die Sie einem Postbuildereignis hinzufügen können.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Informationen über das Erstellen eines postbuildereignisses in einem C#-Projekt finden Sie unter [Vorgehensweise: Angeben von Buildereignissen &#40; C &#35; &#41; ](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Informationen über das Erstellen eines postbuildereignisses in einem Visual Basic-Projekt finden Sie unter [Vorgehensweise: Angeben von Buildereignissen &#40; Visual Basic &#41; ](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Publish Office Solutions by Using Windows Installer  
 Wenn Sie die Projektmappe mit Windows Installer veröffentlichen, umgeht Visual Studio 2010-Tools für Office-Laufzeit beim Laden des VSTO-Add-Ins die folgenden Schritte.  
  
-   Überprüfen des Manifestschemas.  
  
-   Automatische Überprüfung auf Updates.  
  
-   Überprüfen der digitalen Signaturen der Bereitstellungsmanifeste.  
  
    > [!NOTE]  
    >  Dieser Ansatz ist nicht erforderlich, wenn Sie Ihr VSTO-Add-in an einem sicheren Ort auf den Computern der Benutzer bereitstellen.  
  
 Weitere Informationen finden Sie unter [Deploying an Office Solution by Using Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Bypass Ribbon Reflection  
 Wenn Sie eine Projektmappe mithilfe von [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]erstellen, stellen Sie sicher, dass beim Bereitstellen der Projektmappe die neueste Version von Visual Studio 2010-Tools für Office-Laufzeit auf den Benutzercomputern installiert ist. Ältere Versionen dieser Laufzeit reflektierten in Projektmappenassemblys, um Menübandanpassungen zu suchen. Dieser Prozess kann zur Folge haben, dass das VSTO-Add-In langsamer geladen wird.  
  
 Alternativ können Sie für jede Version von Visual Studio 2010-Tools für Office-Laufzeit festlegen, dass keine Reflektion zum Identifizieren von Menübandanpassungen verwendet wird. Überschreiben Sie dazu die `CreateRibbonExtensibility` -Methode, und geben Sie explizit Menübandobjekte zurück. Wenn Ihr VSTO-Add-in menübandanpassungen enthält, zurück `null` innerhalb der Methode.  
  
 Im folgenden Beispiel wird ein Menübandobjekt basierend auf dem Wert eines Felds zurückgegeben.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Perform Expensive Operations in a Separate Execution Thread  
 Erwägen Sie, zeitintensive Aufgaben (z. B. Aufgaben mit langer Ausführungsdauer, Datenbankverbindungen oder andere Arten von Netzwerkaufrufen) in einem separaten Thread auszuführen. Weitere Informationen finden Sie unter [Threading Support in Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Der gesamte Code, der das Office-Objektmodell aufruft, muss im Hauptthread ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Bedarfsgesteuertes Laden von VSTO-Add-Ins](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Verzögertes Laden der CLR in Office-Add-ins](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [VSTO-Leistung: Verzögertes Laden und Entwickler (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Leistungsverbesserungen in Kürze für ein Servicepack in Ihrer Nähe (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO-Leistung: Menübandreflektion (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  