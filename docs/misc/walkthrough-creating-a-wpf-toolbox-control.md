---
title: "Exemplarische Vorgehensweise: Erstellen eines WPF-Toolbox-Steuerelements | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolbox"
  - "WPF"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Exemplarische Vorgehensweise: Erstellen eines WPF-Toolbox-Steuerelements
Mit der Vorlage „WPF\-Toolbox\-Steuerelement“, die in Visual Studio SDK enthalten ist, können Sie die WPF\-Steuerelemente \(Windows Presentation Foundation\) erstellen, die beim Installieren der Erweiterung automatisch zur **Toolbox** hinzugefügt werden. Diese exemplarische Vorgehensweise veranschaulicht, wie Sie die Vorlage verwenden, um ein Zähler\-Steuerelement zu erstellen, das Sie an andere Benutzer verteilen können.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Suchen der Vorlage „WPF\-Toolbox\-Steuerelement“ in Visual Studio  
 Die Vorlage „WPF\-Toolbox\-Steuerelement“ ist an den nachfolgenden Speicherorten im Dialogfeld **Neues Projekt** unter **Installierte Vorlagen** verfügbar:  
  
-   **Visual Basic**, **Erweiterbarkeit**. Die Sprache des Projekts ist Visual Basic.  
  
-   **Visual C\#**, **Erweiterbarkeit**. Die Sprache des Projekts ist C\#.  
  
## Erstellen eines WPF\-Toolbox\-Steuerelement\-Projekts  
 Die Vorlage „WPF\-Toolbox\-Steuerelement“ erstellt ein nicht definiertes Benutzersteuerelement und enthält alle erforderlichen Funktionen, um das Steuerelement zur **Toolbox** hinzufügen.  
  
#### So erstellen Sie das Projekt  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **Installierte Vorlagen** auf den Knoten für Ihre bevorzugte Programmiersprache, und wählen Sie dann **Erweiterbarkeit** aus. Wählen Sie in der Liste der Projekttypen **WPF\-Toolbox\-Steuerelement** aus.  
  
3.  Geben Sie im Feld **Name** den Namen für das Projekt ein. \(In dieser exemplarischen Vorgehensweise wird der Name `Counter` verwendet.\) Klicken Sie auf **OK**.  
  
     Dadurch wird eine Projektmappe erstellt, die ein Benutzersteuerelement, ein Attribut zum Platzieren des Steuerelements in die **Toolbox** und ein VSIX\-Manifest für die Bereitstellung enthält. Mit dem Feld **Name** wird der Name der Projektmappe und der Name des Namespace festgelegt, aber nicht der Name des Steuerelements, wie er in der **Toolbox** angezeigt wird. Diesen legen Sie später in der exemplarischen Vorgehensweise fest.  
  
### Erstellen einer Benutzeroberfläche für das Steuerelement  
 Das `Counter`\-Steuerelement erfordert drei untergeordnete Steuerelemente: zwei <xref:System.Windows.Controls.Label>\-Steuerelemente zum Anzeigen des Texts und der aktuellen Anzahl an sowie ein <xref:System.Windows.Controls.Button>\-Steuerelement, um die Anzahl auf 0 zurückzusetzen. Es sind keine weiteren untergeordneten Steuerelemente erforderlich, da der Zählerwert von den Hostanwendungen programmgesteuert erhöht wird.  
  
##### So erstellen Sie die Benutzeroberfläche  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf die Datei „ToolboxControl.cs“, um sie im Designer zu öffnen.  
  
     Der Designer zeigt ein <xref:System.Windows.Controls.Grid>\-Steuerelement an, das ein <xref:System.Windows.Controls.Button>\-Steuerelement enthält.  
  
2.  Wählen Sie das <xref:System.Windows.Controls.Grid>\-Steuerelement aus, und klicken Sie dann auf die blauen Leisten, die am oberen und linken Rand des Rasters angezeigt werden, um es in zwei Zeilen und zwei Spalten zu unterteilen.  
  
3.  Ziehen Sie ein <xref:System.Windows.Controls.Label>\-Steuerelement aus der **Toolbox** in jede Zelle in der obersten Zeile des Rasters.  
  
     An diesem Punkt könnten Sie das Layout des Steuerelements festlegen, indem Sie die Elemente im Raster anordnen. Stattdessen können Sie die Extensible Application Markup Language \(XAML\) auch direkt bearbeiten, sodass das Steuerelement dynamisch an den Text angepasst wird.  
  
4.  Legen Sie im Bereich **XAML** die Höhe der `RowDefinition`\-Elemente und die Breite der `ColumnDefinition`\-Elemente auf `"auto"` fest.  
  
