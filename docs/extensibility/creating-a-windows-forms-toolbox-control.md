---
title: Erstellen einer Windows Forms-Toolbox-Steuerelement | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 770963e06655c0d4da2946fa7981fd1e4496b7f0
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-windows-forms-toolbox-control"></a>Erstellen ein Windows Forms-Toolbox-Steuerelement
Die Toolbox-Steuerelement von Windows Forms-Elementvorlage, die in der Visual Studio Extensibility Tools (Visual Studio-SDK) enthalten ist können Sie ein Steuerelement zu erstellen, das automatisch hinzugefügt wird, die **Toolbox** Wenn die Erweiterung installiert wird. In diesem Thema zeigt, wie die Vorlage verwenden, um einen einfachen Zähler-Steuerelement zu erstellen, die Sie an andere Benutzer verteilen können.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installation von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Erstellen ein Windows Forms-Toolbox-Steuerelement  
 Die Toolbox-Steuerelement von Windows Forms-Vorlage eine nicht definierte Benutzersteuerelement erstellt und enthält alle Funktionen, die erforderlich ist, um das Steuerelement hinzufügen der **Toolbox**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Erstellen Sie eine Erweiterung mit einer Toolbox-Steuerelement in Windows Forms  
  
1.  Erstellen Sie ein VSIX-Projekt namens `MyWinFormsControl`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, eine **Toolbox-Steuerelement von Windows Forms** Elementvorlage mit dem Namen `Counter`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **Toolbox-Steuerelement von Windows Forms**  
  
3.  Dies fügt ein Benutzersteuerelement, eine `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>an das Steuerelement in der **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** Posten im VSIX-Manifest für die Bereitstellung.</xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>  
  
### <a name="building-a-user-interface-for-the-control"></a>Erstellen einer Benutzeroberfläche für das Steuerelement  
 Die `Counter` Steuerelement erfordert zwei untergeordneten Steuerelementen: eine <xref:System.Windows.Forms.Label>aktuelle Anzahl die anzuzeigenden und <xref:System.Windows.Forms.Button>die Anzahl auf 0 zurückgesetzt.</xref:System.Windows.Forms.Button> </xref:System.Windows.Forms.Label> Ohne weitere untergeordnete Steuerelemente sind erforderlich, da der Aufrufer der Zähler programmgesteuert inkrementiert werden.  
  
##### <a name="to-build-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf Counter.cs, um sie im Designer zu öffnen.  
  
2.  Entfernen Sie die "klicken Sie hier!" **Schaltfläche** , ist standardmäßig enthalten, wenn Sie die Toolbox-Steuerelement von Windows Forms-Elementvorlage hinzuzufügen.  
  
3.  Aus der **Toolbox**, ziehen Sie eine `Label` Steuerelement und dann ein `Button` Steuerelement darunter auf die Entwurfsoberfläche.  
  
4.  Größe des gesamten Benutzersteuerelements auf 150, 50, 50 Pixel und zum Ändern der Größe der Schaltfläche-Steuerelement 20 Pixel.  
  
5.  In der **Eigenschaften** legen die folgenden Werte für die Steuerelemente auf der Entwurfsoberfläche angezeigt.  
  
    |Steuerelement|Eigenschaft|Wert|  
    |-------------|--------------|-----------|  
    |`Label1`|**Text**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**Text**|Zurücksetzen|  
  
### <a name="coding-the-user-control"></a>Codieren des Benutzersteuerelements  
 Das `Counter` -Steuerelement macht folgende Elemente verfügbar: eine Methode zum Erhöhen des Zählerwerts, ein Ereignis, das immer dann ausgelöst wird, wenn der Zählerwert erhöht wird, eine `Reset` -Schaltfläche sowie drei Eigenschaften, mit denen die aktuelle Anzahl und der Anzeigetext gespeichert werden bzw. festgelegt wird, ob die `Reset` -Schaltfläche ein- oder ausgeblendet wird. Die `ProvideToolboxControl` Attribut bestimmt, an welcher Stelle der **Toolbox** der `Counter` Steuerelement angezeigt wird.  
  
##### <a name="to-code-the-user-control"></a>Code des Benutzersteuerelements  
  
1.  Doppelklicken Sie auf das Formular, um die Load-Ereignishandler im Code-Fenster zu öffnen.  
  
2.  Erstellen Sie über die Ereignishandlermethode in der Steuerelementklasse eine ganze Zahl zum Speichern der Wert dieses Indikators und eine Zeichenfolge, die den anzuzeigenden Text speichern, wie im folgenden Beispiel gezeigt.  
  
    ```c#  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Erstellen Sie die folgenden Deklarationen der öffentlichen Eigenschaft.  
  
    ```c#  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     Aufrufer erreichen dieser Eigenschaften abrufen und festlegen den Anzeigetext des Indikators und zum Anzeigen oder Ausblenden der `Reset` Schaltfläche. Aufrufer erhalten den aktuellen Wert der schreibgeschützten `Value` -Eigenschaft, aber sie können nicht den Wert direkt festlegen.  
  
4.  Fügen Sie den folgenden Code in die `Load` -Ereignis für das Steuerelement.  
  
    ```c#  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Festlegen der **Bezeichnung** Text in das <xref:System.Windows.Forms.UserControl.Load>Ereignis ermöglicht die Zieleigenschaften geladen, bevor ihre Werte angewendet werden.</xref:System.Windows.Forms.UserControl.Load> Festlegen der **Bezeichnung** Text im Konstruktor ergibt ein leeres **Bezeichnung**.  
  
