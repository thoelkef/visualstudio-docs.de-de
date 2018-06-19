---
title: Verbessern der Leistung von einem VSTO-Add-in
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cc1605a61d63a5d314ae1f02d864124185546ada
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34269013"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Verbessern der Leistung des VSTO-add-Ins
  Sie können die Benutzererfahrung verbessern, indem Sie VSTO-Add-Ins optimieren, die Sie für Office-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente schnell geöffnet und andere Aufgaben rasch ausgeführt werden können. Wenn das VSTO-Add-In für Outlook bestimmt ist, können Sie das Risiko senken, dass das VSTO-Add-In aufgrund schwacher Leistung deaktiviert wird. Sie können die Leistung des VSTO-Add-Ins mithilfe der folgenden Strategien steigern:  
  
-   [Bedarfsgesteuertes Laden von VSTO-Add-Ins](#Load).  
  
-   [Office-Projektmappen mit Windows Installer veröffentlichen](#Publish).  
  
-   [Menübandreflektion](#Bypass).  
  
-   [Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen](#Perform).  
  
 Weitere Informationen zu einem Outlook-VSTO-Add-in zu optimieren, finden Sie unter [Leistungskriterien zu VSTO-Add-ins aktiviert](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Bedarfsgesteuertes Laden von VSTO-Add-Ins  
 Sie können ein VSTO-Add-In so konfigurieren, dass es nur unter folgenden Umständen geladen wird:  
  
-   Beim ersten Start der Anwendung nach Installation des VSTO-Add-Ins.  
  
-   Bei der ersten Interaktion des Benutzers mit dem VSTO-Add-In nach weiteren Starts der Anwendung.  
  
 Angenommen, Ihr VSTO-Add-in füllt unter Umständen ein Arbeitsblatt mit Daten, wenn der Benutzer eine benutzerdefinierte Schaltfläche auswählt, die mit der Bezeichnung **Meine Daten abrufen**. Die Anwendung muss das VSTO-Add-in mindestens einmal laden, damit die **Meine Daten abrufen** Schaltfläche im Menüband angezeigt werden kann. Allerdings nicht das VSTO-Add-in erneut geladen Wenn der Benutzer die Anwendung das nächste Mal gestartet wird. Das VSTO-Add-In wird nur geladen, wenn der Benutzer die Schaltfläche **Meine Daten abrufen** auswählt.  
  
### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine ClickOnce-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden  
  
1.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
2.  Wählen Sie in der Menüleiste **Ansicht** >  **Eigenschaftenseiten** aus.  
  
3.  Wählen Sie auf der Registerkarte **Veröffentlichen** die Schaltfläche **Optionen** aus.  
  
4.  Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** das Listenelement **Office-Einstellungen** . Wählen Sie die Option **Bedarfsgesteuert laden** und anschließend die Schaltfläche **OK** aus.  
  
### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine Windows Installer-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden  
  
1.  Legen Sie in der Registrierung der `LoadBehavior` Eintrag, der die **_Stamm_\Software\Microsoft\Office\\_Parameter "ApplicationName"_ \Addins\\  _Add-in-ID_** um **0 x 10**.  
  
     Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>So konfigurieren Sie eine Projektmappe so, dass VSTO-Add-Ins beim Debuggen der Projektmappe bedarfsgesteuert geladen werden  
  
1.  Erstellen Sie ein Skript, das `LoadBehavior` Eintrag, der die **_Stamm_\Software\Microsoft\Office\\_Parameter "ApplicationName"_ \Addins\\  _Add-in-ID_** um **0 x 10**.  
  
     Der folgende Code ist ein Beispiel für ein solches Skript.  
  
    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Erstellen Sie ein Postbuildereignis, das die Registrierung mithilfe des Skripts aktualisiert.  
  
     Der folgende Code veranschaulicht eine Befehlszeichenfolge, die Sie einem Postbuildereignis hinzufügen können.  
  
    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Informationen über das Erstellen eines postbuildereignisses in einem C#-Projekt finden Sie unter [Vorgehensweise: angeben Buildereignisse &#40;C&#35;&#41;](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Informationen über das Erstellen eines postbuildereignisses in einem Visual Basic-Projekt finden Sie unter [Vorgehensweise: angeben Buildereignisse &#40;Visual Basic&#41;](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Veröffentlichen Sie Office-Projektmappen mit Windows Installer  
 Wenn Sie die Projektmappe mit Windows Installer veröffentlichen, umgeht Visual Studio 2010-Tools für Office-Laufzeit die folgenden Schritte aus, wenn das VSTO-Add-in geladen wird.  
  
-   Überprüfen des Manifestschemas.  
  
-   Automatische Überprüfung auf Updates.  
  
-   Überprüfen der digitalen Signaturen der Bereitstellungsmanifeste.  
  
    > [!NOTE]  
    >  Dieser Ansatz ist nicht erforderlich, wenn Sie Ihr VSTO-Add-in an einem sicheren Ort auf den Computern der Benutzer bereitstellen.  
  
 Weitere Informationen finden Sie unter [bereitstellen eine Office-Projektmappe mit Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Menübandreflektion umgehen  
 Wenn Sie eine Projektmappe mit erstellen [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], stellen Sie sicher, dass Ihre Benutzer die neueste Version von Visual Studio 2010-Tools für Office-Laufzeit installiert haben, wenn Sie die Projektmappe bereitstellen. Ältere Versionen dieser Laufzeit reflektierten in Projektmappenassemblys, um menübandanpassungen zu suchen. Dieser Prozess kann zur Folge haben, dass das VSTO-Add-In langsamer geladen wird.  
  
 Als Alternative können Sie verhindern, dass eine beliebige Version von Visual Studio 2010-Tools für Office-Laufzeit Reflektion zum Identifizieren von menübandanpassungen verwendet werden. Um diese Strategie zu folgen, überschreiben die `CreateRibbonExtensibility` -Methode und explizit Rückgabeobjekt Menüband. Wenn Ihr VSTO-Add-in menübandanpassungen enthält, zurück `null` innerhalb der Methode.  
  
 Im folgende Beispiel gibt ein menübandobjekt basierend auf dem Wert eines Felds zurück.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen  
 Erwägen Sie, zeitintensive Aufgaben (z. B. Aufgaben mit langer Ausführungsdauer, Datenbankverbindungen oder andere Arten von Netzwerkaufrufen) in einem separaten Thread auszuführen. Weitere Informationen finden Sie unter [Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Der gesamte Code, der das Office-Objektmodell aufruft, muss im Hauptthread ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Bedarfsgesteuertes Laden von VSTO-Add-ins](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Verzögertes Laden der CLR in Office-Add-ins](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [VSTO-Leistung: verzögertes Laden und (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Leistungsverbesserungen in Kürze für ein Servicepack Nähe (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [VSTO-Leistung: Menüband Reflektion (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  