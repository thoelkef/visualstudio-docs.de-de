---
title: Erstellen einer Optionsseite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: "62"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68a3afc0a83d4dba7b7cd46b2b1eba23695a2848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-options-page"></a>Erstellen einer Optionsseite
In dieser exemplarischen Vorgehensweise wird eine einfache Extras/Optionen-Seite, die mit einem Eigenschaftenraster überprüfen und Festlegen von Eigenschaften erstellt.  
  
 Um diese Eigenschaften zu speichern und aus einer Datei wiederherstellen, gehen Sie folgendermaßen vor, und klicken Sie dann finden Sie unter [Erstellen einer Einstellungskategorie](../extensibility/creating-a-settings-category.md).  
  
 Das MPF bietet zwei Klassen, um Sie beim Erstellen von Optionsseiten (Tools), unterstützen die <xref:Microsoft.VisualStudio.Shell.Package> Klasse und die <xref:Microsoft.VisualStudio.Shell.DialogPage> Klasse. Erstellen Sie ein VSPackage zum Bereitstellen von eines Containers für diese Seiten durch Erstellen von Unterklassen für die Paket-Klasse. Erstellen Sie jede Optionsseite "Extras" durch Ableiten von der DialogPage-Klasse.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Erstellen einer Extras Optionen-Rasterseite  
 In diesem Abschnitt erstellen Sie eine einfache Extras Optionen-Eigenschaftenraster. Sie verwenden dieses Raster, um anzuzeigen, und ändern Sie den Wert einer Eigenschaft.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Erstellen das VSIX-Projekt und fügen eine VSPackage  
  
1.  Alle Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellung-Projekt bzw. die die Erweiterung Ressourcen enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `MyToolsOptionsExtension`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Fügen Sie ein VSPackage hinzu, indem Sie ein Paket für Visual Studio-Elementvorlage mit dem Namen `MyToolsOptionsPackage`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **Dialogfeld Neues Element hinzufügen**, wechseln Sie zu **Visual C#-Elemente / Erweiterbarkeit** , und wählen Sie **Visual Studio-Paket**. In der **Namen** Feld am unteren Rand der Dialog, ändern Sie den Dateinamen an `MyToolsOptionsPackage.cs`. Weitere Informationen dazu, wie Sie ein VSPackage erstellen, finden Sie unter [erstellen eine Erweiterung mit einem VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>So erstellen das Eigenschaftenraster Extras – Optionen  
  
1.  Öffnen Sie die MyToolsOptionsPackage-Datei im Code-Editor.  
  
2.  Fügen Sie die folgende Anweisung verwenden.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Deklarieren Sie eine Klasse OptionPageGrid und leiten sie von <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Anwenden einer <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der VSPackage-Klasse, die Klasse eine Kategorie mit Optionen und der Name auf der Seite "Optionen" für die OptionPageGrid zuweisen. Das Ergebnis sollte wie folgt aussehen:  
  
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
  
    -   Anwenden einer <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> , die Eigenschaft eine Raster Eigenschaftenkategorie zugewiesen.  
  
    -   Anwenden einer <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> für die Eigenschaft einen Namen zuzuweisen.  
  
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
    >  Die standardmäßige Implementierung des <xref:Microsoft.VisualStudio.Shell.DialogPage> unterstützt Eigenschaften, die über entsprechende Typkonverter oder die Strukturen oder Arrays, die in Eigenschaften erweitert werden können, die entsprechenden Typkonverter aufweisen. Eine Liste der Einsatz von Typkonvertern, finden Sie unter der <xref:System.ComponentModel> Namespace.  
  
6.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
7.  In der experimentellen Instanz von Visual Studio auf die **Tools** klicken Sie im Menü **Optionen**.  
  
     Im linken Bereich sehen Sie **Meine Kategorie**. (Optionen Kategorien sind in alphabetischer Reihenfolge aufgelistet, damit es zur während des laufenden Vorgangs in der Liste angezeigt werden soll.) Open **Meine Kategorie** , und klicken Sie dann auf **Meine Rasterseite**. Dem Raster der Sortieroptionen wird im rechten Bereich angezeigt. Die Eigenschaftskategorie ist **Meine Optionen**, und der Eigenschaftenname ist **Meine Integer-Option**. Die Beschreibung der Eigenschaft **Integer-Option**, wird am unteren Rand des Bereichs angezeigt. Ändern Sie den Wert von ihrem ursprünglichen Wert von 256 etwas anderes an. Klicken Sie auf **OK**, und klicken Sie dann erneut öffnen **Meine Rasterseite**. Sie können sehen, dass der neue Wert erhalten bleibt.  
  
     Die Seite "Optionen" ist auch über die Visual Studio-Schnellstart verfügbar. Geben Sie in das Fenster "Schnellstart" in der oberen rechten Ecke der IDE, **Meine Kategorie** und sehen Sie **Meine Kategorie -> Meine Rasterseite** in der Dropdownliste aufgeführt.  
  
