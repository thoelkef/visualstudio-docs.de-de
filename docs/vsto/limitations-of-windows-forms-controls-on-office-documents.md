---
title: Einschränkungen von Windows Forms-Steuerelemente in Office-Dokumente | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3180de49b1ede89e6eb5e66d786247ce2700888
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Einschränkungen für Windows Forms-Steuerelemente in Office-Dokumenten
  Es gibt einige Unterschiede zwischen Windows Forms-Steuerelemente, die Microsoft Office Word-Dokumente oder Microsoft Office Excel-Arbeitsblättern hinzugefügt werden, und Windows Forms-Steuerelemente, die in Windows Forms hinzugefügt werden. Z. B. beim Hinzufügen einer <xref:Microsoft.Office.Tools.Word.Controls.Button> -Steuerelements zu einem Dokument, Eigenschaften, z. B. <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>, und <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> nicht Verhalten sich wie zu erwarten.  
  
 Viele dieser Unterschiede werden durch die Art, Windows Forms-Steuerelemente gehostet werden Dokumente geführt. Wenn ein Dokument ein Windows Forms-Steuerelement hinzugefügt wird die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bettet ein ActiveX-Steuerelement, das dann das Windows Forms-Steuerelement im Dokument hostet. Windows Forms-Steuerelement wird nicht direkt in das Dokument eingebettet.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Einschränkungen von Methoden und Eigenschaften von Windows Forms-Steuerelementen  
 Es gibt eine Reihe von Methoden und Eigenschaften eines Windows Forms-Steuerelemente, die nicht die gleiche Weise wie für ein Dokument geeignet sind, als würden Sie in einem Windows Form, und es wird daher empfohlen, dass sie nicht verwendet werden. Angenommen, Festlegen von Eigenschaften wie z. B. `Dock` und `Anchor` wirkt sich nur auf die Position des Steuerelements in Bezug auf das Container-ActiveX-Steuerelement, anstatt das Dokument. Im folgenden finden eine Liste der nicht unterstützten Methoden und Eigenschaften von Windows Forms-Steuerelementen für Word und Excel:  
  
-   Nicht unterstützte Methoden und Eigenschaften der Excel-Steuerelemente:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Nicht unterstützte Methoden und Eigenschaften von Word-Steuerelemente:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Außerdem kann nicht festgelegt werden die `Left` oder `Top` Eigenschaft Windows Forms-Steuerelemente, die auf einem Word-Dokument Textfluss eingefügt wurden. Windows Forms-Steuerelemente werden Textfluss in den folgenden Fällen hinzugefügt:  
  
-   Sie programmgesteuert ein Word-Dokument ein Steuerelement hinzu, und verwenden Sie eine Methode, die einen Bereich für den Speicherort angibt.  
  
-   Windows Forms-Steuerelements hinzufügen zu einem Worddokument zur Entwurfszeit. Sie können dies ändern, indem Sie das Steuerelement im Designer ändern.  
  
## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Unterschiede in Windows Forms-Steuerelemente in Office-Dokumente  
 Windows Forms-Steuerelemente haben in der Regel das gleiche Verhalten für ein Office-Dokument ein, wie sie in einem Windows Form, aber einige Unterschiede. Die folgende Tabelle beschreibt die Unterschiede, die für Windows Forms-Steuerelemente für Office-Dokumente vorhanden sind.  
  
