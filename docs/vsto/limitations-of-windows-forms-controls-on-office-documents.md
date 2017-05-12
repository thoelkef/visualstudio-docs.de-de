---
title: "Einschr&#228;nkungen f&#252;r Windows&#160;Forms-Steuerelemente in Office-Dokumenten"
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
  - "ActiveX-Steuerelemente [Office-Entwicklung in Visual Studio]"
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Windows Forms-Steuerelemente"
  - "Toolbox [Office-Entwicklung in Visual Studio], Nicht unterstützte Steuerelemente"
  - "Benutzersteuerelemente [Office-Entwicklung in Visual Studio], Gruppieren von Steuerelementen"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], ActiveX-Legacy"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Einschränkungen"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Toolbox"
  - "Windows Forms-Steuerelemente [Office-Entwicklung in Visual Studio], Nicht unterstützte Eigenschaften und Methoden"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Einschr&#228;nkungen f&#252;r Windows&#160;Forms-Steuerelemente in Office-Dokumenten
  Es bestehen einige Unterschiede zwischen Windows Forms\-Steuerelementen, die zu Microsoft Office Word\-Dokumenten oder Microsoft Office Excel\-Arbeitsblättern hinzugefügt werden, und Windows Forms\-Steuerelementen, die zu Windows Forms hinzugefügt werden.  Wenn Sie beispielsweise einem Dokument ein <xref:Microsoft.Office.Tools.Word.Controls.Button>\-Steuerelement hinzufügen, verhalten sich Eigenschaften wie <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A> und <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> nicht wie erwartet.  
  
 Viele dieser Unterschiede werden durch die Art und Weise verursacht, mit der Windows Forms\-Steuerelemente in Dokumenten gehostet werden.  Beim Hinzufügen eines Windows Forms\-Steuerelements zu einem Dokument wird von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ein ActiveX\-Steuerelement eingebettet, das anschließend das Windows Forms\-Steuerelement im Dokument hostet.  Das Windows Forms\-Steuerelement wird nicht direkt ins Dokument eingebettet.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Beschränkungen der Methoden und Eigenschaftswerte von Windows Forms\-Steuerelementen  
 Es gibt eine Reihe von Methoden und Eigenschaften von Windows Forms\-Steuerelementen, die bei einem Dokument nicht wie bei einem Windows Form funktionieren und daher nicht verwendet werden sollten.  Das Festlegen von Eigenschaften wie `Dock` und `Anchor` wirkt sich nur auf die Position des Steuerelements in Bezug auf das Container\-ActiveX\-Steuerelement aus, nicht auf die Position in Bezug auf das Dokument.  Die folgende Liste enthält nicht unterstützte Methoden und Eigenschaften von Windows Forms\-Steuerelementen für Word und Excel:  
  
-   Nicht unterstützte Methoden und Eigenschaften von Excel\-Steuerelementen:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Nicht unterstützte Methoden und Eigenschaften von Word\-Steuerelementen:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Auch die Eigenschaften `Left` oder `Top` von Windows Forms\-Steuerelementen, die am Text eines Word\-Dokuments ausgerichtet wurden, können nicht festgelegt werden.  Windows Forms\-Steuerelemente werden in den folgenden Fällen am Text ausgerichtet:  
  
-   Sie können einem Word\-Dokument ein Steuerelement programmgesteuert hinzufügen und eine Methode verwenden, die den Bereich für die Position angibt.  
  
-   Sie fügen einem Word\-Dokument zur Entwurfszeit ein Windows Forms\-Steuerelement hinzu.  Sie können dies ändern, indem Sie das Steuerelement im Designer ändern.  
  
## Unterschiede bei Windows Forms\-Steuerelementen in Office\-Dokumenten  
 In den meisten Fällen verhalten sich Windows Forms\-Steuerelemente in einem Office\-Dokument genauso wie in einem Windows\-Formular, es bestehen jedoch einige Unterschiede.  In der folgenden Tabelle werden die Unterschiede beschrieben, die für Windows Forms\-Steuerelemente in Office\-Dokumenten bestehen.  
  
