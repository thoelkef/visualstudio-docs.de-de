---
title: Erstellen eine Windows Forms-Toolbox-Steuerelement | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371fd4269cee5918bd0d0b623eb49e1f709a311d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781711"
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Erstellen eines Windows Forms-Toolbox-Steuerelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ermöglicht das Erstellen ein Steuerelements, das automatisch hinzugefügt wird, die Toolbox-Steuerelement von Windows Forms-Elementvorlage, die in Visual Studio-Erweiterbarkeitstools (VS SDK) enthalten ist das **Toolbox** beim Installieren der Erweiterung. In diesem Thema wird gezeigt, wie die Vorlage zu verwenden, um einen einfachen Zähler-Steuerelement zu erstellen, die Sie für andere Benutzer verteilen können.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Erstellen eines Windows Forms-Toolbox-Steuerelements  
 Die Windows Forms-Toolbox-Steuerelement-Vorlage erstellt ein nicht definiertes Benutzersteuerelement und enthält alle Funktionen, die erforderlich ist, um das Steuerelement, das Hinzufügen der **Toolbox**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Erstellen Sie eine Erweiterung mit einer Windows Forms-Toolbox-Steuerelement  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `MyWinFormsControl`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, eine **Windows Forms-Toolbox-Steuerelement** Item-Vorlage, die mit dem Namen `Counter`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **Windows Forms-Toolbox-Steuerelement**  
  
3.  Dadurch werden ein Benutzersteuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> zum Platzieren des Steuerelements in der **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** Ressourceneintrag im VSIX-Manifest für die Bereitstellung.  
  
### <a name="building-a-user-interface-for-the-control"></a>Erstellen einer Benutzeroberfläche für das Steuerelement  
 Die `Counter` Steuerelement erfordert zwei untergeordneten Steuerelementen: eine <xref:System.Windows.Forms.Label> zum Anzeigen der aktuellen Anzahl und eine <xref:System.Windows.Forms.Button> auf die Anzahl der auf 0 zurückgesetzt. Ohne weitere untergeordnete Steuerelemente sind erforderlich, da der Aufrufer den Zähler programmgesteuert erhöht werden.  
  
##### <a name="to-build-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf Counter.cs, um sie im Designer zu öffnen.  
  
2.  Entfernen Sie die "hier klicken!" **Schaltfläche** , ist standardmäßig enthalten, wenn Sie die Elementvorlage für Windows Forms-Toolbox-Steuerelement hinzufügen.  
  
3.  Von der **Toolbox**, ziehen Sie eine `Label` Steuerelement und dann eine `Button` Steuerelement darunter auf die Entwurfsoberfläche.  
  
4.  Größe des gesamten Benutzersteuerelements auf 150, 50 Pixel, und Ändern der Größe der Schaltfläche steuern, bis 50, 20 Pixel.  
  
5.  In der **Eigenschaften** legen die folgenden Werte für die Steuerelemente auf der Entwurfsoberfläche angezeigt.  
  
    |Steuerelement|Eigenschaft|Wert|  
    |-------------|--------------|-----------|  
    |`Label1`|**Text**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**Text**|Zurücksetzen|  
  
### <a name="coding-the-user-control"></a>Codieren des Benutzersteuerelements  
 Das `Counter` -Steuerelement macht folgende Elemente verfügbar: eine Methode zum Erhöhen des Zählerwerts, ein Ereignis, das immer dann ausgelöst wird, wenn der Zählerwert erhöht wird, eine `Reset` -Schaltfläche sowie drei Eigenschaften, mit denen die aktuelle Anzahl und der Anzeigetext gespeichert werden bzw. festgelegt wird, ob die `Reset` -Schaltfläche ein- oder ausgeblendet wird. Das `ProvideToolboxControl` -Attribut bestimmt, an welcher Stelle in der **Toolbox** das `Counter` -Steuerelement angezeigt wird.  
  
##### <a name="to-code-the-user-control"></a>Codieren des Benutzersteuerelements  
  
1.  Doppelklicken Sie auf das Formular, um die Load-Ereignishandler im Code-Fenster zu öffnen.  
  
