---
title: Erstellen eine Windows Forms-Toolbox-Steuerelement | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b84c554427d443d54d117b72cec5a423e10e7887
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872920"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Erstellen eines Windows Forms-Toolbox-Steuerelements
Ermöglicht das Erstellen ein Steuerelements, das automatisch hinzugefügt wird, die Toolbox-Steuerelement von Windows Forms-Elementvorlage, die in Visual Studio-Erweiterbarkeitstools (VS SDK) enthalten ist das **Toolbox** beim Installieren der Erweiterung. In diesem Thema wird gezeigt, wie die Vorlage zu verwenden, um einen einfachen Zähler-Steuerelement zu erstellen, die Sie für andere Benutzer verteilen können.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-windows-forms-toolbox-control"></a>Erstellen eines Windows Forms-Toolbox-Steuerelements  
 Die Windows Forms-Toolbox-Steuerelement-Vorlage erstellt ein nicht definiertes Benutzersteuerelement und enthält alle Funktionen, die erforderlich ist, um das Steuerelement, das Hinzufügen der **Toolbox**.  
  
### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Erstellen Sie eine Erweiterung mit einer Windows Forms-Toolbox-Steuerelement  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen `MyWinFormsControl`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual C#-** > **Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, eine **Windows Forms-Toolbox-Steuerelement** Item-Vorlage, die mit dem Namen `Counter`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **Windows Forms-Toolbox-Steuerelement**  
  
3.  Dadurch werden ein Benutzersteuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> zum Platzieren des Steuerelements in der **Toolbox**, und ein **Microsoft.VisualStudio.ToolboxControl** Ressourceneintrag im VSIX-Manifest für die Bereitstellung.  
  
### <a name="build-a-user-interface-for-the-control"></a>Erstellen einer Benutzeroberfläche für das Steuerelement  
 Die `Counter` Steuerelement erfordert zwei untergeordneten Steuerelementen: eine <xref:System.Windows.Forms.Label> zum Anzeigen der aktuellen Anzahl und eine <xref:System.Windows.Forms.Button> auf die Anzahl der auf 0 zurückgesetzt. Ohne weitere untergeordnete Steuerelemente sind erforderlich, da der Aufrufer den Zähler programmgesteuert erhöht werden.  
  
#### <a name="to-build-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche  
  
1.  In **Projektmappen-Explorer**, doppelklicken Sie auf *Counter.cs* um es im Designer zu öffnen.  
  
2.  Entfernen Sie die **klicken Sie hier!** Schaltfläche, die standardmäßig enthalten ist, wenn Sie die Toolbox-Steuerelement von Windows Forms-Elementvorlage hinzuzufügen.  
  
3.  Von der **Toolbox**, ziehen Sie eine `Label` Steuerelement und dann eine `Button` Steuerelement darunter auf die Entwurfsoberfläche.  
  
4.  Größe des gesamten Benutzersteuerelements auf 150, 50 Pixel, und Ändern der Größe der Schaltfläche steuern, bis 50, 20 Pixel.  
  
5.  In der **Eigenschaften** legen die folgenden Werte für die Steuerelemente auf der Entwurfsoberfläche angezeigt.  
  
    |Steuerelement|Eigenschaft|Wert|  
    |-------------|--------------|-----------|  
    |`Label1`|**Text**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**Text**|Zurücksetzen|  
  
### <a name="code-the-user-control"></a>Code des Benutzersteuerelements  
 Die `Counter` Steuerelement macht eine Methode zum Erhöhen des Zählerwerts, ein Ereignis ausgelöst werden, wenn der Zählerwert erhöht wird, eine **zurücksetzen** Schaltfläche sowie drei Eigenschaften zum Speichern der aktuellen Anzahl, den anzuzeigenden Text und angibt, ob angezeigt oder Ausblenden der **zurücksetzen** Schaltfläche. Das `ProvideToolboxControl` -Attribut bestimmt, an welcher Stelle in der **Toolbox** das `Counter` -Steuerelement angezeigt wird.  
  
#### <a name="to-code-the-user-control"></a>Codieren des Benutzersteuerelements  
  
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
  
     Aufrufer stehen diese Eigenschaften zum Abrufen und festlegen den Anzeigetext des Indikators und zum Anzeigen oder Ausblenden der **zurücksetzen** Schaltfläche. Aufrufer erhalten den aktuellen Wert der Read-only `Value` -Eigenschaft, aber sie können nicht den Wert direkt festlegen.  
  
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
  