5.  Bearbeiten Sie das Markup für die Schaltfläche und die zwei Bezeichnungen wie im folgenden Beispiel dargestellt.  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     Die Attribute `Grid.Row` und `Grid.Column` legen die Position der Elemente im Raster fest. Das `Grid.ColumnSpan`\-Attribut auf der Schaltfläche ermöglicht, dass die Größe der ersten Spalte unabhängig von der Breite der Schaltfläche geändert werden kann.  
  
     Die `Content`\-Attribute der Bezeichnungen verwenden eine `{Binding}`\-Syntax zum Binden an Eigenschaften, die Sie später in dieser exemplarischen Vorgehensweise definieren.  
  
### Codieren des Benutzersteuerelements  
 Das `Counter`\-Steuerelement macht folgende Elemente verfügbar: eine Methode zum Erhöhen des Zählerwerts, ein Ereignis, das immer dann ausgelöst wird, wenn der Zählerwert erhöht wird, eine `Reset`\-Schaltfläche sowie drei Eigenschaften, mit denen die aktuelle Anzahl und der Anzeigetext gespeichert werden bzw. festgelegt wird, ob die `Reset`\-Schaltfläche ein\- oder ausgeblendet wird. Das `ProvideTolboxControl`\-Attribut bestimmt, an welcher Stelle in der **Toolbox** das `Counter`\-Steuerelement angezeigt wird.  
  
 Sie könnten dieses Steuerelement auf die gleiche Weise wie ein Windows Forms\-Steuerelement schreiben, d. h. mithilfe von Ereignishandlern und öffentlichen Methoden, um den Inhalt der Bezeichnungen festzulegen. In WPF können Sie jedoch einen Datenkontext für das Steuerelement festlegen, sodass Sie Attribute von XAML\-Elementen direkt an die Eigenschaften im Code binden können. Dieses Modell bietet auch eine Abstraktionsebene, um die Kernfunktionen von der Benutzeroberfläche \(UI\) des Steuerelements zu trennen.  
  
 Diese exemplarische Vorgehensweise veranschaulicht, wie Sie eine Datenmodellklasse erstellen und anschließend den Datenkontext des Steuerelements an das Datenmodell binden.  
  
##### So erstellen Sie ein Datenmodell  
  
1.  Doppelklicken Sie auf die Schaltfläche, um das Codefenster zu öffnen.  
  
2.  Fügen Sie am Anfang der Datei eine `using`\-Direktive für den <xref:System.ComponentModel>\-Namespace hinzu.  
  
3.  Erstellen Sie nach der generierten Klasse eine öffentliche Klasse, um den Datenkontext zu definieren.  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     Diese Klasse implementiert die <xref:System.ComponentModel.INotifyPropertyChanged>\-Schnittstelle, die den XAML\-Elementen das Binden an definierte Eigenschaften ermöglicht.  
  
4.  Klicken Sie mit der rechten Maustaste auf die <xref:System.ComponentModel.INotifyPropertyChanged>\-Schnittstellendeklaration, klicken Sie auf **Schnittstelle implementieren**, und klicken Sie dann erneut auf **Schnittstelle implementieren**.  
  
     Visual Studio deklariert ein `PropertyChanged`\-Ereignis.  
  
5.  Erstellen Sie nach der Ereignisdeklaration die folgende private Methode zum Auslösen des Ereignisses.  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  Erstellen Sie die folgenden privaten Felder und die öffentlichen Eigenschaften, die die Werte der beiden Bezeichnungen im Steuerelement enthalten sollen.  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     Das Auslösen des `PropertyChanged`\-Ereignisses bewirkt, dass die XAML\-Bindung den Inhalt der gebundenen Steuerelemente aktualisiert. Durch das Festlegen der Eigenschaften als `public` werden sie für den Designer verfügbar gemacht, aber nicht für andere Programme, die nicht an diesen Datenkontext gebunden sind.  
  
 Nachdem Sie das Datenmodell erstellt haben, können Sie nun die Code\-Behind\-Funktionalität des Steuerelements implementieren.  
  
##### So implementieren Sie das Steuerelement  
  
1.  Klicken Sie in der Definition der partiellen Klasse, die das Steuerelement implementiert, mit der rechten Maustaste auf den Klassennamen, klicken Sie auf **Umgestalten**, klicken Sie auf **Umbenennen**, und ändern Sie dann den Namen der Klasse in `Counter`. Dies ist der Name, der bei Installation der Erweiterung in der **Toolbox** angezeigt wird.  
  
2.  Ändern Sie direkt oberhalb der Klassendefinition in der `ProvideToolboxControl`\-Attributdeklaration den Wert des ersten Parameters von `"Counter"` in `"General"`. Dadurch wird der Name der Elementgruppe festgelegt, die das Steuerelement in der **Toolbox** hostet.  
  
     Das folgende Beispiel zeigt das `ProvideToolboxControl`\-Attribut und die angepasste Klassendefinition.  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  Erstellen Sie ein privates Feld für den Datenkontext für das Steuerelement, und weisen Sie dann den Datenkontext im Konstruktor der `MyDataModel`\-Klasse zu, wie im folgenden Beispiel gezeigt.  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  Erstellen Sie die folgenden öffentlichen Eigenschaften zum Spiegeln der `Text`\- und `Count`\-Eigenschaften aus den Datenkontext.  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     Diese Eigenschaften machen den Inhalt aus dem Datenkontext für jede Anwendung verfügbar, die das Steuerelement enthält.  
  
