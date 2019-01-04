---
title: Verbesserung der Leistung eines VSTO-Add-Ins
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc4a65a0b09a706eebad04c90e1779d00c7f3801
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937282"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Verbesserung der Leistung eines VSTO-add-Ins
  Sie können die Benutzererfahrung verbessern, indem Sie VSTO-Add-Ins optimieren, die Sie für Office-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente schnell geöffnet und andere Aufgaben rasch ausgeführt werden können. Wenn das VSTO-Add-In für Outlook bestimmt ist, können Sie das Risiko senken, dass das VSTO-Add-In aufgrund schwacher Leistung deaktiviert wird. Sie können die Leistung des VSTO-Add-Ins mithilfe der folgenden Strategien steigern:

- [Bedarfsgesteuertes Laden von VSTO-Add-Ins](#Load).

- [Office-Projektmappen mit Windows Installer veröffentlichen](#Publish).

- [Menübandreflektion](#Bypass).

- [Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen](#Perform).

  Weitere Informationen dazu, wie Sie ein Outlook VSTO-Add-in zu optimieren, finden Sie unter [Leistungskriterien zu VSTO-Add-ins aktiviert](http://go.microsoft.com/fwlink/?LinkID=266503).

##  <a name="Load"></a> Bedarfsgesteuertes Laden von VSTO-Add-Ins
 Sie können ein VSTO-Add-In so konfigurieren, dass es nur unter folgenden Umständen geladen wird:

- Beim ersten Start der Anwendung nach Installation des VSTO-Add-Ins.

- Bei der ersten Interaktion des Benutzers mit dem VSTO-Add-In nach weiteren Starts der Anwendung.

  Angenommen, Ihr VSTO-Add-in füllt unter Umständen ein Arbeitsblatt mit Daten, wenn der Benutzer eine benutzerdefinierte Schaltfläche mit der Bezeichnung **Meine Daten abrufen**. Die Anwendung muss das VSTO-Add-in mindestens einmal laden, damit die **Meine Daten abrufen** Schaltfläche im Menüband angezeigt werden kann. Allerdings nicht das VSTO-Add-in erneut geladen, wenn der Benutzer die Anwendung das nächste Mal startet. Das VSTO-Add-In wird nur geladen, wenn der Benutzer die Schaltfläche **Meine Daten abrufen** auswählt.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine ClickOnce-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden

1.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.

2.  Wählen Sie in der Menüleiste **Ansicht** >  **Eigenschaftenseiten** aus.

3.  Wählen Sie auf der Registerkarte **Veröffentlichen** die Schaltfläche **Optionen** aus.

4.  Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** das Listenelement **Office-Einstellungen** . Wählen Sie die Option **Bedarfsgesteuert laden** und anschließend die Schaltfläche **OK** aus.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine Windows Installer-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden

1.  Legen Sie in der Registrierung der `LoadBehavior` Eintrag, der die **_Stamm_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Add-in-ID_** um **0 x 10**.

     Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>So konfigurieren Sie eine Projektmappe so, dass VSTO-Add-Ins beim Debuggen der Projektmappe bedarfsgesteuert geladen werden

1.  Erstellen Sie ein Skript, das `LoadBehavior` Eintrag, der die **_Stamm_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Add-in-ID_** um **0 x 10**.

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

     Informationen zum Erstellen von Postbuildereignis in einer C# Projekt, finden Sie unter [Vorgehensweise: Festlegen von Buildereignissen &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Weitere Informationen zur Verwendung ein postbuildereignisses in einem Visual Basic-Projekt zu erstellen, finden Sie unter [Vorgehensweise: Festlegen von Buildereignissen &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

##  <a name="Publish"></a> Veröffentlichen Sie Office-Projektmappen mithilfe von Windows Installer
 Wenn Sie die Projektmappe mit Windows Installer veröffentlichen, umgeht Visual Studio 2010-Tools für Office-Laufzeit die folgenden Schritte aus, wenn das VSTO-Add-in geladen wird.

- Überprüfen des Manifestschemas.

- Automatische Überprüfung auf Updates.

- Überprüfen der digitalen Signaturen der Bereitstellungsmanifeste.

  > [!NOTE]
  >  Dieser Ansatz ist nicht erforderlich, wenn Sie an einem sicheren Speicherort auf den Computern der Benutzer das VSTO-Add-in bereitstellen.

  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe mit Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

##  <a name="Bypass"></a> Menübandreflektion umgehen
 Wenn Sie eine Lösung mit erstellen [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], stellen Sie sicher, dass die Benutzer die neueste Version von Visual Studio 2010-Tools für Office-Laufzeit installiert haben, wenn Sie die Lösung bereitstellen. Ältere Versionen dieser Laufzeit reflektierten in Projektmappenassemblys, um menübandanpassungen zu suchen. Dieser Prozess kann zur Folge haben, dass das VSTO-Add-In langsamer geladen wird.

 Als Alternative können Sie verhindern, dass jede Version von Visual Studio 2010-Tools für Office-Laufzeit mithilfe von Reflektion zum Identifizieren von menübandanpassungen. Um diese Strategie zu folgen, außer Kraft setzen der `CreateRibbonExtensibility` -Methode, und die Menüband-Objekte explizit zurück. Wenn Ihr VSTO-Add-in keine menübandanpassungen enthält, zurück `null` innerhalb der Methode.

 Das folgende Beispiel gibt ein menübandobjekt basierend auf dem Wert eines Felds zurück.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

##  <a name="Perform"></a> Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen
 Erwägen Sie, zeitintensive Aufgaben (z. B. Aufgaben mit langer Ausführungsdauer, Datenbankverbindungen oder andere Arten von Netzwerkaufrufen) in einem separaten Thread auszuführen. Weitere Informationen finden Sie unter [Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).

> [!NOTE]
>  Der gesamte Code, der das Office-Objektmodell aufruft, muss im Hauptthread ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Bedarfsgesteuertes Laden von VSTO-Add-ins](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Verzögertes Laden der CLR in Office-Add-ins](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Erstellen von VSTO-Add-ins für Office mit Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