|Funktionalität|Unterschied|  
|-------------------|----------------|  
|Aktivierreihenfolge des Steuerelements|Sie können nicht über die Steuerelemente auf einem Excel-Arbeitsblatt oder Word-Dokument platziert Registerkarte.|  
|Steuerelement-Gruppierung|Sie können keine <xref:System.Windows.Forms.GroupBox> -Steuerelement andere Steuerelemente in einem Office-Dokument enthalten. Wenn Sie mehrere Optionsfelder direkt auf das Dokument hinzufügen, sind die Optionsfelder nicht gegenseitig. Sie können Code, damit die Optionsfelder sich gegenseitig ausschließende schreiben. Allerdings wird der optimalen Ansatz, um ein Benutzersteuerelement die Optionsfelder hinzu, und fügen Sie dann auf das Dokument das Benutzersteuerelement. Weitere Informationen finden Sie im Beispiel Steuerelemente in Word bzw. Excel-Steuerelemente am [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).|  
|Steuerelementtyp|Windows Forms-Steuerelemente in Dokumenten verwendet werden in einer Klasse, die von bereitgestellte eingebunden der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , durch das erhalten die Steuerelemente bestimmte zusätzliche Funktionalität zum Excel-Arbeitsblatt oder Word-Dokument. Angenommen, Sie haben eine `Button` in einem Excel-Arbeitsblatt zu steuern, achten Sie darauf, dass Sie zur Angabe als <xref:Microsoft.Office.Tools.Excel.Controls.Button> statt <xref:System.Windows.Forms.Button> verweisen oder das Objekt umwandeln.|  
|Steuerelement-Position und Größe|Die Größe und Position des Steuerelements richtet sich nach Eigenschaften, die Teil des Containers ActiveX-Steuerelement. Die ActiveX-Steuerelementeigenschaften werden andere Werte als die entsprechenden Eigenschaften eines Windows Forms-Steuerelements. Beim Festlegen der `Top`, `Left`, `Height`, oder `Width` Eigenschaften eines Steuerelements, gemessen verweist, anstatt Pixel.|  
|Position des Steuerelements in Word-Dokumenten|Wenn Sie einem Flusslayout Steuerelemente hinzugefügt haben, sollten Sie bedenken, die die Steuerelemente mit dem Inhalt wie die Änderungen am Inhalt eingefügt werden. Sie können das Steuerelement in einem Absatz verankern, beim ziehen es aus der **Toolbox** daran, dass das Steuerelement zum Word-Dokument am Text ausgerichtet hinzugefügt wird. Wenn Sie eine andere Methode verwenden, um das Steuerelement, z. B. durch Doppelklicken auf das Steuerelement hinzuzufügen, wird das Steuerelement gemäß der Option "Wort" eingefügt, die Sie festgelegt haben, für das Einfügen von Bildern.<br /><br /> Kann nicht festgelegt werden die `Left` oder `Top` Eigenschaft eines Steuerelements, das Text ausgerichtet ist.<br /><br /> Steuerelemente können nicht in einer Kopf- oder Fußzeile oder in einem Unterdokument platziert werden.|  
|Steuerelementereignisse|Wenn das Steuerelement ausgewählt ist, löst sie Ereignisse in der folgenden Reihenfolge aus:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Wenn das Steuerelement deaktiviert ist, löst sie Ereignisse in der folgenden Reihenfolge aus:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Skalierung des Steuerelements|Wenn Sie den Zoomfaktor eines Dokuments in etwas anderes als 100 % ändern, Steuerelemente, werden deaktiviert, auch wenn sie angezeigt werden mit dem Dokument zu skalieren. Z. B. Wenn Sie eine Schaltfläche klicken, wenn das Dokument am 130 % Zoom ist, es wird eine Meldung anzeigen, dass das Steuerelement deaktiviert wurde, bis Zoom auf 100 % festgelegt wird. Die Steuerelemente funktioniert ordnungsgemäß, wenn Sie den Zoom auf 100 % ändern.|  
|Eigenschaftswerte von Steuerelementen|Obwohl die Eigenschaften der Steuerelemente in einem Windows Form in einen ganzzahligen Wert festgelegt sind, werden sie auf ein einzelnes für Steuerelemente in einem Word-Dokument festgelegt. In Excel werden die Eigenschaftswerte von Steuerelementen in einen Double festgelegt. Wenn die `Height` und `Width` Eigenschaft eines Steuerelements in einem Arbeitsblatt überschreitet die Größe des Arbeitsblatts oder des Bildschirms, wird der Wert abgeschnitten.|  
|Größenanpassung des Steuerelements|Wenn die Größe eines Steuerelements im Dokument mit einer der acht Ziehpunkte werden die neuen Steuerelement Dimensionen nicht wiedergegeben der **Eigenschaften** Fenster bis zu das Steuerelement wieder aktiviert wird.|  
|Verhalten des Steuerelements|Steuerelemente in einem Excel-Arbeitsblatt möglicherweise unvorhersehbar reagieren, wenn das Arbeitsblattfenster aufgeteilt wird. Z. B. der Zugriff auf eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> im Arbeitsblatt möglicherweise nur zur Verfügung in eines der Fenster.|  
|Benennung von Steuerelementen|Sie können keine reservierte Wörter für Name-Steuerelemente. Angenommen, Sie fügen eine <xref:Microsoft.Office.Tools.Excel.Controls.Button> zu einem Arbeitsblatt und ändern Sie den Namen in **System**, Fehler auftreten, wenn Sie das Projekt erstellen.|  
|Programmgesteuertes Hinzufügen von Steuerelementen|Verwenden Sie zum Hinzufügen eines Steuerelements zu Ihrem Dokument zur Laufzeit nicht Konstruktor des Steuerelements. Verwenden Sie stattdessen die Hilfsmethoden, die von der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Verwenden Sie z. B. die <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> Methode, um einem Arbeitsblatt eine Schaltfläche hinzuzufügen. Wenn Sie möchten ein Steuerelement hinzufügen, die von den Hilfsmethoden nicht unterstützt wird, können Sie die AddControl-Methode verwenden. Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Kopieren der Steuerelemente|Wenn Sie ein Windows Forms-Steuerelement kopieren und fügen Sie ihn in ein Dokument zur Laufzeit, wird ein leerer Container ActiveX-Steuerelement in das Dokument eingefügt. Windows Forms-Steuerelement nicht in den neuen Speicherort angezeigt, und Code hinter dem ursprünglichen Steuerelement nicht in der ActiveX-Steuerelement-Container kopiert wird.|  
  
