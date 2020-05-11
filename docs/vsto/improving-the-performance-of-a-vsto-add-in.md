---
title: Verbessern der Leistung eines VSTO Add-Ins
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416548"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Verbessern der Leistung eines VSTO-Add-Ins
  Sie können die Benutzererfahrung verbessern, indem Sie VSTO-Add-Ins optimieren, die Sie für Office-Anwendungen erstellen, sodass diese schnell gestartet und heruntergefahren, Elemente schnell geöffnet und andere Aufgaben rasch ausgeführt werden können. Wenn das VSTO-Add-In für Outlook bestimmt ist, können Sie das Risiko senken, dass das VSTO-Add-In aufgrund schwacher Leistung deaktiviert wird. Sie können die Leistung des VSTO-Add-Ins mithilfe der folgenden Strategien steigern:

- [Bedarfsgesteuertes Laden von VSTO-Add-Ins](#Load).

- [Office-Projektmappen mit Windows Installer veröffentlichen](#Publish).

- [Bypass-Band-Reflektion](#Bypass).

- [Kostenintensive Vorgänge in einem separaten Ausführungsthread ausführen](#Perform).

  Weitere Informationen zum Optimieren eines Outlook VSTO-Add-Ins finden Sie unter [Leistungskriterien, um VSTO-Add-Ins aktiviert zu halten.](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>VSTO-Add-Ins bei Bedarf laden
 Sie können ein VSTO-Add-In so konfigurieren, dass es nur unter folgenden Umständen geladen wird:

- Beim ersten Start der Anwendung nach Installation des VSTO-Add-Ins.

- Bei der ersten Interaktion des Benutzers mit dem VSTO-Add-In nach weiteren Starts der Anwendung.

  Beispielsweise kann Ihr VSTO-Add-In ein Arbeitsblatt mit Daten füllen, wenn der Benutzer eine benutzerdefinierte Schaltfläche mit der Bezeichnung **"Meine Daten abrufen"** auswählt. Die Anwendung muss Ihr VSTO-Add-In mindestens einmal laden, damit die Schaltfläche **"Meine Daten abrufen"** in der Multifunktionsleiste angezeigt werden kann. Das VSTO-Add-In wird jedoch nicht erneut geladen, wenn der Benutzer die Anwendung das nächste Mal startet. Das VSTO-Add-In wird nur geladen, wenn der Benutzer die Schaltfläche **Meine Daten abrufen** auswählt.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine ClickOnce-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden

1. Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.

2. Wählen Sie in der Menüleiste**Eigenschaftenseiten** **anzeigen** > aus.

3. Wählen Sie auf der Registerkarte **Veröffentlichen** die Schaltfläche **Optionen** aus.

4. Wählen Sie im Dialogfeld **Veröffentlichungsoptionen** das Listenelement **Office-Einstellungen** . Wählen Sie die Option **Bedarfsgesteuert laden** und anschließend die Schaltfläche **OK** aus.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>So konfigurieren Sie eine Windows Installer-Projektmappe, um VSTO-Add-Ins bedarfsgesteuert zu laden

1. Legen Sie in `LoadBehavior` der Registrierung den Eintrag des **Schlüssels _"Root"-Datei_"Root"-Software-Microsoft-Office-Anwendungsname\\_ApplicationName_,Addins-Add-In-ID-Schlüssel\\** auf **0x10**fest.

     Weitere Informationen finden Sie unter [Registrierungseinträge für VSTO-Add-Ins](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>So konfigurieren Sie eine Projektmappe so, dass VSTO-Add-Ins beim Debuggen der Projektmappe bedarfsgesteuert geladen werden

1. Erstellen Sie ein `LoadBehavior` Skript, das den Eintrag des ** _Schlüssels_\\\\"Root" für die Datei "Root" und "Microsoft"Office_ApplicationName"_ auf** **0x10**festsetzt.

     Der folgende Code ist ein Beispiel für ein solches Skript.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Erstellen Sie ein Postbuildereignis, das die Registrierung mithilfe des Skripts aktualisiert.

     Der folgende Code veranschaulicht eine Befehlszeichenfolge, die Sie einem Postbuildereignis hinzufügen können.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Informationen zum Erstellen von Postbuildereignissen in einem C-Projekt finden Sie unter [Gewusst wie: Angeben ](../ide/how-to-specify-build-events-csharp.md)von Buildereignissen &#40;C&#35;&#41;.

     Informationen zum Erstellen eines Postbuildereignisses in einem Visual Basic-Projekt finden Sie unter [Gewusst wie: Angeben ](../ide/how-to-specify-build-events-visual-basic.md)von Buildereignissen &#40;Visual Basic&#41;.

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Veröffentlichen von Office-Lösungen mithilfe von Windows Installer
 Wenn Sie Ihre Projektmappe mit Windows Installer veröffentlichen, umgeht die Visual Studio 2010-Laufzeit "Tools for Office" die folgenden Schritte, wenn das VSTO-Add-In geladen wird.

- Überprüfen des Manifestschemas.

- Automatische Überprüfung auf Updates.

- Überprüfen der digitalen Signaturen der Bereitstellungsmanifeste.

  > [!NOTE]
  > Dieser Ansatz ist nicht erforderlich, wenn Sie Ihr VSTO-Add-In an einem sicheren Speicherort auf den Computern der Benutzer bereitstellen.

  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Bypass-Bandreflexion
 Wenn Sie eine Lösung [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]mithilfe von erstellen, stellen Sie sicher, dass Ihre Benutzer beim Bereitstellen der Lösung die neueste Version der Visual Studio 2010-Tools für Office-Laufzeit installiert haben. Ältere Versionen der VSTO-Laufzeit werden in Lösungsassemblys widergespiegelt, um Multifunktionsleistenanpassungen zu finden. Dieser Prozess kann zur Folge haben, dass das VSTO-Add-In langsamer geladen wird.

 Alternativ können Sie verhindern, dass jede Version der Visual Studio 2010-Laufzeit von Tools für Office Reflektion verwendet, um Multifunktionsleistenanpassungen zu identifizieren. Um diese Strategie zu `CreateRibbonExtensibility` befolgen, überschreiben Sie die Methode, und geben Sie Ribbon-Objekte explizit zurück. Wenn Ihr VSTO-Add-In keine Multifunktionsleistenanpassungen `null` enthält, kehren Sie innerhalb der Methode zurück.

 Im folgenden Beispiel wird ein Ribbon-Objekt basierend auf dem Wert eines Felds zurückgegeben.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Ausführen teurer Vorgänge in einem separaten Ausführungsthread
 Erwägen Sie, zeitintensive Aufgaben (z. B. Aufgaben mit langer Ausführungsdauer, Datenbankverbindungen oder andere Arten von Netzwerkaufrufen) in einem separaten Thread auszuführen. Weitere Informationen finden Sie [unter Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Der gesamte Code, der das Office-Objektmodell aufruft, muss im Hauptthread ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen

- [BedarfsladenvsTO-Add-Ins](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Verzögertes Laden der CLR in Office-Add-Ins](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Erstellen von VSTO-Add-ins für Office mithilfe von Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
