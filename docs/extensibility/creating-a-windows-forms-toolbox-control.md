---
title: Erstellen eines Windows Forms Toolbox-Steuerelements | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7e7749302252c5d56f21c58de9b6ac23f898572
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739582"
---
# <a name="create-a-windows-forms-toolbox-control"></a>Erstellen eines Windows Forms Toolbox-Steuerelements

Mit der Elementevorlage Windows Forms Toolbox Control, die in den Visual Studio Extensibility Tools (VS SDK) enthalten ist, können Sie ein **Toolbox-Steuerelement** erstellen, das automatisch hinzugefügt wird, wenn die Erweiterung installiert wird. In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie die Vorlage verwenden, um ein einfaches Leistungsindikatorsteuerelement zu erstellen, das Sie an andere Benutzer verteilen können.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-toolbox-control"></a>Erstellen des Toolbox-Steuerelements

Die Windows Forms Toolbox Control-Vorlage erstellt ein nicht definiertes Benutzersteuerelement und stellt alle Funktionen bereit, die zum Hinzufügen des Steuerelements zur **Toolbox**erforderlich sind.

### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Erstellen einer Erweiterung mit einem Windows Forms Toolbox-Steuerelement

1. Erstellen Sie ein `MyWinFormsControl`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie `Counter`eine Windows Forms Toolbox **Control-Elementvorlage** mit dem Namen hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Erweiterbarkeit,** > **Extensibility** und wählen Sie Windows Forms **Toolbox Control** aus.

