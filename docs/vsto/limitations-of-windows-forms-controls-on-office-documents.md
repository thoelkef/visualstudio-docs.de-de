---
title: Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumente
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 610ee5e18054b6da35a3098b851d1585c70b6bc3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863551"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumente

Es gibt einige Unterschiede zwischen Windows Forms-Steuerelemente, die Microsoft Office Word-Dokumenten oder Microsoft Office Excel-Arbeitsblätter hinzugefügt werden, und Windows Forms-Steuerelemente, die Windows Forms hinzugefügt werden. Wenn Sie z. B. Hinzufügen einer <xref:Microsoft.Office.Tools.Word.Controls.Button> steuern, wie z. B. auf ein Dokument, Eigenschaften <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, und <xref:System.Windows.Forms.Control.TabIndex> Verhalten sich nicht wie zu erwarten.

Viele dieser Unterschiede werden durch die Art, Windows Forms-Steuerelemente gehostet werden verursacht, für Dokumente. Wenn ein Dokument, ein Windows Forms-Steuerelement hinzugefügt wird die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bettet ein ActiveX-Steuerelement, das dann das Windows Forms-Steuerelement im Dokument hostet. Das Windows Forms-Steuerelement ist nicht direkt in das Dokument eingebettet.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Einschränkungen von Methoden und Eigenschaften von Windows Forms-Steuerelementen

Es gibt eine Reihe von Methoden und Eigenschaften von Windows Forms-Steuerelementen, die nicht die gleiche Weise wie für ein Dokument arbeiten würden in einem Windows Form, und es wird daher empfohlen, dass sie nicht verwendet werden. Zum Festlegen von Eigenschaften wie z. B. <xref:System.Windows.Forms.Control.Dock> und <xref:System.Windows.Forms.Control.Anchor> wirkt sich nur auf die Position des Steuerelements in Bezug auf das Dokument, anstatt das Container-ActiveX-Steuerelement. Im folgenden finden eine Liste der nicht unterstützten Methoden und Eigenschaften von Windows Forms-Steuerelementen für Word und Excel:

- Nicht unterstützte Eigenschaften der Excel-Steuerelemente:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- Nicht unterstützte Methoden und Eigenschaften des Word-Steuerelemente:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

Außerdem kann nicht festgelegt werden die <xref:System.Windows.Forms.Control.Left> oder <xref:System.Windows.Forms.Control.Top> Eigenschaft von Windows Forms-Steuerelementen, die am Text in einem Worddokument ausgerichtet sind. Windows Forms-Steuerelemente werden Textfluss in den folgenden Fällen hinzugefügt:

- Sie können programmgesteuert hinzufügen eines Steuerelements zu einem Word-Dokument und verwenden Sie eine Methode, die einen Bereich für den Speicherort angibt.

- Sie fügen Sie ein Windows Forms-Steuerelement in einem Word-Dokument zur Entwurfszeit hinzu. Sie können dies ändern, indem Sie das Steuerelement im Designer ändern.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Unterschiede in Windows Forms-Steuerelemente für Office-Dokumente

Windows Forms-Steuerelemente haben in der Regel das gleiche Verhalten für ein Office-Dokument, wie sie in einem Windows Form, aber einige Unterschiede. Die folgende Tabelle beschreibt die Unterschiede, die für Windows Forms-Steuerelemente für Office-Dokumente vorhanden sind.