7.  Wechseln Sie zurück zur Entwurfsansicht, und doppelklicken Sie auf die **zurücksetzen** Schaltfläche zum Generieren der `btnReset_Click` Ereignishandler, und füllen Sie es dann darüber, wie im folgenden Beispiel gezeigt.  
  
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
  
### <a name="test-the-control"></a>Testen Sie das Steuerelement  
 So testen Sie eine **Toolbox** steuern, testen Sie es zunächst in der Entwicklungsumgebung aus, und klicken Sie dann zu einer kompilierten Anwendung testen.  
  
#### <a name="to-test-the-control"></a>So testen Sie das Steuerelement  
  
1.  Drücken Sie **F5**.  
  
     Dies erstellt das Projekt und öffnet eine zweite experimentelle Instanz von Visual Studio, die das Steuerelement installiert ist.  
  
2.  Erstellen Sie in der experimentellen Instanz von Visual Studio eine **Windows Forms-Anwendung** Projekt.  
  
3.  In **Projektmappen-Explorer**, doppelklicken Sie auf *"Form1.cs"* im Designer öffnen, wenn es nicht bereits geöffnet ist.  
  
4.  In der **Toolbox**, `Counter` Steuerelement angezeigt werden soll, der **allgemeine** Abschnitt.  
  
5.  Ziehen Sie eine `Counter` -Steuerelement zu Ihrem Formular ein, und wählen Sie ihn. Die `Value`, `Message`, und `ShowReset` werden Eigenschaften angezeigt werden, der **Eigenschaften** Fenster zusammen mit den Eigenschaften, die von geerbt werden <xref:System.Windows.Forms.UserControl>.  
  
6.  Legen Sie die `Message` -Eigenschaft auf `Count:`fest.  
  
7.  Ziehen Sie eine <xref:System.Windows.Forms.Button> -Steuerelement auf das Formular, und legen die Eigenschaften für Name und Text der Schaltfläche auf `Test`.  
  
8.  Doppelklicken Sie auf die Schaltfläche mit den um *"Form1.cs"* im code anzeigen und erstellen Sie einen Click-Ereignishandler.  
  
9. Rufen Sie in der Click-Ereignishandler `counter1.Increment()`.  
  
10. In der Konstruktorfunktion, nach dem Aufruf von `InitializeComponent`, Typ `counter1``.``Incremented +=` , und drücken Sie dann die **Registerkarte** zweimal.  
  
     Visual Studio generiert einen Handler auf Formularebene für die `counter1.Incremented` Ereignis.  
  
11. Markieren Sie die `Throw` -Anweisung in dem Ereignishandler geben `mbox`, und drücken Sie dann **Registerkarte** zweimal, um ein Meldungsfeld mit dem Codeausschnitt Mbox zu generieren.  
  
12. Fügen Sie in der nächsten Zeile, die folgenden `if` / `else` Block, um die Sichtbarkeit der Festlegen der **zurücksetzen** Schaltfläche.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Drücken Sie **F5**.  
  
     Das Formular wird geöffnet. Die `Counter` Steuerelement zeigt den folgenden Text.  
  
     **Anzahl von: 0**  
  
14. Klicken Sie auf **Test**.  
  
     Der Zähler erhöht und die Visual Studio zeigt ein Meldungsfeld an.  
  
15. Das Meldungsfeld zu schließen.  
  
     Die **zurücksetzen** Schaltfläche wird ausgeblendet.  
  
16. Klicken Sie auf **Test** bis der Zähler ist **5** schließen die Nachricht jedes Mal Felder.  
  
     Die **zurücksetzen** Schaltfläche wird erneut angezeigt.  
  
17. Klicken Sie auf **Zurücksetzen**.  
  
     Der Leistungsindikator wird zurückgesetzt, um **0**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Beim Erstellen einer **Toolbox** -Steuerelement, das Visual Studio erstellt eine Datei namens *ProjectName.vsix* in der "\bin\debug\" des Projekts. Sie können das Steuerelement bereitstellen, durch das Hochladen der *VSIX* -Datei mit einem Netzwerk oder auf einer Website. Wenn ein Benutzer öffnet die *VSIX* Datei, die das Steuerelement installiert ist, und Visual Studio hinzugefügt **Toolbox** auf dem Computer des Benutzers. Alternativ können Sie hochladen, die *VSIX* Datei [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkID=123847) , damit Benutzer sie finden können der **Tools**  >   **Erweiterungen und Updates** Dialogfeld.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Erstellen Sie ein WPF-Toolbox-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Grundlagen für die Entwicklung von Windows Forms-Steuerelementen](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
