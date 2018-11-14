---
title: Erstellen einer Optionsseite | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b9d61b4a57e0255577fdb0621dafd4263fc127c
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607769"
---
# <a name="create-an-options-page"></a>Erstellen einer Optionsseite
In dieser exemplarischen Vorgehensweise erstellt eine einfache Extras/Optionen-Seite, die ein Eigenschaftenraster zum Überprüfen und Festlegen von Eigenschaften verwendet.  
  
 Um diese Eigenschaften zu speichern und aus einer Datei wiederherstellen, gehen Sie folgendermaßen vor, und klicken Sie dann finden Sie unter [erstellen eine Einstellungskategorie](../extensibility/creating-a-settings-category.md).  
  
 Das MPF bietet zwei Klassen zum Erstellen von Optionsseiten im Menü Extras, stehen Ihnen die <xref:Microsoft.VisualStudio.Shell.Package> Klasse und die <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse. Sie erstellen eine VSPackage, um einen Container für diese Seiten zu ermöglichen, indem Unterklassen der `Package` Klasse. Erstellen Sie jede Optionsseite "Tools" durch Ableiten von der `DialogPage` Klasse.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-tools-options-grid-page"></a>Erstellen Sie eine Rasterseite Extras – Optionen  
 In diesem Abschnitt erstellen Sie ein einfaches Extras/Optionen Eigenschaftenraster. Sie können dieses Raster verwenden, um anzuzeigen, und ändern Sie den Wert einer Eigenschaft.  
  
### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Erstellen das VSIX-Projekt und Hinzufügen von einem VSPackage  
  
1. Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Bereitstellung-Projekt, das die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `MyToolsOptionsExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual C#-** > **Erweiterbarkeit**.  
  
2. Fügen Sie eine VSPackage, indem ein Visual Studio-Paket-Elementvorlage, die mit dem Namen hinzufügen `MyToolsOptionsPackage`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **Dialogfeld "Neues Element hinzufügen"**, wechseln Sie zu **Visual c#-Elemente** > **Erweiterbarkeit** , und wählen Sie **Visual Studio-Paket**. In der **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen an `MyToolsOptionsPackage.cs`. Weitere Informationen dazu, wie Sie ein VSPackage zu erstellen, finden Sie unter [erstellen Sie eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
### <a name="to-create-the-tools-options-property-grid"></a>Um das Eigenschaftenraster Extras/Optionen zu erstellen.  
  
1.  Öffnen der *MyToolsOptionsPackage* Datei im Code-Editor.  
  
2.  Fügen Sie die folgenden using-Anweisung.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Deklarieren Sie eine `OptionPageGrid` Klasse und leiten sie von <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Anwenden einer <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> auf die `VSPackage` Klasse, um die Klasse eine Kategorie mit Optionen und der Name der Optionen-Seite für die OptionPageGrid zuweisen. Das Ergebnis sollte wie folgt aussehen:  
  
    ```csharp  
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
  
    -   Anwenden einer <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> , auf die Eigenschaft einen Namen zuzuweisen.  
  
    -   Anwenden einer <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> eine Beschreibung der Eigenschaft zugewiesen.  
  
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
    >  Die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage> unterstützt Eigenschaften, die entsprechenden Konverter haben oder die Strukturen oder Arrays, die in Eigenschaften erweitert werden können, die entsprechenden Typkonverter aufweisen. Eine Liste der Konverter, finden Sie unter den <xref:System.ComponentModel> Namespace.  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
7.  In der experimentellen Instanz von Visual Studio auf die **Tools** klicken Sie im Menü **Optionen**.  
  
     Im linken Bereich sollte **My Category**. (Optionen Kategorien werden in alphabetischer Reihenfolge aufgeführt, sodass sie über während des laufenden Vorgangs in der Liste angezeigt werden soll.) Open **My Category** , und klicken Sie dann auf **Meine Rasterseite**. Das Raster wird im rechten Bereich angezeigt. Die Eigenschaftskategorie ist **Meine Optionen**, und der Eigenschaftenname ist **Meine ganze Zahl Option**. Die Beschreibung der Eigenschaft **Meine ganze Zahl Option**, wird am unteren Rand des Bereichs. Ändern Sie den Wert der ursprüngliche Wert von 256 auf etwas anderes. Klicken Sie auf **OK**, und klicken Sie dann erneut öffnen **Meine Rasterseite**. Sie können sehen, dass der neue Wert beibehalten.  
  
     Ihre Seite "Optionen" ist auch über Visual Studio-Schnellstarts verfügbar. Geben Sie in das Fenster "Schnellstart" in der oberen rechten Ecke der IDE, **My Category** und Sie sehen **My Category -> Meine Rasterseite** in der Dropdownliste aufgeführt.  
  
