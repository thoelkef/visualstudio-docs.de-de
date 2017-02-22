---
title: "Erstellen eine Optionsseite | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Optionsseiten (Tools) [Visual Studio SDK], erstellen"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
caps.handback.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen eine Optionsseite
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erstellt eine einfache Extras\/Optionen\-Seite, die ein Eigenschaftenraster zum Überprüfen und Festlegen von Eigenschaften verwendet.  
  
 Um diese Eigenschaften zu speichern und aus einer Datei wiederherstellen, gehen Sie folgendermaßen vor, und sehen Sie sich [Erstellen einer Einstellungskategorie](../extensibility/creating-a-settings-category.md).  
  
 Die MPF stellt zwei Klassen zum Optionsseiten im Menü Extras, erstellen die <xref:Microsoft.VisualStudio.Shell.Package> Klasse und die <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse. Erstellen Sie ein VSPackage, um einen Container für diese Seiten zu gewährleisten, indem Sie Unterklassen der\-Klasse. Sie erstellen jedes Optionsseite "Extras" von der DialogPage\-Klasse ableiten.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen eine Rasterseite des Tools\-Optionen  
 In diesem Abschnitt erstellen Sie eine einfache Tooloptionen Eigenschaftenraster. Sie verwenden dieses Raster anzeigen und ändern Sie den Wert einer Eigenschaft.  
  
#### So erstellen das VSIX\-Projekt und fügen ein VSPackage  
  
1.  Alle Visual Studio\-Erweiterung beginnt mit der ein VSIX\-Bereitstellungsprojekt, das die Ressourcen für die Erweiterung enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX\-Projekt namens `MyToolsOptionsExtension`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Fügen Sie ein VSPackage hinzu, indem Sie ein Visual Studio\-Paket\-Elementvorlage mit dem Namen `MyToolsOptionsPackage`. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Dialogfeld Neues Element hinzufügen**, zur **Visual C\#\-Elemente \/ Erweiterbarkeit** und wählen Sie **Visual Studio\-Paket**. In den **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen `MyToolsOptionsPackage.cs`. Weitere Informationen dazu, wie Sie ein VSPackage erstellen, finden Sie unter [Erstellen eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### Erstellen Sie im Eigenschaftenraster Tooloptionen  
  
1.  Öffnen Sie die Datei MyToolsOptionsPackage im Code\-Editor.  
  
2.  Fügen Sie die folgende using\-Anweisung.  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  Deklarieren Sie eine OptionPageGrid\-Klasse und leiten Sie ihn von <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Anwenden einer <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der VSPackage\-Klasse der Klasse ein Optionskategorie und der Name der Seite Optionen für die OptionPageGrid zuweisen. Das Ergebnis sollte wie folgt aussehen:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Hinzufügen einer `OptionInteger` Eigenschaft, um die `OptionPageGrid` Klasse.  
  
    -   Anwenden einer <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> die Eigenschaft eine Eigenschaft Raster Kategorie zuweisen.  
  
    -   Anwenden einer <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> der Eigenschaft einen Namen zuzuweisen.  
  
    -   Anwenden einer <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> eine Beschreibung der Eigenschaft zugewiesen.  
  
    ```c#  
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
    >  Die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage> unterstützt Eigenschaften, die entsprechenden Konverter haben oder die Strukturen oder Arrays, die in Eigenschaften erweitert werden können, die entsprechenden Konverter verfügen. Eine Liste der Konverter finden Sie in der <xref:System.ComponentModel> Namespace.  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
7.  In der experimentellen Instanz von Visual Studio auf die **Tools** klicken Sie im Menü **Optionen**.  
  
     Im linken Bereich sollte **Meine Kategorie**. \(Optionen Kategorien werden in alphabetischer Reihenfolge aufgeführt, sodass sie über in der Mitte unten in der Liste angezeigt werden soll.\) Öffnen Sie **Meine Kategorie** und klicken Sie dann auf **Meine Rasterseite**. Das Raster wird im rechten Bereich angezeigt. Die Eigenschaftskategorie ist **Meine Optionen**, und der Eigenschaftenname ist **Meine Integer\-Option**. Die Beschreibung der Eigenschaft **Meine Integer\-Option**, wird am unteren Rand des Bereichs. Ändern Sie den Wert der ursprüngliche Wert von 256 auf etwas anderes. Klicken Sie auf **OK**, und öffnen Sie Sie erneut **Meine Rasterseite**. Sie können sehen, dass der neue Wert beibehalten.  
  
     Die Optionsseite steht auch über Visual Studio\-Schnellstart. Geben Sie im Fenster Schnellstartleiste in der oberen rechten Ecke der IDE **Meine Kategorie** sehen Sie **Meine Kategorie, und wählen Sie My Rasterseite** in der Dropdownliste aufgeführt.  
  
## Erstellen eines Tools Optionen benutzerdefinierten Seite  
 In diesem Abschnitt erstellen Sie eine Tools\-Optionen\-Seite mit einer benutzerdefinierten Benutzeroberfläche. Sie können diese Seite verwenden, um anzuzeigen, und ändern Sie den Wert einer Eigenschaft.  
  
1.  Öffnen Sie die Datei MyToolsOptionsPackage im Code\-Editor.  
  
2.  Fügen Sie die folgende using\-Anweisung.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Hinzufügen einer `OptionPageCustom` Klasse unmittelbar vor der `OptionPageGrid` Klasse. Leiten Sie die neue Klasse von `DialogPage`.  
  
    ```c#  
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
  
