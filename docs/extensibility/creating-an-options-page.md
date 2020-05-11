---
title: Erstellen einer Optionsseite | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739519"
---
# <a name="create-an-options-page"></a>Erstellen einer Optionsseite

In dieser exemplarischen Vorgehensweise wird eine einfache Seite "Tools/Optionen" erstellt, die ein Eigenschaftenraster zum Untersuchen und Festlegen von Eigenschaften verwendet.

 Um diese Eigenschaften in einer Einstellungsdatei zu speichern und aus dieser Wiederherstellung wiederherzustellen, führen Sie die folgenden Schritte aus, und lesen Sie dann [die Kategorie Einstellungen erstellen](../extensibility/creating-a-settings-category.md).

 Die MPF stellt zwei Klassen bereit, mit <xref:Microsoft.VisualStudio.Shell.Package> denen <xref:Microsoft.VisualStudio.Shell.DialogPage> Sie Seiten für Tools-Optionen, die Klasse und die Klasse erstellen können. Sie erstellen ein VSPackage, um einen Container für `Package` diese Seiten bereitzustellen, indem Sie die Klasse unterklassen. Sie erstellen jede Werkzeugoptionsseite, indem `DialogPage` Sie von der Klasse ableiten.

## <a name="prerequisites"></a>Voraussetzungen

 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Erstellen einer Rasterseite für Tools-Optionen

 In diesem Abschnitt erstellen Sie ein einfaches Eigenschaftenraster für Tools-Optionen. Sie verwenden dieses Raster, um den Wert einer Eigenschaft anzuzeigen und zu ändern.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>So erstellen Sie das VSIX-Projekt und fügen ein VSPackage hinzu

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungsprojekt, das die Erweiterungselemente enthält. Erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie ein `MyToolsOptionsExtension`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Fügen Sie ein VSPackage hinzu, indem `MyToolsOptionsPackage`Sie eine Visual Studio-Paketelementvorlage mit dem Namen hinzufügen. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im **Dialogfeld Neues Element hinzufügen**zu **Visual C-Items** > **Extensibility,** und wählen Sie **Visual Studio-Paket aus.** Ändern Sie im Feld **Name** am unteren Rand `MyToolsOptionsPackage.cs`des Dialogfelds den Dateinamen in . Weitere Informationen zum Erstellen eines VSPackage finden Sie unter [Erstellen einer Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>So erstellen Sie das Eigenschaftenraster "Tools Options"

1. Öffnen Sie die Datei *MyToolsOptionsPackage* im Code-Editor.

2. Fügen Sie die folgende Verwendungsanweisung hinzu.

   ```csharp
   using System.ComponentModel;
   ```

3. Deklarieren Sie eine `OptionPageGrid` <xref:Microsoft.VisualStudio.Shell.DialogPage>Klasse, und leiten Sie sie von ab.

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Wenden <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Sie `VSPackage` eine auf die Klasse an, um der Klasse eine Optionskategorie und den Seitennamen der Optionen für das OptionPageGrid zuzuweisen. Das Ergebnis sollte wie folgt aussehen:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Fügen `OptionInteger` Sie der `OptionPageGrid` Klasse eine Eigenschaft hinzu.

    - Wenden <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> Sie eine an, um der Eigenschaft eine Eigenschaftgridkategorie zuzuweisen.

    - Wenden <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> Sie eine an, um der Eigenschaft einen Namen zuzuweisen.

    - Wenden <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> Sie eine an, um der Eigenschaft eine Beschreibung zuzuweisen.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Die Standardimplementierung <xref:Microsoft.VisualStudio.Shell.DialogPage> von unterstützt Eigenschaften, die über entsprechende Konverter verfügen oder Strukturen oder Arrays sind, die in Eigenschaften mit entsprechenden Konvertern erweitert werden können. Eine Liste der Konverter finden <xref:System.ComponentModel> Sie im Namespace.

6. Erstellen Sie das Projekt, und starten Sie das Debugging.

7. Klicken Sie in der experimentellen Instanz von Visual Studio im Menü **Extras** auf **Optionen**.

     Im linken Bereich finden Sie **Meine Kategorie**. (Optionskategorien sind in alphabetischer Reihenfolge aufgeführt, daher sollte sie etwa auf halbem Weg in der Liste angezeigt werden.) Öffnen Sie **Meine Kategorie,** und klicken Sie dann auf **Meine Rasterseite**. Das Optionsraster wird im rechten Bereich angezeigt. Die Eigenschaftskategorie ist **Meine Optionen**, und der Eigenschaftsname ist **Meine Ganzzahloption**. Die Eigenschaftenbeschreibung **"Meine Ganzzahloption**" wird am unteren Rand des Bereichs angezeigt. Ändern Sie den Wert von seinem Anfangswert 256 in etwas anderes. Klicken Sie auf **OK**, und öffnen Sie dann **Meine Rasterseite**erneut. Sie können sehen, dass der neue Wert beibehalten wird.

     Ihre Optionsseite ist auch über das Suchfeld von Visual Studio verfügbar. Geben Sie im Suchfeld am oberen Rand der IDE **Meine Kategorie** ein, und in den Ergebnissen werden Meine **Kategorie -> Meine Rasterseite** aufgeführt.

## <a name="create-a-tools-options-custom-page"></a>Erstellen einer benutzerdefinierten Seite mit Tools-Optionen

 In diesem Abschnitt erstellen Sie eine Seite "Tools-Optionen" mit einer benutzerdefinierten Benutzeroberfläche. Sie verwenden diese Seite, um den Wert einer Eigenschaft anzuzeigen und zu ändern.

1. Öffnen Sie die Datei *MyToolsOptionsPackage* im Code-Editor.

2. Fügen Sie die folgende Verwendungsanweisung hinzu.

    ```csharp
    using System.Windows.Forms;
    ```

3. Fügen `OptionPageCustom` Sie eine Klasse `OptionPageGrid` kurz vor der Klasse hinzu. Leiten Sie die `DialogPage`neue Klasse von ab.

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Fügen Sie ein GUID-Attribut hinzu. Hinzufügen einer OptionString-Eigenschaft:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Wenden Sie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> eine Sekunde auf die VSPackage-Klasse an. Dieses Attribut weist der Klasse eine Optionskategorie und einen Optionsseitennamen zu.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Fügen Sie dem Projekt ein neues **Benutzersteuerelement** mit dem Namen MyUserControl hinzu.

7. Fügen Sie dem Benutzersteuerelement ein **TextBox-Steuerelement** hinzu.

     Klicken Sie im **Fenster Eigenschaften** auf der Symbolleiste auf die Schaltfläche **Ereignisse,** und doppelklicken Sie dann auf das **Ereignis Verlassen.** Der neue Ereignishandler wird im *MyUserControl.cs-Code* angezeigt.

8. Fügen Sie `OptionsPage` der `Initialize` Steuerelementklasse ein öffentliches Feld, eine Methode hinzu, und aktualisieren Sie den Ereignishandler, um den Optionswert auf den Inhalt des Textfelds festzulegen:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     Das `optionsPage` Feld enthält einen `OptionPageCustom` Verweis auf die übergeordnete Instanz. Die `Initialize` Methode `OptionString` wird in der **TextBox**angezeigt. Der Ereignishandler schreibt den aktuellen Wert `OptionString` der **TextBox** in die Zeit, wenn focus die **TextBox**verlässt.

9. Fügen Sie in `OptionPageCustom.Window` `OptionPageCustom` der Paketcodedatei der Klasse eine Außerkraftsetzung für die Eigenschaft `MyUserControl`hinzu, um eine Instanz von zu erstellen, zu initialisieren und zurückzugeben. Die Klasse sollte nun wie folgt aussehen:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Erstellen Sie das Projekt, und führen Sie es aus.

11. Klicken Sie in der experimentellen Instanz auf > **Tools-Optionen**. **Tools**

12. Suchen Sie **meine Kategorie** und dann **Meine benutzerdefinierte Seite**.

13. Ändern Sie den Wert von **OptionString**. Klicken Sie auf **OK**, und öffnen Sie **dann Meine benutzerdefinierte Seite**erneut. Sie können sehen, dass der neue Wert beibehalten wurde.

## <a name="access-options"></a>Zugriffsoptionen

 In diesem Abschnitt erhalten Sie den Wert einer Option aus dem VSPackage, das die zugehörige Seite Tools-Optionen hostet. Die gleiche Technik kann verwendet werden, um den Wert jedes öffentlichen Eigentums zu erhalten.

1. Fügen Sie in der Paketcodedatei der **MyToolsOptionsPackage-Klasse** eine öffentliche Eigenschaft namens **OptionInteger** hinzu.

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Dieser Code <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> ruft auf, `OptionPageGrid` um eine Instanz zu erstellen oder abzurufen. `OptionPageGrid`, <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> um die Optionen zu laden, bei denen es sich um öffentliche Eigenschaften handelt.

2. Fügen Sie nun eine benutzerdefinierte Befehlselementvorlage mit dem Namen **MyToolsOptionsCommand** hinzu, um den Wert anzuzeigen. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **Benutzerdefinierter Befehl aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *MyToolsOptionsCommand.cs*.

3. Ersetzen Sie in der Datei *MyToolsOptionsCommand* den `ShowMessageBox` Text der Befehlsmethode durch Folgendes:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Erstellen Sie das Projekt, und starten Sie das Debugging.

5. Klicken Sie in der experimentellen Instanz im Menü **Extras** auf **MyToolsOptionsCommand**aufrufen .

     Ein Meldungsfeld zeigt `OptionInteger`den aktuellen Wert von an.

## <a name="see-also"></a>Weitere Informationen

- [Options- und Optionsseiten](../extensibility/internals/options-and-options-pages.md)