|Funktionalität|Unterschied|
|-------------------|----------------|
|Steuerreihenfolge|Sie können nicht über die Steuerelemente auf einem Excel-Arbeitsblatt oder Word-Dokument Registerkarte.|
|Steuerelement-Gruppierung|Sie können keine <xref:System.Windows.Forms.GroupBox> Steuerelement andere Steuerelemente auf einem Office-Dokument enthalten. Wenn Sie mehrere Optionsfelder direkt zu einem Dokument hinzufügen, sind die Optionsfelder nicht gegenseitig. Sie können Code aus, um die Optionsfelder sich gegenseitig ausschließende stellen schreiben. Allerdings ist der bevorzugte Ansatz die Optionsfelder, ein Benutzersteuerelement hinzuzufügen, und fügen Sie dann auf das Dokument das Benutzersteuerelement hinzu. Weitere Informationen finden Sie unter dem Beispiel des Word-Steuerelemente oder Beispiel für Excel-Steuerelemente unter [Office-Entwicklungsbeispiele und exemplarische Vorgehensweisen](../vsto/office-development-samples-and-walkthroughs.md).|
|Steuerelementtyp|Eine Klasse, die von bereitgestellte Windows Forms-Steuerelemente in Dokumenten verwendete umschlossen sind die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , das Ihnen die Steuerelemente bestimmte Zusatzfunktionen auf die Excel-Arbeitsblatt oder Word-Dokument. Angenommen, Sie haben eine **Schaltfläche** in einem Excel-Arbeitsblatt zu steuern, müssen Sie den Typ angeben <xref:Microsoft.Office.Tools.Excel.Controls.Button> statt <xref:System.Windows.Forms.Button> verweisen oder Umwandeln des Objekts.|
|Steuerelement Position und Größe|Die Größe und Position des Steuerelements richtet sich nach den Eigenschaften, die Teil des Containers ActiveX-Steuerelement. Die ActiveX-Steuerelementeigenschaften werden andere Werte als die entsprechenden Eigenschaften eines Windows Forms-Steuerelements. Beim Festlegen der `Top`, `Left`, `Height`, oder `Width` Eigenschaften eines Steuerelements, gemessen verweist, anstatt Pixel.|
|Position des Steuerelements in Word-Dokumenten|Wenn Sie einem Flusslayout Steuerelemente hinzufügen, sollten Sie bedenken, die die Steuerelemente mit dem Inhalt wie die Änderungen am Inhalt eingefügt werden. Sie können das Steuerelement auf einen Absatz können nicht verankern, wenn Sie es aus ziehen die **Toolbox** daran, dass das Steuerelement zum Word-Dokument am Text ausgerichtet hinzugefügt wird. Wenn Sie eine andere Methode verwenden, um das Steuerelement, z. B. durch Doppelklicken auf das Steuerelement hinzuzufügen, wird das Steuerelement gemäß der Option "Wort" eingefügt, die Sie festgelegt haben, für das Einfügen von Bildern.<br /><br /> Sie können nicht festgelegt werden die `Left` oder `Top` Eigenschaft eines Steuerelements, das Text ausgerichtet ist.<br /><br /> Sie können keine Steuerelemente in einer Kopf- oder Fußzeile oder in einem Unterdokument platzieren.|
|Steuerelementereignisse|Wenn das Steuerelement ausgewählt ist, löst Ereignisse in der folgenden Reihenfolge aus:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Wenn das Steuerelement deaktiviert ist, löst Ereignisse in der folgenden Reihenfolge aus:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Skalierung des Steuerelements|Wenn Sie auf einen anderen als 100 % die zoomeinstellung eines Dokuments ändern, Steuerelemente sind deaktiviert, auch wenn sie angezeigt werden mit dem Dokument zu skalieren. Z. B. Wenn Sie eine Schaltfläche klicken, wenn das Dokument 130 % Zoom ist, es wird eine Meldung anzeigen, dass das Steuerelement deaktiviert wurde, bis Zoom auf 100 % festgelegt wird. Die Steuerelemente funktioniert ordnungsgemäß, wenn Sie den Zoom auf 100 % ändern.|
|Eigenschaftswerte von Steuerelementen|Obwohl die Eigenschaften der Steuerelemente auf einem Windows Form in einen ganzzahligen Wert festgelegt werden, werden sie mit einem einzelnen für Steuerelemente in einem Word-Dokument festgelegt. In Excel werden die Eigenschaftswerte von Steuerelementen auf einen Double-Wert festgelegt. Wenn die `Height` und `Width` Eigenschaft eines Steuerelements in einem Arbeitsblatt überschreitet die Größe des Arbeitsblatts oder des Bildschirms, wird der Wert abgeschnitten.|
|Größenanpassung des Steuerelements|Wenn Sie die Größe ein Steuerelements im Dokument mit einem der acht Ziehpunkte ändern, werden die Abmessungen des Steuerelements nicht in wiedergegeben der **Eigenschaften** Fenster, bis das Steuerelement wieder aktiviert wird.|
|Verhalten des Steuerelements|Steuerelemente in einem Excel-Arbeitsblatt möglicherweise unvorhersehbar reagieren, wenn das Arbeitsblattfenster aufgeteilt wird. Z. B. Zugriff auf eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> auf dem Arbeitsblatt möglicherweise nur zur Verfügung in eines der Fenster.|
|Benennung von Steuerelementen|Sie können keine reservierte Wörtern benennen-Steuerelemente. Wenn Sie hinzufügen, z. B. eine <xref:Microsoft.Office.Tools.Excel.Controls.Button> zu einem Arbeitsblatt, und ändern Sie den Namen in **System**, Fehler auftreten, wenn Sie das Projekt erstellen.|
|Programmgesteuertes Hinzufügen von Steuerelementen|Verwenden Sie nicht den Konstruktor des Steuerelements, das Dokument zur Laufzeit ein Steuerelement hinzu. Verwenden Sie stattdessen die Hilfsmethoden, die von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Beispielsweise verwenden die <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> Methode, um eine Schaltfläche in einem Arbeitsblatt hinzuzufügen. Wenn Sie möchten ein Steuerelement hinzufügen, die von den Hilfsmethoden nicht unterstützt wird, können Sie mithilfe der `AddControl` Methode. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Kopieren von Steuerelementen|Wenn Sie ein Windows Forms-Steuerelement zu kopieren und fügen Sie ihn in ein Dokument zur Laufzeit, wird ein leerer Container ActiveX-Steuerelement in das Dokument eingefügt. Das Windows Forms-Steuerelement nicht in den neuen Speicherort angezeigt, und Code-behind das ursprüngliche Steuerelement wird nicht in das ActiveX-Steuerelement-Container kopiert.|