4.  Ein GUID\-Attribut hinzufügen. Fügen Sie eine Eigenschaft OptionString hinzu:  
  
    ```c#  
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
  
5.  Wenden Sie eine zweite <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der VSPackage\-Klasse. Dieses Attribut weist der Klasse ein Optionskategorie und der Name der Seite Optionen.  
  
    ```c#  
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
  
6.  Fügen Sie einen neuen **Benutzersteuerelement** mit dem Namen MyUserControl zum Projekt.  
  
7.  Hinzufügen einer **Textfeld** \-Steuerelement auf das Benutzersteuerelement.  
  
     In der **Eigenschaften** in der Symbolleiste des Fensters klicken Sie auf die **Ereignisse** Schaltfläche, und doppelklicken Sie dann auf die **lassen** Ereignis. Der neue Ereignishandler wird im Code MyUserControl.cs angezeigt.  
  
8.  Fügen Sie eine öffentliche `OptionsPage` Feld eine `Initialize` Methode, um die Control\-Klasse und der Ereignishandler zum Festlegen der Wert auf den Inhalt des Textfelds Update:  
  
    ```c#  
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
  
     Die `optionsPage` Feld enthält einen Verweis auf das übergeordnete `OptionPageCustom` Instanz. Die `Initialize` Methode `OptionString` in der **Textfeld**. Der\-Ereignishandler schreibt den aktuellen Wert der der **TextBox** auf der `OptionString` Wenn konzentrieren bewirkt, dass die **TextBox**.  
  
9. Fügen Sie in der Paketdatei Code eine Überschreibung für die `OptionPageCustom.Window` \-Eigenschaft für die OptionPageCustom\-Klasse erstellen, initialisieren und Zurückgeben einer Instanz von `MyUserControl`. Die Klasse sollte jetzt wie folgt aussehen:  
  
    ```c#  
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
  
11. Klicken Sie in der experimentellen Instanz auf **Extras \/ Optionen**.  
  
12. Suchen Sie **Meine Kategorie** und **Meine benutzerdefinierte Seite**.  
  
13. Ändern Sie den Wert der **OptionString**. Klicken Sie auf **OK**, und öffnen Sie Sie erneut **eigene benutzerdefinierte Seite**. Sie können sehen, dass der neue Wert übernommen hat.  
  
## Beim Zugriff auf Optionen.  
 In diesem Abschnitt erhalten Sie den Wert einer Option aus dem VSPackage, die die zugehörige Tools\-Optionen\-Seite hostet. Das gleiche Verfahren kann verwendet werden, um den Wert einer öffentlichen Eigenschaft abzurufen.  
  
1.  Fügen Sie in der Codedatei Paket eine öffentliche Eigenschaft namens **OptionInteger** an der **MyToolsOptionsPackage** Klasse.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Dieser Code ruft <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> Erstellen oder Abrufen einer `OptionPageGrid` Instanz.`OptionPageGrid` Aufrufe <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> seine Optionen laden, die öffentlichen Eigenschaften sind.  
  
2.  Jetzt fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **MyToolsOptionsCommand** den Wert angezeigt. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Befehl benutzerdefinierte**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **MyToolsOptionsCommand.cs**.  
  
3.  Ersetzen Sie den Hauptteil des Befehls in der Datei MyToolsOptionsCommand `ShowMessageBox` \-Methode durch Folgendes:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen MyToolsOptionsCommand**.  
  
     Ein Meldungsfeld zeigt den aktuellen Wert des `OptionInteger`.  
  
## Siehe auch  
 [Optionen und Optionen \(Seiten\)](../extensibility/internals/options-and-options-pages.md)