5.  Erstellen Sie die folgende öffentliche Methode, um die Zähler inkrementiert.  
  
    ```c#  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Fügen Sie eine Deklaration für das `Incremented` Ereignis, um die Control-Klasse.  
  
    ```c#  
    public event EventHandler Incremented;  
    ```  
  
     Aufrufer können auf dieses Ereignis reagieren auf Änderungen in den Wert des Indikators hinzufügen.  
  
7.  Kehren Sie zur Entwurfsansicht, und doppelklicken Sie auf zurück der `Reset` Schaltfläche zum Generieren der `btnReset_Click` Ereignishandler, und füllen Sie es in, wie im folgenden Beispiel gezeigt.  
  
    ```c#  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Direkt oberhalb der Klassendefinition in die `ProvideToolboxControl` -Attributdeklaration, ändern Sie den Wert des ersten Parameters von `"MyWinFormsControl.Counter"` auf `"General"`. Dadurch wird der Name der Elementgruppe festgelegt, die das Steuerelement in der **Toolbox**hostet.  
  
     Das folgende Beispiel zeigt das `ProvideToolboxControl` -Attribut und die angepasste Klassendefinition.  
  
    ```c#  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Testen des Steuerelements  
 So testen Sie eine **Toolbox** steuern, testen Sie es zunächst in der Development Environment, und es dann in einer kompilierten Anwendung testen.  
  
##### <a name="to-test-the-control"></a>So testen Sie das Steuerelement  
  
1.  Drücken Sie F5.  
  
     Erstellt das Projekt und öffnet eine zweite experimentelle Instanz von Visual Studio, das Steuerelement installiert ist.  
  
2.  Erstellen Sie in der experimentellen Instanz von Visual Studio eine **Windows Forms-Anwendung** Projekt.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf "Form1.cs", um sie im Designer zu öffnen, wenn es nicht bereits geöffnet ist.  
  
4.  In der **Toolbox**, `Counter` Steuerelement angezeigt werden soll, der **allgemeine** Abschnitt.  
  
5.  Ziehen Sie eine `Counter` in das Formular, und wählen Sie es. Die `Value`, `Message`, und `ShowReset` Eigenschaften werden angezeigt, der **Eigenschaften** zusammen mit den Eigenschaften, die geerbt werden, <xref:System.Windows.Forms.UserControl>.</xref:System.Windows.Forms.UserControl> -Fenster  
  
6.  Legen Sie die `Message`-Eigenschaft auf `Count:` fest.  
  
7.  Ziehen Sie eine <xref:System.Windows.Forms.Button>-Steuerelement auf das Formular, und legen Sie dann die Eigenschaften Name und Text der Schaltfläche auf `Test`.</xref:System.Windows.Forms.Button>  
  
8.  Doppelklicken Sie auf die Schaltfläche Öffnen Sie Form1.cs in der Codeansicht, und erstellen Sie einen Click-Ereignishandler.  
  
9. Rufen Sie in der Click-Ereignishandler `counter1.Increment()`.  
  
10. In der Konstruktorfunktion, nach dem Aufruf von `InitializeComponent`, Typ `counter1``.``Incremented +=` und die Tabulatortaste zweimal drücken.  
  
     Visual Studio generiert einen Handler auf Formularebene für die `counter1.Incremented` Ereignis.  
  
11. Markieren Sie die `Throw` -Anweisung in den Ereignishandler Typ `mbox`, und drücken Sie dann die Registerkarte zweimal, um ein Meldungsfeld der Mbox-Codeausschnitt zu generieren.  
  
12. Fügen Sie auf der nächsten Zeile die folgenden `if` / `else` Block, um die Sichtbarkeit der Festlegen der `Reset` Schaltfläche.  
  
    ```c#  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Drücken Sie F5.  
  
     Das Formular wird geöffnet. Die `Counter` -Steuerelement zeigt den folgenden Text.  
  
     **Anzahl: 0**  
  
14. Klicken Sie auf **Test**.  
  
     Der Zähler erhöht und die Visual Studio zeigt ein Meldungsfenster an.  
  
15. Das Meldungsfeld zu schließen.  
  
     Die **zurücksetzen** Schaltfläche wird ausgeblendet.  
  
16. Klicken Sie auf **Test** bis der Zähler ist **5** jedem Feldern durch das Schließen der Nachricht.  
  
     Die **zurücksetzen** Schaltfläche wird erneut angezeigt.  
  
17. Klicken Sie auf **Zurücksetzen**.  
  
     Der Leistungsindikator wird zurückgesetzt, um **0**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Beim Erstellen eines **Toolbox** -Steuerelements erstellt Visual Studio eine Datei namens *Projektname*.vsix im Ordner „\bin\debug\“ des Projekts. Sie können das Steuerelement bereitstellen, indem Sie die VSIX-Datei in ein Netzwerk oder auf eine Website hochladen. Wenn ein Benutzer die VSIX-Datei öffnet, wird das Steuerelement installiert und Visual Studio hinzugefügt **Toolbox** auf dem Computer des Benutzers. Alternativ können Sie die VSIX-Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) -Website, damit Benutzer diesen finden können, indem Sie Durchsuchen der **Extras / Erweiterungen und Updates** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern Sie die Toolbox](../misc/extending-the-toolbox.md)   
 [Erstellen ein WPF-Toolbox-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Grundlagen der Entwicklung von Windows Forms](http://msdn.microsoft.com/Library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)