|Funktionalität|Difference|  
|--------------------|----------------|  
|Steuerelement\-Aktivierreihenfolge|Sie können Steuerelemente, die auf einem Excel\-Arbeitsblatt oder einem Word\-Dokument platziert sind, nicht per TAB\-TASTE aktivieren.|  
|Steuerelementgruppierung|Sie können ein <xref:System.Windows.Forms.GroupBox>\-Steuerelement nicht als Container für andere Steuerelemente in einem Office\-Dokument verwenden.  Wenn Sie dem Dokument mehrere Optionsfelder direkt hinzufügen, schließen sich die Optionsfelder nicht gegenseitig aus.  Um zu gewährleisten, dass sich die Optionsfelder gegenseitig ausschließen, können Sie Code schreiben. Die bevorzugte Vorgehensweise besteht jedoch darin, einem Benutzersteuerelement Optionsfelder hinzuzufügen und dieses Benutzersteuerelement dann dem Dokument hinzuzufügen.  Weitere Informationen finden Sie im Beispiel für Word\-Steuerelemente bzw. Excel\-Steuerelemente unter [Beispiele und exemplarische Vorgehensweisen für die Programmierung mit Office](../vsto/office-development-samples-and-walkthroughs.md).|  
|Steuerelementtyp|In Dokumenten verwendete Windows Forms\-Steuerelemente werden in einer Klasse umschlossen, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellt wird. Diese Klasse verleiht den Steuerelementen eine für die Excel\-Arbeitsmappe oder das Word\-Dokument spezifische Funktionalität.  Bei einem `Button`\-Steuerelement in einer Excel\-Arbeitsmappe sollten Sie z. B. den Typ als <xref:Microsoft.Office.Tools.Excel.Controls.Button> und nicht als <xref:System.Windows.Forms.Button> angeben, wenn Sie auf das Objekt verweisen oder es umwandeln.|  
|Position und Größe von Steuerelementen|Die Größe und Position eines Steuerelements wird durch Eigenschaften bestimmt, die Teil des Container\-ActiveX\-Steuerelements sind.  Die ActiveX\-Steuerelementeigenschaften benötigen andere Werte als die entsprechenden Eigenschaften eines Windows Forms\-Steuerelements.  Wenn Sie die Eigenschaften `Top`, `Left`, `Height` oder `Width` eines Steuerelements festlegen, wird dies in Punkten und nicht in Pixel gemessen.|  
|Steuerelementposition in Word\-Dokumenten|Wenn Sie Steuerelemente zu einem flussbasierten Layout hinzufügen, sollten Sie beachten, dass die Steuerelemente mit dem Inhalt mitfließen, wenn dieser sich ändert.  Sie können das Steuerelement nicht an einem Absatz verankern, wenn Sie es aus der **Toolbox** ziehen. Der Grund dafür ist, dass das Steuerelement am Text im Word\-Dokument ausgerichtet wird.  Wenn Sie zum Hinzufügen des Steuerelements eine andere Methode \(z. B. Doppelklick auf das Steuerelement\) verwenden, wird das Steuerelement entsprechend der Word\-Option eingefügt, die für das Einfügen von Grafiken festgelegt ist.<br /><br /> Sie können die `Left`\-Eigenschaft und die `Top`\-Eigenschaft eines Steuerelements, das am Text ausgerichtet wurde, nicht festlegen.<br /><br /> Sie können keine Steuerelemente in einem Header, einer Fußzeile oder innerhalb eines Unterdokuments einfügen.|  
|Steuerelementereignisse|Die Auswahl des Steuerelements löst Ereignisse in folgender Reihenfolge aus:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Das Aufheben der Auswahl des Steuerelements löst Ereignisse in folgender Reihenfolge aus:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Steuerelementskalierung|Wenn Sie die Zoomeinstellung eines Dokuments auf einen anderen Wert als 100 Prozent festlegen, werden Steuerelemente deaktiviert, obwohl sie scheinbar mit dem Dokument skaliert werden.  Wenn Sie beispielsweise auf eine Schaltfläche klicken, während das Dokument eine Zoomeinstellung von 130 % hat, wird eine Meldung angezeigt. Daraus geht hervor, dass das Steuerelement so lange deaktiviert ist, bis die Zoomeinstellung wieder auf 100 % festgelegt wird.  Die Steuerelemente funktionieren ordnungsgemäß, wenn Sie die Zoomeinstellung wieder auf 100 % ändern.|  
|Eigenschaftswerte von Steuerelementen|Die Eigenschaften von Steuerelementen in einem Windows Form haben ganzzahlige Werte, während diese Eigenschaften in einem Word\-Dokument auf Werte mit einfacher Genauigkeit festgelegt werden.  In Excel werden die Eigenschaften von Steuerelementen auf Werte mit doppelter Genauigkeit festgelegt.  Wenn die `Height`\-Eigenschaft oder die `Width`\-Eigenschaft eines Steuerelements in einem Arbeitsblatt die Größe des Arbeitsblattes oder des Bildschirms überschreitet, wird der Wert entsprechend vermindert.|  
|Größenänderungen bei Steuerelementen|Wenn Sie die Größe eines Steuerelements im Dokument mit einem der acht Ziehpunkte ändern, werden die neuen Steuerelementabmessungen erst bei einem erneuten Auswählen des Steuerelements im **Eigenschaftenfenster** aktualisiert.|  
|Steuerelementverhalten|Steuerelemente in einem Excel\-Arbeitsblatt können möglicherweise unvorhersehbar reagieren, wenn das Fenster mit dem Arbeitsblatt geteilt wird.  So kann z. B. der Zugriff auf eine <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> im Arbeitsblatt nur in einem der Fenster möglich sein.|  
|Benennung von Steuerelementen|Für die Benennung von Steuerelementen können Sie keine reservierten Wörter verwenden.  Wenn Sie beispielsweise einem Arbeitsblatt einen <xref:Microsoft.Office.Tools.Excel.Controls.Button> hinzufügen und den Namen auf **System** ändern, gibt es beim Erstellen des Projekts Fehler.|  
|Programmgesteuertes Hinzufügen von Steuerelementen|Fügen Sie Steuerelemente nicht mithilfe des Konstruktors des Steuerelements einem Dokument zur Laufzeit hinzu.  Verwenden Sie stattdessen die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellten Hilfsmethoden.  Verwenden Sie z. B. die <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>\-Methode, um einem Arbeitsblatt eine Schaltfläche hinzuzufügen.  Wenn Sie ein Steuerelement hinzufügen möchten, dass von den Hilfsmethoden nicht unterstützt wird, können Sie die AddControl\-Methode verwenden.  Weitere Informationen finden Sie unter [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Kopieren von Steuerelementen|Wenn Sie ein Windows Forms\-Steuerelement kopieren und zur Laufzeit in ein Dokument einfügen, wird ein leeres Container\-ActiveX\-Steuerelement in das Dokument eingefügt.  Das Windows Forms\-Steuerelement wird nicht an der neuen Position angezeigt, und der Code, der im ursprünglichen Steuerelement hinterlegt ist, wird nicht in das Container\-ActiveX\-Steuerelement kopiert.|  
  
## Einschränkungen bei Projekten auf Dokumentebene  
 Einige Einschränkungen der Verwendung von Windows Forms\-Steuerelementen in Dokumenten gelten nur für Projekte auf Dokumentebene.  
  
### Unterstützung von Steuerelementen zur Entwurfszeit  
 Bestimmte Windows Forms\-Steuerelemente werden aus der **Toolbox** entfernt, wenn im Visual Studio\-Designer ein Excel\-Arbeitsblatt oder ein Word\-Dokument geöffnet ist.  Der Grund können technische Einschränkungen oder die Tatsache sein, dass die Funktionalität bereits in Word oder Excel verfügbar ist.  Excel\- und Word\-Projekte unterstützen alle Windows Forms\-Steuerelemente und weitere Komponenten, die in der **Toolbox** angezeigt werden, wenn das Dokument den Fokus hat, und ermöglichen außerdem das Hinzufügen von Drittanbieter\-Steuerelementen zu Arbeitsblättern oder Dokumenten.  
  
> [!NOTE]  
>  Bei einem geschützten Dokument werden alle Steuerelemente aus der **Toolbox** entfernt.  Informationen zum Dokumentschutz finden Sie unter [Dokumentschutz in Projektmappen auf Dokumentebene](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Das <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut von Drittanbieter\-Steuerelementen muss auf **true** festgelegt sein, damit diese in einer Office\-Lösung verwendet werden können.  
  
 Die folgenden Steuerelemente und Komponenten sind in der **Toolbox** nicht verfügbar:  
  
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
  
### Unterstützung für ältere ActiveX\-Steuerelemente  
 Wenn Sie ein Office\-Projekt auf Dokumentebene erstellen, das ein vorhandenes Word\-Dokument oder eine Excel\-Arbeitsmappe mit ActiveX\-Steuerelementen verwendet, geht die Funktionalität dieser ActiveX\-Steuerelemente nicht verloren. Das Hinzufügen neuer ActiveX\-Steuerelemente von Visual Studio aus wird jedoch nicht unterstützt.  Wenn das Word\-Dokument z. B. eine Schaltfläche aus der **Steuerelement**\-Toolbox enthält, die ein VBA\-\(Visual Basic for Applications\)\-Makro ausführt, wird das Makro auch nach der Verwendung des Dokuments in einem Office\-Projekt weiterhin ausgeführt.  Es wird dennoch empfohlen, ActiveX\-Steuerelemente und VBA\-Makros zu entfernen und durch Windows Forms\-Steuerelemente und verwalteten Code zu ersetzen.  
  
## Siehe auch  
 [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)   
 [Übersicht über Windows Forms-Steuerelemente in Office-Dokumenten](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Hinzufügen von Steuerelementen zu Office-Dokumenten zur Laufzeit](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Gewusst wie: Hinzufügen von Windows Forms-Steuerelementen zu Office-Dokumenten](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  