## <a name="create-a-tools-options-custom-page"></a>Erstellen einer benutzerdefinierten Tools-Optionen-Seite  
 In diesem Abschnitt erstellen Sie eine Seite "Extras/Optionen", mit einer benutzerdefinierten Benutzeroberfläche. Sie können diese Seite verwenden, um anzuzeigen, und ändern Sie den Wert einer Eigenschaft.  
  
1.  Öffnen der *MyToolsOptionsPackage* Datei im Code-Editor.  
  
2.  Fügen Sie die folgenden using-Anweisung.  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Hinzufügen einer `OptionPageCustom` Klasse, kurz bevor die `OptionPageGrid` Klasse. Leiten Sie die neue Klasse von `DialogPage`.  
  
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
  
4.  Fügen Sie ein GUID-Attribut hinzu. Fügen Sie eine OptionString-Eigenschaft hinzu:  
  
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
  
5.  Anwenden eine Sekunde <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der VSPackage-Klasse. Dieses Attribut weist der Klasse, eine Kategorie mit Optionen und einen Namen für Optionen-Seite.  
  
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
  
6.  Fügen Sie einen neuen **Benutzersteuerelement** mit dem Namen MyUserControl zum Projekt.  
  
7.  Hinzufügen einer **Textfeld** Steuerelement auf das Benutzersteuerelement.  
  
     In der **Eigenschaften** Fenster auf der Symbolleiste klicken Sie auf die **Ereignisse** Schaltfläche, und doppelklicken Sie dann auf die **lassen** Ereignis. Der neue Ereignishandler wird angezeigt, der *MyUserControl.cs* Code.  
  
8.  Hinzufügen eine öffentlichen `OptionsPage` Feld eine `Initialize` Methode zum Control-Klasse, und aktualisieren Sie der Ereignishandler zum Festlegen der Option-Wert auf den Inhalt des Textfelds:  
  
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
  
     Die `optionsPage` Feld enthält einen Verweis auf das übergeordnete Element `OptionPageCustom` Instanz. Die `Initialize` Methode zeigt `OptionString` in die **Textfeld**. Der Ereignishandler schreibt den aktuellen Wert des der **Textfeld** auf die `OptionString` Wenn konzentrieren / / Blätter der **Textfeld**.  
  
9. In der Paket-Codedatei, fügen Sie eine Außerkraftsetzung für die `OptionPageCustom.Window` Eigenschaft, um die `OptionPageCustom` Klasse zu erstellen, initialisieren und zurückgeben eine Instanz von `MyUserControl`. Die Klasse sollte jetzt wie folgt aussehen:  
  
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
  
11. Klicken Sie in der experimentellen Instanz auf **Tools** > **Optionen**.  
  
12. Suchen **Meine Kategorie** und dann **meiner Seite**.  
  
13. Ändern Sie den Wert der **OptionString**. Klicken Sie auf **OK**, und klicken Sie dann erneut öffnen **Meine benutzerdefinierte Seite**. Sie können sehen, dass der neue Wert persistent gespeichert wurde.  
  
## <a name="access-options"></a>Access-Optionen  
 In diesem Abschnitt erhalten Sie den Wert einer Option aus dem VSPackage, die die zugeordnete Tooloptionen-Seite hostet. Das gleiche Verfahren kann verwendet werden, um den Wert, der eine beliebige öffentliche Eigenschaft abzurufen.  
  
1.  Fügen Sie in der Paket-Codedatei, die eine öffentliche Eigenschaft namens **OptionInteger** auf die **MyToolsOptionsPackage** Klasse.  
  
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
  
     Dieser Code ruft <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> zu erstellen oder Abrufen einer `OptionPageGrid` Instanz. `OptionPageGrid` Aufrufe <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> zu diesen Optionen laden, die öffentlichen Eigenschaften sind.  
  
2.  Fügen Sie jetzt eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **MyToolsOptionsCommand** zur Anzeige des Werts. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an *MyToolsOptionsCommand.cs*.  
  
3.  In der *MyToolsOptionsCommand* Datei, ersetzen Sie den Text des Befehls der `ShowMessageBox` -Methode durch Folgendes:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  In der experimentellen Instanz auf die **Tools** Menü klicken Sie auf **aufrufen MyToolsOptionsCommand**.  
  
     Ein Meldungsfeld angezeigt, den aktuellen Wert der `OptionInteger`.  
  
## <a name="see-also"></a>Siehe auch  
 [Optionen und Optionsseiten](../extensibility/internals/options-and-options-pages.md)