3. Dadurch wird ein Benutzersteuerelement, ein `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> zum Platzieren des Steuerelements in der **Toolbox**und ein **Microsoft.VisualStudio.ToolboxControl** Asset-Eintrag im VSIX-Manifest für die Bereitstellung hinzugefügt.

### <a name="build-a-user-interface-for-the-control"></a>Erstellen einer Benutzeroberfläche für das Steuerelement

Das `Counter` Steuerelement erfordert zwei <xref:System.Windows.Forms.Label> untergeordnete Steuerelemente: eine, <xref:System.Windows.Forms.Button> um die aktuelle Anzahl anzuzeigen, und eine, um die Anzahl auf 0 zurückzusetzen. Es sind keine anderen untergeordneten Steuerelemente erforderlich, da Aufrufer den Zähler programmgesteuert erhöhen.

#### <a name="to-build-the-user-interface"></a>So erstellen Sie die Benutzeroberfläche

1. Doppelklicken Sie im **Projektmappen-Explorer**auf *Counter.cs,* um sie im Designer zu öffnen.

2. Entfernen Sie die **Klicken Sie hier !** Schaltfläche, die standardmäßig beim Hinzufügen der Windows Forms Toolbox Control-Elementvorlage enthalten ist.

3. Ziehen **Toolbox**Sie aus `Label` der Toolbox `Button` ein Steuerelement und dann ein Steuerelement darunter auf die Entwurfsoberfläche.

4. Ändern Sie die Größe des gesamten Benutzersteuerelements auf 150, 50 Pixel, und ändern Sie die Größe des Schaltflächensteuerelements auf 50, 20 Pixel.

5. Legen Sie im **Fenster Eigenschaften** die folgenden Werte für die Steuerelemente auf der Entwurfsoberfläche fest.

    |Control|Eigenschaft|Wert|
    |-------------|--------------|-----------|
    |`Label1`|**Text**|""|
    |`Button1`|**Name**|btnReset|
    |`Button1`|**Text**|Reset|

### <a name="code-the-user-control"></a>Codeieren des Benutzersteuerelements

Das `Counter` Steuerelement macht eine Methode zum Erhöhen des Leistungsindikators verfügbar, ein Ereignis, das ausgelöst werden soll, wenn der Zähler erhöht wird, eine **Reset-Schaltfläche** und drei Eigenschaften zum Speichern der aktuellen Anzahl, des Anzeigetexts und zum Ein- oder Ausblenden der **Schaltfläche Zurücksetzen.** Das `ProvideToolboxControl` -Attribut bestimmt, an welcher Stelle in der **Toolbox** das `Counter` -Steuerelement angezeigt wird.

#### <a name="to-code-the-user-control"></a>So codieren Sie das Benutzersteuerelement

1. Doppelklicken Sie auf das Formular, um den Ladeereignishandler im Codefenster zu öffnen.

2. Oberhalb der Ereignishandlermethode erstellen Sie in der Steuerelementklasse eine ganze Zahl zum Speichern des Leistungsindikatorwerts und eine Zeichenfolge zum Speichern des Anzeigetexts, wie im folgenden Beispiel gezeigt.

    ```csharp
    int currentValue;
    string displayText;
    ```

3. Erstellen Sie die folgenden öffentlichen Eigenschaftsdeklarationen.

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

    Anrufer können auf diese Eigenschaften zugreifen, um den Anzeigetext des Leistungsindikators abzurufen und festzulegen und die **Schaltfläche Zurücksetzen ein-** oder auszublenden. Aufrufer können den aktuellen Wert der `Value` schreibgeschützten Eigenschaft abrufen, aber sie können den Wert nicht direkt festlegen.

4. Setzen Sie den `Load` folgenden Code in das Ereignis für das Steuerelement.

    ```csharp
    private void Counter_Load(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = Message + Value;
    }

    ```

    Wenn Sie den <xref:System.Windows.Forms.UserControl.Load> **Label-Text** im Ereignis festlegen, können die Zieleigenschaften geladen werden, bevor ihre Werte angewendet werden. Das Festlegen des **Label-Textes** im Konstruktor würde zu einer leeren **Beschriftung**führen.

5. Erstellen Sie die folgende öffentliche Methode, um den Leistungsindikator zu erhöhen.

    ```csharp
    public void Increment()
    {
        currentValue++;
        label1.Text = displayText + Value;
        Incremented(this, EventArgs.Empty);
    }

    ```

6. Fügen Sie der `Incremented` Steuerelementklasse eine Deklaration für das Ereignis hinzu.

    ```csharp
    public event EventHandler Incremented;
    ```

    Aufrufer können diesem Ereignis Handler hinzufügen, um auf Änderungen im Wert des Leistungsindikators zu reagieren.

7. Kehren Sie zur Entwurfsansicht zurück, und `btnReset_Click` doppelklicken Sie auf die Schaltfläche **Zurücksetzen,** um den Ereignishandler zu generieren, und füllen Sie ihn dann aus, wie im folgenden Beispiel gezeigt.

    ```csharp
    private void btnReset_Click(object sender, EventArgs e)
    {
        currentValue = 0;
        label1.Text = displayText + Value;
    }

    ```

8. Ändern Sie direkt oberhalb der Klassendefinition in der `ProvideToolboxControl` -Attributdeklaration den Wert des ersten Parameters von `"MyWinFormsControl.Counter"` in `"General"`. Dadurch wird der Name der Elementgruppe festgelegt, die das Steuerelement in der **Toolbox**hostet.

    Das folgende Beispiel zeigt das `ProvideToolboxControl` -Attribut und die angepasste Klassendefinition.

    ```csharp
    [ProvideToolboxControl("General", false)]
    public partial class Counter : UserControl
    ```

### <a name="test-the-control"></a>Testen des Steuerelements

 Um ein **Toolbox-Steuerelement** zu testen, testen Sie es zunächst in der Entwicklungsumgebung, und testen Sie es dann in einer kompilierten Anwendung.

#### <a name="to-test-the-control"></a>So testen Sie das Steuerelement

1. Drücken Sie **F5,** um mit **dem Debuggen**zu beginnen.

    Dieser Befehl erstellt das Projekt und öffnet eine zweite Experimentelle Instanz von Visual Studio, auf der das Steuerelement installiert ist.

2. Erstellen Sie in der experimentellen Instanz von Visual Studio ein **Windows Forms Application-Projekt.**

3. Doppelklicken Sie im **Projektmappen-Explorer**auf *Form1.cs,* um sie im Designer zu öffnen, wenn sie noch nicht geöffnet ist.

4. In **Toolbox**der Toolbox `Counter` sollte das Steuerelement im Abschnitt **Allgemein** angezeigt werden.

5. Ziehen `Counter` Sie ein Steuerelement in das Formular, und wählen Sie es aus. Die `Value` `Message`, `ShowReset` und Eigenschaften werden im **Eigenschaftenfenster** zusammen mit den Eigenschaften <xref:System.Windows.Forms.UserControl>angezeigt, die von geerbt werden.

6. Setzen Sie die `Message`-Eigenschaft auf `Count:`.

7. Ziehen <xref:System.Windows.Forms.Button> Sie ein Steuerelement in das Formular, und legen `Test`Sie dann den Namen und die Texteigenschaften der Schaltfläche auf fest.

8. Doppelklicken Sie auf die Schaltfläche, um *Form1.cs* in der Codeansicht zu öffnen und einen Klickhandler zu erstellen.

9. Rufen Sie im `counter1.Increment()`Klickhandler an.

10. Geben Sie in der Konstruktorfunktion `counter1``.``Incremented +=` nach dem Aufruf von `InitializeComponent`ein, und drücken Sie dann zweimal die **Tabulatortaste.**

    Visual Studio generiert einen Handler `counter1.Incremented` auf Formularebene für das Ereignis.

11. Markieren `Throw` Sie die Anweisung im `mbox`Ereignishandler, geben Sie ein, und drücken Sie dann zweimal die **Tabulatortaste,** um ein Meldungsfeld aus dem mbox-Codeausschnitt zu generieren.

12. Fügen Sie in der `if` / `else` nächsten Zeile den folgenden Block hinzu, um die Sichtbarkeit der **Schaltfläche Zurücksetzen festzulegen.**

    ```csharp
    if (counter1.Value < 5) counter1.ShowReset = false;
    else counter1.ShowReset = true;
    ```

13. Drücken Sie **F5**.

    Das Formular wird geöffnet. Das `Counter` Steuerelement zeigt den folgenden Text an.

    **Anzahl: 0**

14. Klicken Sie auf **Testen**.

    Die Leistungsindikatorinkremente werden erhöht, und Visual Studio zeigt ein Meldungsfeld an.

15. Schließen Sie das Meldungsfeld.

    Die **Reset-Taste** verschwindet.

16. Klicken Sie auf **Testen,** bis der Zähler **5** erreicht, die die Meldungsfelder jedes Mal schließen.

    Die **Reset-Schaltfläche** wird erneut angezeigt.

17. Klicken Sie auf **Zurücksetzen**.

    Der Zähler wird auf **0**zurückgesetzt.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie ein **Toolbox-Steuerelement** erstellen, erstellt Visual Studio eine Datei mit dem Namen *ProjectName.vsix* im Ordner "bin"-Debug" ihres Projekts. Sie können das Steuerelement bereitstellen, indem Sie die *vSix-Datei* in ein Netzwerk oder eine Website hochladen. Wenn ein Benutzer die *.vsix-Datei* öffnet, wird das Steuerelement installiert und der Visual Studio **Toolbox** auf dem Computer des Benutzers hinzugefügt. Alternativ können Sie die *.vsix-Datei* in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) hochladen, damit Benutzer sie finden können, indem Sie im Dialogfeld**Tools-Erweiterungen** **Tools** > und Updates navigieren.

## <a name="see-also"></a>Weitere Informationen

- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Erstellen eines WPF Toolbox-Steuerelements](../extensibility/creating-a-wpf-toolbox-control.md)
- [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Grundlagen der Windows Forms-Steuerelemententwicklung](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)