5.  Erstellen Sie die folgende öffentliche Methode, um den Zählerwert zu erhöhen, und ein Ereignis, um die Hostanwendung zu benachrichtigen.  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  Implementieren Sie den Klickhandler für die `Reset`\-Schaltfläche wie folgt.  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  Fügen Sie folgende öffentliche Eigenschaft zum Anzeigen oder Ausblenden der `Reset`\-Schaltfläche hinzu.  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## Testen des Steuerelements  
 Zum Testen eines **Toolbox**\-Steuerelements testen Sie es zunächst in der Entwicklungsumgebung und anschließend in einer Hostanwendung.  
  
#### So testen Sie das Steuerelement  
  
1.  Drücken Sie F5.  
  
     Dadurch wird das Projekt erstellt und eine zweite Instanz von Visual Studio geöffnet, in der das Steuerelement installiert ist.  
  
2.  Erstellen Sie in der neuen Instanz von Visual Studio ein WPF\-Anwendungsprojekt.  
  
3.  Doppelklicken Sie im **Projektmappen\-Explorer** auf die Datei "MainWindow.xaml", um sie im Designer zu öffnen.  
  
4.  Ziehen Sie ein **Zähler**\-Steuerelement aus dem Abschnitt **Allgemein** der **Toolbox** in Ihr Formular, und markieren Sie es.  
  
     Die Eigenschaften `Text` und `ShowReset` sollten zusammen mit den anderen von <xref:System.Windows.Controls.UserControl> geerbten Eigenschaften im Fenster **Eigenschaften** angezeigt werden. Die `Count`\-Eigenschaft sollte nicht angezeigt werden, da sie schreibgeschützt ist.  
  
5.  Ändern Sie den Wert der `Text`\-Eigenschaft.  
  
     Der Bezeichnungstext, der im Designer angezeigt wird, sollte sich ändern.  
  
6.  Legen Sie die `ShowReset`\-Eigenschaft auf `Hidden` fest, und ändern Sie sie anschließend wieder in `Visible`.  
  
     Die `Reset`\-Schaltfläche im Steuerelement sollte verschwinden und dann erneut angezeigt werden.  
  
7.  Ziehen Sie ein <xref:System.Windows.Controls.Button>\-Steuerelement auf das Formular, legen Sie sein `Content```\-Attribut auf `Test` fest, und doppelklicken Sie dann auf die Schaltfläche, um den Klickhandler in der Codeansicht zu öffnen.  
  
8.  Implementieren Sie den Klickhandler, um die `Increment`\-Methode des Steuerelements aufzurufen.  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. Geben Sie nach dem Aufruf von `InitializeComponent` in der Konstruktorfunktion `counter1.Implemented +=` ein, und drücken Sie dann zweimal die TAB\-Taste, um einen Handler für das `Counter.Incremented`\-Ereignis zu generieren.  
  
10. Implementieren Sie den neuen Handler, wie im folgenden Beispiel gezeigt.  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. Drücken Sie F5.  
  
     Die WPF\-Anwendung sollte geöffnet werden.  
  
12. Klicken Sie auf **Test**.  
  
     Der Zählerwert sollte erhöht und die Schaltfläche leicht abgeblendet werden.  
  
13. Klicken Sie vier weitere Male auf **Test**.  
  
     Der Zählerwert sollte erhöht und die Schaltfläche weiter abgeblendet werden, bis sie ganz verschwunden ist. Wenn Sie weiter an die Stelle klicken, an der sich die Schaltfläche befand, sollte der Zählerwert weiterhin erhöht werden.  
  
14. Klicken Sie auf **Zurücksetzen**.  
  
     Der Zähler sollte auf **0** zurückgesetzt werden.  
  
## Nächste Schritte  
 Beim Erstellen eines **Toolbox**\-Steuerelements erstellt Visual Studio eine Datei namens *Projektname*.vsix im Ordner „\\bin\\debug\\“ des Projekts. Sie können das Steuerelement bereitstellen, indem Sie die VSIX\-Datei in ein Netzwerk oder auf eine Website hochladen. Wenn ein Benutzer die VSIX\-Datei öffnet, wird das Steuerelement installiert und zur **Toolbox** von Visual Studio hinzugefügt. Alternativ können Sie die VSIX\-Datei auf die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847)\-Website hochladen, damit Benutzer sie im **Erweiterungs\-Manager** finden können.  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Erstellen ein Windows Forms\-Toolbox\-Steuerelement](../extensibility/creating-a-windows-forms-toolbox-control.md)   
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Arbeiten mit Steuerelementen im WPF\-Designer.](http://msdn.microsoft.com/de-de/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [Übersicht über das Erstellen von Steuerelementen](../Topic/Control%20Authoring%20Overview.md)