2.  Erstellen Sie über die Ereignishandlermethode in der Steuerelementklasse eine ganze Zahl zum Speichern der Wert dieses Indikators und eine Zeichenfolge, die den anzuzeigenden Text zu speichern, wie im folgenden Beispiel dargestellt.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Erstellen Sie die folgenden Deklarationen für die öffentliche Eigenschaft.  
  
    ```csharp  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     Aufrufer stehen diese Eigenschaften zum Abrufen und festlegen den Anzeigetext des Indikators und zum Anzeigen oder Ausblenden der `Reset` Schaltfläche. Aufrufer erhalten den aktuellen Wert der Read-only `Value` -Eigenschaft, aber sie können nicht den Wert direkt festlegen.  
  
4.  Platzieren Sie den folgenden Code in die `Load` Ereignis für das Steuerelement.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     Festlegen der **Bezeichnung** Text in die <xref:System.Windows.Forms.UserControl.Load> Ereignis können die Eigenschaften als Ziel zu laden, bevor Sie ihre Werte angewendet werden. Festlegen der **Bezeichnung** Text im Konstruktor ergibt ein leeres **Bezeichnung**.  
  
5.  Erstellen Sie die folgende öffentliche Methode, um den Zähler zu erhöhen.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Fügen Sie eine Deklaration für die `Incremented` Ereignis, um die Control-Klasse.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     Aufrufer können Handler für dieses Ereignis reagieren auf Änderungen in den Wert des Zählers hinzufügen.  
  
7.  Wechseln Sie zurück zur Entwurfsansicht, und doppelklicken Sie auf die `Reset` Schaltfläche zum Generieren der `btnReset_Click` Ereignishandler, und füllen Sie es dann darüber, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Ändern Sie direkt oberhalb der Klassendefinition in der `ProvideToolboxControl` -Attributdeklaration den Wert des ersten Parameters von `"MyWinFormsControl.Counter"` in `"General"`. Dadurch wird der Name der Elementgruppe festgelegt, die das Steuerelement in der **Toolbox**hostet.  
  
     Das folgende Beispiel zeigt das `ProvideToolboxControl` -Attribut und die angepasste Klassendefinition.  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Testen des Steuerelements  
 So testen Sie eine **Toolbox** steuern, testen Sie es zunächst in der Entwicklungsumgebung aus, und klicken Sie dann zu einer kompilierten Anwendung testen.  
  
##### <a name="to-test-the-control"></a>So testen Sie das Steuerelement  
  
1.  Drücken Sie F5.  
  
     Dies erstellt das Projekt und öffnet eine zweite experimentelle Instanz von Visual Studio, die das Steuerelement installiert ist.  
  
2.  Erstellen Sie in der experimentellen Instanz von Visual Studio eine **Windows Forms-Anwendung** Projekt.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf "Form1.cs", um sie im Designer zu öffnen, wenn es nicht bereits geöffnet ist.  
  
4.  In der **Toolbox**, `Counter` Steuerelement angezeigt werden soll, der **allgemeine** Abschnitt.  
  
5.  Ziehen Sie eine `Counter` -Steuerelement zu Ihrem Formular ein, und wählen Sie ihn. Die `Value`, `Message`, und `ShowReset` werden Eigenschaften angezeigt werden, der **Eigenschaften** Fenster zusammen mit den Eigenschaften, die von geerbt werden <xref:System.Windows.Forms.UserControl>.  
  
6.  Legen Sie die `Message` -Eigenschaft auf `Count:`fest.  
  
7.  Ziehen Sie eine <xref:System.Windows.Forms.Button> -Steuerelement auf das Formular, und legen die Eigenschaften für Name und Text der Schaltfläche auf `Test`.  
  
8.  Doppelklicken Sie auf die Schaltfläche, um die "Form1.cs" in der Codeansicht zu öffnen und erstellen Sie einen Ereignishandler auf.  
  
9. Rufen Sie in der Click-Ereignishandler `counter1.Increment()`.  
  
10. In der Konstruktorfunktion, nach dem Aufruf von `InitializeComponent`, Typ `counter1``.``Incremented +=` , und drücken Sie dann zweimal die TAB.  
  
     Visual Studio generiert einen Handler auf Formularebene für die `counter1.Incremented` Ereignis.  
  
11. Markieren Sie die `Throw` -Anweisung in dem Ereignishandler geben `mbox`, und drücken Sie dann die Registerkarte zweimal, um ein Meldungsfeld mit dem Codeausschnitt Mbox zu generieren.  
  
12. Fügen Sie in der nächsten Zeile, die folgenden `if` / `else` Block, um die Sichtbarkeit der Festlegen der `Reset` Schaltfläche.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Drücken Sie F5.  
  
     Das Formular wird geöffnet. Die `Counter` Steuerelement zeigt den folgenden Text.  
  
     **Anzahl: 0**  
  
14. Klicken Sie auf **Test**.  
  
     Der Zähler erhöht und die Visual Studio zeigt ein Meldungsfeld an.  
  
15. Das Meldungsfeld zu schließen.  
  
     Die **zurücksetzen** Schaltfläche wird ausgeblendet.  
  
16. Klicken Sie auf **Test** bis der Zähler ist **5** schließen die Nachricht jedes Mal Felder.  
  
     Die **zurücksetzen** Schaltfläche wird erneut angezeigt.  
  
17. Klicken Sie auf **Zurücksetzen**.  
  
     Der Leistungsindikator wird zurückgesetzt, um **0**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Beim Erstellen eines **Toolbox** -Steuerelements erstellt Visual Studio eine Datei namens *Projektname*.vsix im Ordner „\bin\debug\“ des Projekts. Sie können das Steuerelement bereitstellen, indem Sie die VSIX-Datei in ein Netzwerk oder auf eine Website hochladen. Wenn ein Benutzer die VSIX-Datei öffnet, wird das Steuerelement installiert und in Visual Studio hinzugefügt **Toolbox** auf dem Computer des Benutzers. Alternativ können Sie die VSIX-Datei zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website aus, damit Benutzer sie finden können der **Extras / Erweiterungen und Updates** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Erstellen eines WPF-Toolbox-Steuerelements](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Grundlagen für das Entwickeln von Windows Forms-Steuerelementen](http://msdn.microsoft.com/library/6277bb81-90f7-4c5b-9f4b-b02bb42dd316)