## <a name="limitations-in-document-level-projects"></a>Einschränkungen in Projekten auf Dokumentebene

Einige Einschränkungen bei der Verwendung von Windows Forms-Steuerelemente in Dokumenten gelten nur für Projekte auf Dokumentebene.

### <a name="control-support-at-design-time"></a>Unterstützung von Steuerelementen zur Entwurfszeit

Bestimmte Windows Forms-Steuerelemente werden entfernt, von der **Toolbox** Wenn eine Excel-Arbeitsblatt oder Word-Dokument in Visual Studio-Designer geöffnet ist. Dies ist aufgrund technischer Einschränkungen oder weil die Funktionalität bereits im Word- oder Excel verfügbar sind. Excel und Word-Projekte unterstützen alle von der Windows Forms-Steuerelemente und andere Komponenten, die in angezeigt werden. die **Toolbox** Wenn das Dokument den Fokus besitzt, und Sie können auch Drittanbieter-Steuerelementen zu einem Arbeitsblatt oder Dokument hinzufügen.

> [!NOTE]
> Alle Steuerelemente werden entfernt, von der **Toolbox** Wenn ein Dokument geschützt ist. Informationen zum Dokumentschutz finden Sie unter [Dokumentschutz in Projektmappen auf Anwendungsebene](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Drittanbieter-Steuerelemente müssen die <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attributsatz auf **"true"** um in einer Office-Projektmappe verwendet werden.

Die folgenden Steuerelemente und Komponenten sind nicht verfügbar, in der **Toolbox**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Unterstützung für ältere ActiveX-Steuerelemente

Wenn Sie ein Office-Projekt auf Dokumentebene, die verwendet wird erstellen, ein vorhandenes Word-Dokument oder eine Excel-Arbeitsmappe, die ActiveX-Steuerelemente enthält, geht die Funktionalität des ActiveX-Steuerelemente nicht verloren; Es ist jedoch keine Unterstützung für das Hinzufügen von neuen ActiveX-Steuerelemente in Visual Studio-Dokumenten aus. Wenn Ihr Word-Dokument eine Schaltfläche aus enthält z. B. die **Steuerelement** Toolbox, die eine Makro Visual Basic für Applikationen (VBA) ausgeführt wird, diese Funktion bleibt weiterhin das Makro ausgeführt, nachdem das Dokument in einem Office-Projekt verwendet wurde. Allerdings empfiehlt es sich, dass Sie ActiveX-Steuerelemente und VBA-Makros zu entfernen und Ersetzen Sie sie mit Windows Forms-Steuerelementen und verwaltetem Code.

## <a name="see-also"></a>Siehe auch

- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Windows Forms-Steuerelemente in Office-Dokumente – Übersicht](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)