## <a name="creating-a-tools-options-custom-page"></a>Erstellen einer Extras Optionen benutzerdefinierten Seite  
 In diesem Abschnitt erstellen Sie eine Seite "Extras – Optionen" mit einer benutzerdefinierten Benutzeroberfläche. Sie können diese Seite zum Anzeigen und ändern Sie den Wert einer Eigenschaft verwenden.  
  
1.  Öffnen Sie die MyToolsOptionsPackage-Datei im Code-Editor.  
  
2.  Fügen Sie die folgende Anweisung verwenden.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Hinzufügen einer `OptionPageCustom` Klasse, kurz vor dem Ausführen der `OptionPageGrid` Klasse. Leiten Sie die neue Klasse von `DialogPage`.  
  
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
  
4.  Fügen Sie ein GUID-Attribut hinzu. Fügen Sie eine Eigenschaft OptionString hinzu:  
  
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
  
5.  Anwenden einer zweiten <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> der VSPackage-Klasse. Dieses Attribut weist der Klasse, eine Kategorie mit Optionen und die Optionen Seitennamen.  
  
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
  
6.  Fügen Sie einen neuen **Benutzersteuerelement** MyUserControl dem Projekt benannt.  
  
7.  Hinzufügen einer **Textfeld** Steuerelement auf das Benutzersteuerelement.  
  
     In der **Eigenschaften** klicken Sie im Fenster auf der Symbolleiste auf die **Ereignisse** aus, und doppelklicken Sie dann auf die **lassen** Ereignis. Die neuen Ereignishandler wird im Code MyUserControl.cs angezeigt.  
  
8.  Fügen Sie einen öffentlichen `OptionsPage` Feld, eine `Initialize` Methode, um der Steuerelementklasse und der Ereignishandler die Option-Wert auf den Inhalt des Textfelds, das Update:  
  
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
  
     Die `optionsPage` Feld enthält einen Verweis auf das übergeordnete Element `OptionPageCustom` Instanz. Die `Initialize` Methode zeigt `OptionString` in der **Textfeld**. Der Ereignishandler schreibt den aktuellen Wert der die **Textfeld** auf die `OptionString` Wenn konzentrieren bewirkt, dass die **Textfeld**.  
  
9. Fügen Sie in der Paket-Codedatei eine Außerkraftsetzung für die `OptionPageCustom.Window` Eigenschaft, um die OptionPageCustom-Klasse erstellen, initialisieren und Zurückgeben einer Instanz von `MyUserControl`. Die Klasse sollte jetzt wie folgt aussehen:  
  
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
  
11. Klicken Sie in der experimentellen Instanz auf **Extras / Optionen**.  
  
12. Suchen **meiner Kategorie** und dann **Meine benutzerdefinierte Seite**.  
  
13. Ändern Sie den Wert der **OptionString**. Klicken Sie auf **OK**, und klicken Sie dann erneut öffnen **eigene Seite "Benutzerdefiniert"**. Sie können sehen, dass der neue Wert persistent gespeichert wurde.  
  
## <a name="accessing-options"></a>Zugreifen auf Optionen  
 In diesem Abschnitt erhalten Sie den Wert einer Option, aus dem VSPackage, die der zugeordneten Seite "Extras – Optionen" hostet. Das gleiche Verfahren kann verwendet werden, um den Wert für jede öffentliche Eigenschaft abzurufen.  
  
1.  Fügen Sie in der Paket-Codedatei eine öffentliche Eigenschaft mit dem Namen **OptionInteger** auf die **MyToolsOptionsPackage** Klasse.  
  
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
  
     Dieser Code ruft <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> zu erstellen oder Abrufen einer `OptionPageGrid` Instanz. `OptionPageGrid`Aufrufe <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> , dessen Optionen laden, wodurch die öffentlichen Eigenschaften sind.  
  
2.  Fügen Sie jetzt eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **MyToolsOptionsCommand** den Wert anzuzeigen. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Befehl**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **MyToolsOptionsCommand.cs**.  
  
3.  Ersetzen Sie den Text des Befehls in der Datei MyToolsOptionsCommand `ShowMessageBox` -Methode durch Folgendes:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
5.  In der experimentellen Instanz auf dem **Tools** Menü klicken Sie auf **aufrufen MyToolsOptionsCommand**.  
  
     Ein Meldungsfeld zeigt den aktuellen Wert des `OptionInteger`.  
  
## <a name="see-also"></a>Siehe auch  
 [Optionen und Optionsseiten](../extensibility/internals/options-and-options-pages.md)