## <a name="limitations-in-document-level-projects"></a>Beschränkungen in Projekten auf Dokumentebene  
 Einige Einschränkungen bei der Verwendung von Windows Forms-Steuerelemente in Dokumenten gelten nur für Projekte auf Dokumentebene.  
  
### <a name="control-support-at-design-time"></a>Unterstützung von Steuerelementen zur Entwurfszeit  
 Bestimmte Windows Forms-Steuerelemente werden entfernt, von der **Toolbox** Wenn ein Excel-Arbeitsblatt oder Word-Dokument in der Visual Studio-Designer geöffnet ist. Dies ist aufgrund von technischen Einschränkungen oder weil die Funktionalität bereits im Word- oder Excel verfügbar sind. Excel und Word-Projekte unterstützen alle Windows Forms-Steuerelemente und andere Komponenten, die in der **Toolbox** Wenn das Dokument den Fokus hat, und Sie können auch Drittanbieter-Steuerelementen zu einem Arbeitsblatt oder Dokument hinzufügen.  
  
> [!NOTE]  
>  Entfernt alle Steuerelemente aus der **Toolbox** , ein Dokument geschützt ist. Informationen über Dokumentschutz finden Sie unter [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Drittanbieter-Steuerelemente müssen die <xref:System.Runtime.InteropServices.ComVisibleAttribute> -Attributsatz zur **"true"** um in einer Office-Projektmappe verwendet werden.  
  
 Die folgenden Steuerelemente und Komponenten sind nicht verfügbar in der **Toolbox**:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### <a name="support-for-legacy-activex-controls"></a>Unterstützung für ältere ActiveX-Steuerelemente  
 Wenn Sie ein Office-Projekt auf Dokumentebene, die verwendet wird erstellen, ein vorhandenes Word-Dokument oder eine Excel-Arbeitsmappe, die ActiveX-Steuerelemente enthält, geht die Funktionalität des ActiveX-Steuerelemente nicht verloren; Es ist jedoch keine Unterstützung für das Hinzufügen von neuen ActiveX-Steuerelemente in Visual Studio-Dokumenten aus. Beispielsweise verfügt das Word-Dokument eine Schaltfläche aus der **Steuerelement** Toolbox, die eine Makro Visual Basic für Applikationen (VBA) ausgeführt wird, ist sie weiterhin das Makro ausführen, nachdem das Dokument in einem Office-Projekt verwendet wurde. Allerdings wird empfohlen, dass Sie ActiveX-Steuerelemente und VBA-Makros zu entfernen und Sie sie mit Windows Forms-Steuerelemente ersetzen und verwaltetem Code.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Windows Forms-Steuerelemente in Office-Dokumente (Übersicht)](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Vorgehensweise: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  