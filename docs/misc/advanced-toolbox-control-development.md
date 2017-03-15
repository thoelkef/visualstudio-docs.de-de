---
title: "Erweiterte Toolbox-Steuerelemententwicklung | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolbox [Visual Studio SDK], Hinzufügen von Elementen mithilfe von MPF"
ms.assetid: d22479a8-6d95-400c-a115-f46d10c10d2f
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# Erweiterte Toolbox-Steuerelemententwicklung
> [!NOTE]
>  Es wird empfohlen, benutzerdefinierte Steuerelement der Toolbox hinzufügen, die Toolbox\-Steuerelementvorlagen zu verwenden, die mit dem Visual Studio 10 SDK enthalten sind.  In diesem Thema wird aus Gründen der Abwärtskompatibilität und für das Hinzufügen von vorhandenen Steuerelementen zur Toolbox und für erweiterte steuer Toolbox die Entwicklung beibehalten.  
>   
>  Weitere Informationen zum Erstellen von Toolbox Steuerelemente, indem Sie die Vorlagen verwenden, finden Sie unter [Gewusst wie: Erstellen eines Toolbox\-Steuerelements, das Windows Forms verwendet](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) und [Erstellen ein WPF\-Toolbox\-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 VSPackage auf das verwaltete Paketframework kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Funktionen erweitern, indem Sie der Toolbox Steuerelemente, die auf Objekte hinzufügen, die von <xref:System.Drawing.Design.ToolboxItem>\-Objekten abgeleitet sind.  Jedes <xref:System.Drawing.Design.ToolboxItem> wird von einem Objekt implementiert, das von <xref:System.ComponentModel.Component>abgeleitet ist.  
  
## Toolboxelement\-Anbieter VSPackage  
 VSPackage auf das verwaltete Paketframework muss als Anbieter steuer Toolbox von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Attribute und Handle Toolbox\-verknüpfte Ereignisse registrieren.  
  
#### So konfigurieren Toolboxelement\-Anbieter als VSPackage  
  
1.  Erstellen Sie eine Instanz <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> , das auf die Klasse angewendet wird, die <xref:Microsoft.VisualStudio.Shell.Package>implementiert.  Beispiele:  
  
    ```vb#  
    Namespace Vsip.LoadToolboxMembers   
        <ProvideToolboxItems(14)> _   
        <DefaultRegistryRoot("Software\Microsoft\VisualStudio\8.0")> _   
        <InstalledProductRegistration(False, "#100", "#102", "1.0", IconResourceID := 400)> _   
        <ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)> _   
        <ProvideMenuResource(1000, 1)> _   
        <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
        Public Class LoadToolboxMembers   
            Inherits Package   
        End Class   
    End Namespace  
    ```  
  
    ```c#  
    namespace Vsip.LoadToolboxMembers {  
        [ProvideToolboxItems(14)]  
        [DefaultRegistryRoot("Software\\Microsoft\\VisualStudio\\8.0")]  
        [InstalledProductRegistration(false, "#100", "#102", "1.0", IconResourceID = 400)]  
        [ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)]  
        [ProvideMenuResource(1000, 1)]  
        [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
        public class LoadToolboxMembers : Package {  
    ```  
  
    > [!NOTE]
    >  Der Konstruktor für <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> nimmt eine ganzzahlige Versionsnummer als Argument.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Versionsnummer dieser Umgebung verwendet, um zu bestimmen, ob ein VSPackage, das <xref:System.Drawing.Design.ToolboxItem>\-Objekte bereitstellt, neu geladen werden muss oder wenn zwischengespeicherte Informationen über die Toolbox verwendet werden können.  Um das Laden von VSPackages zu gewährleisten, wenn Sie <xref:System.Drawing.Design.ToolboxItem> bereitstellen das in der Entwicklungsphase befindet, inkrementieren Sie immer diese Version nach einer beliebigen Änderung.  
  
2.  Wenn die <xref:System.Drawing.Design.ToolboxItem>\-Objekte nichtstandardisierte Toolbox\-Zwischenablageformate angeben, muss eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> auf die Klasse angewendet werden, die das <xref:Microsoft.VisualStudio.Shell.Package>\-Objekt für jedes Zwischenablageformat implementiert, das von der <xref:System.Drawing.Design.ToolboxItem>\-Objekten unterstützt wird, die einem VSPackage bereitstellt.  
  
     Weitere Informationen zu unterstützten Toolbox\-Zwischenablageformate finden Sie unter [Erweitern der Toolbox](../misc/extending-the-toolbox.md).  
  
    > [!NOTE]
    >  Wenn ein VSPackage angibt, dass alle <xref:System.Drawing.Design.ToolboxItem>\-Objekte mit nicht standardmäßigen Zwischenablageformaten erhält, nimmt die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung an, dass nur diejenigen Formate, die von den Instanzen <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> VSPackages zu einer angewendeten<xref:Microsoft.VisualStudio.Shell.Package>\-Klassenimplementierung angegeben werden, durch ein VSPackage unterstützt werden.  Wenn ein VSPackage die standardmäßige Zwischenablageformate sowie ein nichtstandardisiertes Format unterstützen muss, muss er eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> sowie das Standardformat aller nichtstandardisierte Format anwenden.  
  
3.  Wenn ein VSPackage die dynamische Konfiguration von <xref:System.Drawing.Design.ToolboxItem>bereitstellt, muss sie:  
  
    1.  Wenden Sie eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> erstellte mit <xref:System.Type> , dem das Paket verwendet, um die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle zu implementieren.  
  
    2.  Auf einem `public`\-Klassen unabhängige von VSPackages <xref:Microsoft.VisualStudio.Shell.Package>, muss ein VSPackage die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle implementieren.  
  
         Eine Instanz <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> muss auf die Klasse angewendet werden, die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>, wobei eine Zeichenfolge implementiert, die Auswahlkriterien \(Filter\) enthält als Argument an den Konstruktor der <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>\-Instanz.  
  
 Weitere Informationen dazu, wie Sie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung, dass ein VSPackage Toolbox Steuerelemente bereitstellt, finden Sie unter [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)benachrichtigt.  
  
 Ein Beispiel, veranschaulichend, wie Sie möglicherweise <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> Unterstützung implementiert, finden Sie unter [Exemplarische Vorgehensweise: Dynamisches Anpassen der Konfiguration von Toolboxelementen](../misc/walkthrough-customizing-toolbox-item-configuration-dynamically.md).  
  
1.  VSPackages das <xref:System.Drawing.Design.ToolboxItem> bereitstellt, muss <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignisse behandeln.  
  
    1.  Klassenhandler implementieren und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> für die <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignisse:  
  
        ```vb#  
        Private Sub OnToolboxUpgraded(ByVal sender As Object, ByVal e As EventArgs)   
            OnToolboxInitialized(send, e)   
        End Sub   
        Private Sub OnToolboxInitialized(ByVal sender As Object, ByVal e As EventArgs)   
            'Make sure all toolbox items are added.   
        End Sub  
        ```  
  
        ```c#  
        private void OnToolboxUpgraded(object sender, EventArgs e) {  
            OnToolboxInitialized(send,e);  
        }  
        private void OnToolboxInitialized(object sender, EventArgs e) {  
            //Make sure all toolbox items are added.  
        }  
        ```  
  
    2.  Abonnieren Sie <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignissen.  
  
         Dies ist in der <xref:Microsoft.VisualStudio.Shell.Package><xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>\-Methode Implementierung normalerweise durchgeführt:  
  
        ```vb#  
        Protected Overloads Overrides Sub Initialize()   
            AddHandler ToolboxInitialized, AddressOf OnToolboxInitialized   
            AddHandler ToolboxUpgraded, AddressOf OnToolboxUpgraded   
        End Sub  
        ```  
  
        ```c#  
        protected override void Initialize() {  
            ToolboxInitialized += new EventHandler(OnToolboxInitialized);  
            ToolboxUpgraded += new EventHandler(OnToolboxUpgraded);  
        }  
        ```  
  
     Ein Beispiel dafür, wie Handler für <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> und <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded>\-Ereignissen finden Sie unter [Exemplarische Vorgehensweise: Automatisches Laden von Toolboxelementen](../misc/walkthrough-autoloading-toolbox-items.md)implementiert.  
  
## Erstellen Toolbox\-Steuer  
 Die zugrunde liegende Implementierung eines Steuerelements Toolbox aus <xref:System.ComponentModel.Component> abgeleitet werden muss und dem Standard\- oder in einer abgeleiteten Implementierung des <xref:System.Drawing.Design.ToolboxItem>\-Objekt gekapselt werden.  
  
 Die einfachste Möglichkeit, <xref:System.ComponentModel.Component>bereitzustellen abgeleiteten Implementierung der Toolbox die Steuerelemente ist, indem ein Objekt erweitert, das von <xref:System.Windows.Forms.Control>insbesondere die <xref:System.Windows.Forms.UserControl>\-Klasse abgeleitet ist.  
  
#### So erstellen Sie Steuerelemente Toolbox  
  
1.  Verwenden Sie den Projektmappen\-Explorer, **Neues Element hinzufügen** Befehl Toolbox ein Objekt zu erstellen, das <xref:System.Windows.Forms.UserControl>implementiert.  
  
    ```vb#  
    Public Partial Class ToolboxControl1   
        Inherits UserControl   
        Public Sub New()   
            InitializeComponent()   
        End Sub   
        Private Sub button1_Click(ByVal sender As Object, ByVal e As EventArgs)   
            MsgBox("Hello world from" & Me.ToString())   
        End Sub   
  
        Private Sub ToolboxItem1_Load(ByVal sender As Object, ByVal e As EventArgs)   
  
        End Sub   
    End Class  
    ```  
  
    ```c#  
    public partial class ToolboxControl1 : UserControl {  
            public ToolboxControl1() {  
                InitializeComponent();  
            }  
  
            private void button1_Click(object sender, EventArgs e) {  
                MessageBox.Show("Hello world from" + this.ToString());  
            }  
  
            private void ToolboxItem1_Load(object sender, EventArgs e) {  
  
            }  
        }  
    ```  
  
     Weitere Informationen zur Erstellung von Windows Forms\-Steuerelemente und Toolbox Steuerelemente finden Sie unter [Entwickeln benutzerdefinierter Windows Forms\-Steuerelemente mit .NET Framework](../Topic/Developing%20Custom%20Windows%20Forms%20Controls%20with%20the%20.NET%20Framework.md) oder [Exemplarische Vorgehensweise: Automatisches Laden von Toolboxelementen](../misc/walkthrough-autoloading-toolbox-items.md).  
  
2.  \(Optional\) kann eine Anwendung die Möglichkeit, ein benutzerdefiniertes Objekt zu verwenden, das vom <xref:System.Drawing.Design.ToolboxItem>\-Objekt, um dessen Toolbox die Steuerung an **Toolbox**bereitzustellen.  
  
    > [!NOTE]
    >  Jede Klasse, die aus dem <xref:System.Drawing.Design.ToolboxItem>\-Objekt abgeleitet wird, muss eine Instanz <xref:System.SerializableAttribute> verfügen, das zuvor angewendet wird.  
  
     Eine benutzerdefinierte Implementierung, die von <xref:System.Drawing.Design.ToolboxItem> abgeleitet wurde, kann eine Anwendung mithilfe von größeres Steuerelement ermöglicht darüber, wie die Daten <xref:System.Drawing.Design.ToolboxItem> Designermetadaten, verbesserte Behandlung von Unterstützung für nichtstandardisierte Zwischenablageformate und Funktionalität serialisiert wird, kann die Endbenutzer interaktion.  
  
     Im Beispiel werden Benutzer mithilfe eines Dialogfelds aufgefordert, Funktionen auszuwählen:  
  
    ```vb#  
    <ToolboxItemAttribute(GetType(CustomControl))> _   
    <Serializable()> _   
    Class CustomControl   
        Inherits ToolboxItem   
  
        Public Sub New(ByVal type As Type)   
            MyBase.New(GetType(CustomControl))   
        End Sub   
        Public Sub New(ByVal type As Type, ByVal icon As Bitmap)   
            MyBase.New(GetType(SCustomControl))   
            Me.DisplayName = "CustomContorl"   
            Me.Bitmap = icon   
        End Sub   
  
        Private Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)   
            Deserialize(info, context)   
        End Sub   
        Protected Overloads Overrides Function CreateComponentsCore(ByVal host As IDesignerHost) As IComponent()   
            Dim dialog As New CustomControlDialog(host)   
            Dim dialogResult__1 As DialogResult = dialog.ShowDialog()   
            If dialogResult__1 = DialogResult.OK Then   
                Dim component As IComponent = DirectCast(dialog.CustomInstance, IComponent)   
                Dim container As IContainer = host.Container   
                container.Add(component)   
                Return New IComponent() {component}   
            Else   
                Return New IComponent() {}   
            End If   
        End Function   
    End Class  
    ```  
  
    ```c#  
    [ToolboxItemAttribute(typeof(CustomControl))]  
    [Serializable]  
    class CustomControl : ToolboxItem {  
  
        public CustomControl(Type type) : base(typeof(CustomControl)) {}  
            public CustomControl(Type type, Bitmap icon) : base(typeof(SCustomControl)) {  
            this.DisplayName = "CustomContorl";  
            this.Bitmap = icon;  
        }  
  
        private CustomControl(SerializationInfo info, StreamingContext context) {  
            Deserialize(info, context);  
        }  
        protected override IComponent[] CreateComponentsCore(IDesignerHost host) {  
            CustomControlDialog dialog = new CustomControlDialog(host);  
            DialogResult dialogResult = dialog.ShowDialog();  
            if (dialogResult == DialogResult.OK) {  
                IComponent component = (IComponent)dialog.CustomInstance;  
                IContainer container = host.Container;  
                container.Add(component);  
                return new IComponent[] { component };  
            }  
            else {  
                return new IComponent[] {};  
            }  
        }  
    }  
    ```  
  
> [!NOTE]
>  Es ist auch möglich, für eine Klasse vom <xref:System.Drawing.Design.ToolboxItem>\-Objekt, eine eigene unabhängige Implementierung des zugrunde liegenden Steuerelements bereitzustellen abgeleitet ist.  Diese Klasse wird dann zum Erstellen und Angeben aller zugrunde liegenden Komponenten zuständig.  
  
## Explizite Einführung von Toolboxelementen  
 So zeigen Sie anschließend hinzugefügten der Toolbox hinzugefügt werden soll, muss ein Steuerelement in einer Instanz von <xref:System.Drawing.Design.ToolboxItem> oder eines Objekts enthalten sein, das von <xref:System.Drawing.Design.ToolboxItem> abgeleitet wird und mit der **Toolbox** zu <xref:System.Drawing.Design.IToolboxService>\-Schnittstelle.  
  
#### So kapseln und Steuerelemente Toolbox hinzu  
  
1.  Kapseln die <xref:System.ComponentModel.Component> Implementierung in eine Instanz eines <xref:System.Drawing.Design.ToolboxItem>\-Objekts oder <xref:System.Drawing.Design.ToolboxItem>abgeleitete Objekt, indem Sie <xref:System.Drawing.Design.ToolboxItem.Initialize%2A>\-Methode des Objekts mit implementierenden <xref:System.Type?displayProperty=fullName>der Komponente aufrufen:  
  
    ```vb#  
    Dim customItem As New ToolboxItem()   
    If customItem IsNot Nothing Then   
        customItem.Initialize(userControl)   
    End If  
    ```  
  
    ```c#  
    ToolboxItem customItem = new ToolboxItem() ;  
    if (customItem != null) {  
        customItem.Initialize(userControl);  
    }  
    ```  
  
     Im Beispiel oben `userControl` eines Objekts, das von <xref:System.Windows.Forms.UserControl> abgeleitet ist \(eine Instanz des Objekts `ToolboxControl1` oben\), das verwendet wird, um ein neues <xref:System.Drawing.Design.ToolboxItem>zu erstellen.  
  
    > [!NOTE]
    >  Die Standardimplementierung des <xref:System.Drawing.Design.ToolboxItem>\-Konstruktors, der ein <xref:System.Type?displayProperty=fullName>\-Argument akzeptiert \(<xref:System.Drawing.Design.ToolboxItem.%23ctor%28System.Type%29>\-Konstruktor ruft die <xref:System.Drawing.Design.ToolboxItem><xref:System.Drawing.Design.ToolboxItem.Initialize%2A>\-Methode des Objekts aufgerufen.  
  
2.  Verwenden Sie den Toolboxdienst \(<xref:System.Drawing.Design.IToolboxService>\), um das <xref:System.Drawing.Design.ToolboxItem>\-Objekt hinzuzufügen, das von der zugrunde liegenden Steuerelementimplementierung erstellt wird.  
  
     Im folgenden Beispiel wird der Zugriff auf den Toolboxdienst erhalten, werden einige Eigenschaften der <xref:System.Drawing.Design.ToolboxItem>\-Instanz `customItem` festgelegt, und anschließend wird `customItem` zu **Toolbox**hinzugefügt:  
  
    ```vb#  
    Dim toolboxService As IToolboxService = TryCast(GetService(GetType(IToolboxService)), IToolboxService)  
    customItem.Bitmap = New System.Drawing.Bitmap(ToolBoxControl1, "Control1.bmp")  
    customItem.DisplayName = "Custom Item"   
    toolboxService.AddToolboxItem(item, "Custom Tab")  
    ```  
  
    ```c#  
    IToolboxService toolboxService = GetService(typeof(IToolboxService)) as IToolboxService;  
    customItem.Bitmap = new System.Drawing.Bitmap(ToolboxControl1,"Control1.bmp");  
    customItem.DisplayName= "Custom Item";  
    toolboxService.AddToolboxItem(item, "Custom Tab");  
    ```  
  
## Verwenden der Reflektion zum Hinzufügen von Toolbox\-Kontrollen  
 Das Anwenden von Attributen auf die Klasse an, die ein Toolbox die Steuerung implementiert, ermöglicht die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung oder eine [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] basierte Anwendung, Reflektion verwenden, um Steuerelemente **Toolbox**automatisch erkannt und ordnungsgemäß hinzugefügt werden soll.  
  
#### So Reflektion und Attribute in Toolbox Steuerelemente anwenden  
  
1.  Identifizieren Sie alle Objekte, die zum Implementieren der Toolbox die Steuerelemente mit Instanzen von <xref:System.ComponentModel.ToolboxItemAttribute>verwendet werden.  
  
     Der Typ der Instanz von <xref:System.ComponentModel.ToolboxItemAttribute> auf ein Objekt willen bestimmt, ob und wie <xref:System.Drawing.Design.ToolboxItem> von ihm erstellt wird.  
  
    1.  Eine Instanz von <xref:System.ComponentModel.ToolboxItemAttribute> erstellten Anwenden `BOOLEAN` mit einem Wert von `false` auf ein Objekt macht dieses Objekt nicht durch Reflektion zur Toolbox verfügbar.  
  
         Dies kann hilfreich sein, ein Objekt als <xref:System.Windows.Forms.UserControl> von **Toolbox** während der Entwicklung zu suchen.  
  
    2.  Eine Instanz von <xref:System.ComponentModel.ToolboxItemAttribute> erstellten Anwenden `BOOLEAN` mit einem Wert von `true` auf ein Objekt macht, dass das Objekt, das einem der Toolbox durch Reflektion verfügbar ist, und setzt voraus, dass das Objekt der Toolbox mit einem Standardwert <xref:System.Drawing.Design.ToolboxItem>\-Objekts hinzugefügt wird.  
  
    3.  Eine Instanz von <xref:System.ComponentModel.ToolboxItemAttribute> erstellten mit <xref:System.Type> Anwenden eines benutzerdefinierten Objekts, das von <xref:System.Drawing.Design.ToolboxItem> abgeleitetes Objekt bereitstellt, und über Reflektion auf **Toolbox** erfordert, dass das Objekt der Toolbox mit diesem benutzerdefinierten Objekts hinzugefügt wird, das von <xref:System.Drawing.Design.ToolboxItem>abgeleitet ist.  
  
2.  Geben Sie Reflektions \(um die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Mechanismus zur Umgebung die Bitmap\) an, die zum Anzeigen des Steuerelements Toolbox in **Toolbox** zu verwenden, indem Sie eine Instanz von <xref:System.Drawing.ToolboxBitmapAttribute> Implementierung der steuer zur Toolbox hinzufügen.  
  
3.  Falls erforderlich, wenden Sie Instanzen von <xref:System.ComponentModel.ToolboxItemFilterAttribute> zu <xref:System.Drawing.Design.ToolboxItem>\-Objekten, die Reflektion verwenden, um sie für die Verwendung mit Objekten als statisch markiert, die ein übereinstimmendes Attribut verfügen.  
  
     Im folgenden Beispiel verfügt die Implementierung eines Toolbox steuer eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> darauf angewendeten, die dieses Steuerelement in **Toolbox** bereitstellt Arbeitsdokument nur, wenn es sich beim aktuellen Designer <xref:System.Windows.Forms.UserControl>  
  
    ```vb#  
    <ToolboxItemFilter(System.Windows.Forms.UserControl, ToolboxItemFilterType.Require)> _   
    <SerializableAttribute()> _   
    <GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class CustomToolboxItem   
        Inherits ToolboxItem   
    End Class  
    ```  
  
    ```c#  
    [ToolboxItemFilter(System.Windows.Forms.UserControl,ToolboxItemFilterType.Require)]  
    [SerializableAttribute()]  //ToolboxItem implementations much has this attribute.  
    [GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class CustomToolboxItem : ToolboxItem   
    ```  
  
 Es gibt drei grundlegende Verfahren für die Verwendung von Reflektion zum Automatisches Laden von <xref:System.Drawing.Design.ToolboxItem>.  
  
### Verwenden von ToolService\-Funktionalität zum Abrufen von Toolbox\-Kontrollen  
 <xref:System.Drawing.Design.ToolboxService> stellt <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> VSPackages mit den statischen Methoden, die Reflektion verwenden, um Assembly nach allen Typen, die Toolboxelemente unterstützen überprüfen und Elemente für diese Typen zurück.  So zurückgegeben werden soll, muss ein Toolboxelement:  
  
-   Er muss öffentlich sein.  
  
-   Implementieren Sie die <xref:System.ComponentModel.IComponent>\-Klasse.  
  
-   Er darf nicht abstrakt sein.  
  
-   Haben Sie <xref:System.ComponentModel.ToolboxItemAttribute> in seinem Typ.  
  
-   <xref:System.ComponentModel.ToolboxItemAttribute> nicht festgelegt haben `false` in seinem Typ  
  
-   Er darf keine generischen Parameter enthalten.  
  
##### So rufen Sie diese Liste  
  
1.  Erstellen Sie eine Instanz von <xref:System.Reflection.Assembly> die Assembly ansprechend, die für <xref:System.Drawing.Design.ToolboxItem>\-Objekte überprüft werden soll.  
  
    > [!NOTE]
    >  Zum Abrufen einer Instanz von <xref:System.Reflection.Assembly> für die aktuelle Assembly, verwenden Sie die statische Methode <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.  
  
2.  <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>Aufruf eines <xref:System.Collections.ICollection>\-Objekt zurückgibt, das eine Liste der entsprechenden Objekte enthält.  
  
    > [!NOTE]
    >  Wenn ein Objekt in der zurückgegebenen <xref:System.Collections.ICollection> verfügt, die eine gültige Instanz von <xref:System.Drawing.ToolboxBitmapAttribute> zu ihrer Implementierung, die <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>\-Methode festgelegt wird <xref:System.Drawing.Design.ToolboxItem.Bitmap%2A>\-Eigenschaft des <xref:System.Drawing.Design.ToolboxItem> .  
  
3.  Verwenden Sie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> abzurufen, um Zugriff auf <xref:System.Drawing.Design.IToolboxService>, und legen Sie seine <xref:System.Drawing.Design.IToolboxService.AddToolboxItem%2A>\-Methode, um Elemente aus dem zurückgegebenen <xref:System.Collections.ICollection>\-Objekt zur Toolbox hinzugefügt werden soll.  
  
     Der Code unter der Abfragen und die ausgeführte Anwendung ruft eine Liste aller seiner <xref:System.Drawing.Design.ToolboxItem>\-Objekte und lädt sie.  Ein Beispiel, das die Ausführung von Code in veranschaulichend finden Sie in der `Initialization`\-Methode in [Exemplarische Vorgehensweise: Dynamisches Anpassen der Konfiguration von Toolboxelementen](../misc/walkthrough-customizing-toolbox-item-configuration-dynamically.md).  
  
    ```vb#  
    Protected ToolboxItemList As ICollection = Nothing  
    ToolboxItemList = ToolboxService.GetToolboxItems(Assembly.GetExecutingAssembly(), "")  
    If ToolboxItemList Is Nothing Then   
        Throw New ApplicationException("Unable to generate a toolbox Items listing for " & [GetType]().FullName)   
    End If   
    Dim toolboxService As IToolboxService = TryCast(GetService(GetType(IToolboxService)), IToolboxService)   
    For Each itemFromList As ToolboxItem In ToolboxItemList   
        toolboxService.AddToolboxItem(itemFromList, CategoryTab)   
    Next  
    ```  
  
    ```c#  
    protected ICollection ToolboxItemList = null;  
    ToolboxItemList = ToolboxService.GetToolboxItems(Assembly.GetExecutingAssembly(), "");  
    if (ToolboxItemList == null){  
        throw new ApplicationException("Unable to generate a toolbox Items listing for "  
    + GetType().FullName);  
    }  
    IToolboxService toolboxService = GetService(typeof(IToolboxService)) as IToolboxService;  
    foreach (ToolboxItem itemFromList in ToolboxItemList){  
        toolboxService.AddToolboxItem(itemFromList, CategoryTab);  
    }  
    ```  
  
### Verwenden von eingebetteten Text\-Betriebsmittel, um Toolbox\-Kontrollen automatisch zu laden  
 Eine Text Ressource in einer Assembly, die eine richtig formatierte Liste der Toolbox die Steuerelemente enthält, kann durch <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> verwendet werden, um ein Toolbox die Steuerung automatisch geladen werden sollen, wenn sie richtig formatiert ist.  
  
 Eine Text Ressource, die eine Liste von Objekten enthält, muss das Laden einer Assembly verfügbar sein, die zu einem VSPackage zugegriffen werden kann.  
  
##### So fügen Sie Text eine Ressource hinzufügen verfügbar machen und der Assembly  
  
1.  Klicken Sie mit der rechten Maustaste auf das Projekt **Projektmappen\-Explorer**.  
  
2.  Zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** stellen einen Namen und **Textdatei** .  
  
4.  In **Projektmappen\-Explorer**hat der rechten Maustaste auf die neu erstellte Textdatei und die **Buildvorgang**\-Eigenschaft auf Eingebettete Ressource fest.  
  
     Einträge, für das **Toolbox**\-Steuerelement geladen werden kann, muss der Name der implementierenden Klasse den Namen der Assembly, die sie enthält.  
  
     Weitere Informationen über das Format der Toolbox Steuerelemente Einträgen Text der eingebetteten Ressource finden Sie in der <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> Referenzseite.  
  
5.  Installieren Sie einen Suchpfad für Dateien, die die Assemblys enthalten, die Toolbox steuer Objekte.  
  
     <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>, Verzeichnisse der Suche nur im angegebenen Registrierungseintrag HKEY\_CURRENT\_USER \\ Software \\ Microsoft \\ VisualStudio \\ *\<version\>* \\ AssemblyFolders, wo  *\<version\>*  die Versionsnummer der Version von Visual Studio ist \(z. B. 8.0\).  
  
    > [!NOTE]
    >  Der Stammpfad von HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ *\<Version\>*  kann mit einem alternativen Stamm, wenn die Visual Studio\-Shell initialisiert wird oder Verwendung von <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute>überschrieben werden.  Weitere Informationen finden Sie unter [Befehlszeilenoptionen](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
     Ausführliche Informationen über das richtige Format der AssemblyFolder\-Registrierungseinträge finden Sie in der <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> Referenzseite.  
  
6.  Rufen Sie eine Instanz von <xref:System.IO.TextReader.Synchronized%2A> der eingebetteten Ressource Text und Zugreifen auf, wenn Lokalisierungsunterstützung für den angegebenen Kategorienamen, eine Instanz von <xref:System.Resources.ResourceManager>erforderlich ist und diese verwendet wird, um die <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A>\-Methode aufzurufen.  
  
    ```vb#  
    Dim rm As New ResourceManager("TbxCategories", Assembly.GetExecutingAssembly())  
    Dim toolboxStream As Stream = TbxItemProvider.[GetType]().Assembly.GetManifestResourceStream("ToolboxItems.txt")  
    If toolboxStream IsNot Nothing Then   
        Using reader As TextReader = New StreamReader(toolboxStream)   
            ParseToolboxResource(reader, rm)   
        End Using   
    End If  
    ```  
  
    ```c#  
    ResourceManager rm = new ResourceManager("TbxCategories", Assembly.GetExecutingAssembly());  
    Stream toolboxStream = TbxItemProvider.GetType().Assembly.GetManifestResourceStream("ToolboxItems.txt");  
    if (toolboxStream != null) {  
        using (TextReader reader = new StreamReader(toolboxStream)) {  
        ParseToolboxResource(reader, rm);  
    }  
    }  
    ```  
  
     Im Beispiel oben wird eine Liste mit Text in einer eingebetteten Ressource in der Assembly enthalten `TbxItemProvider`\-Klasse enthält die <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> wird zusammen mit den `TbxCategories` Zeichenfolgenressourcen übergeben.  
  
     Die Methode durchsucht alle Dateien in Verzeichnissen, die Assemblys enthalten, die unter dem AssemblyFolders\-Registrierungseintrag für die Toolbox die Steuerelemente angegeben werden, die in der Ressource aufgeführten und lädt sie.  
  
    > [!NOTE]
    >  Wenn ein Toolbox die Steuerung, das durch <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> gefunden wird, verfügt, die eine gültige Instanz von <xref:System.Drawing.ToolboxBitmapAttribute> zu ihrer Implementierung, die festlegt <xref:Microsoft.VisualStudio.Shell.Package.ParseToolboxResource%2A> Bitmap, die verwendet wurde, um die Toolbox die Steuerung anzuzeigen.  
  
### Explizit durch Reflektion, um Toolbox\-Kontrollen automatisch zu laden  
 Wenn es erforderlich ist, Assemblys zu Informationen über die **Toolbox**\-Steuerelemente explizit abzufragen, die sie enthalten, anstatt die Aufgabe zu <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A>delegierend, kann dies geschehen.  
  
##### Um explizit Reflektion verwenden, um Toolbox auf Steuerelemente automatisch laden  
  
1.  Erstellen Sie eine Instanz von <xref:System.Reflection.Assembly>und jede Assembly verweisen, die für <xref:System.Drawing.Design.ToolboxItem>\-Objekte überprüft werden soll.  
  
    > [!NOTE]
    >  Zum Abrufen einer Instanz von <xref:System.Reflection.Assembly> für die aktuelle Assembly, verwenden Sie die statische Methode <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.  
  
2.  Für jede Assembly überprüft werden soll, verwenden Sie die <xref:System.Reflection.Assembly> des Objekts <xref:System.Reflection.Assembly.GetTypes%2A>\-Methode zum Abrufen einer Liste von jedem <xref:System.Type?displayProperty=fullName> in der Assembly.  
  
3.  Stellen Sie sicher, dass der Typ nicht abstrakt ist und die <xref:System.ComponentModel.IComponent>\-Schnittstelle unterstützt \(alle Implementierungen der Toolbox Steuerelemente, mit denen ein <xref:System.Drawing.Design.ToolboxItem>\-Objekt zu instanziieren, müssen diese Schnittstelle implementieren\).  
  
4.  Rufen Sie die Attribute aus <xref:System.Type> und verwenden diese Informationen, um zu bestimmen, ob ein VSPackage das Objekt geladen werden soll.  
  
    > [!NOTE]
    >  Obwohl in den Prinzipal kann ein <xref:System.Drawing.Design.ToolboxItem>\-Objekt aus einer <xref:System.ComponentModel.IComponent>\-Schnittstellenimplementierung ohne eine Instanz von <xref:System.ComponentModel.ToolboxItemAttribute> zu erstellen `false` nicht festgelegt, es empfiehlt es sich, angewendeten nicht.  
  
5.  Verwenden Sie zum Abrufen <xref:System.Type.GetConstructor%2A>\-Konstruktoren für die <xref:System.Drawing.Design.ToolboxItem>\-Objekten, die die Toolbox steuert, erfordert.  
  
6.  Erstellen Sie die <xref:System.Drawing.Design.ToolboxItem>\-Objekte und fügen Sie sie hinzu. **Toolbox**  
  
 Zum Beispiel zu sehen, explizite Verwendung der Reflektion abzurufen und zu illustrieren Steuerelemente Toolbox automatisch zu laden, finden Sie unter `CreateItemList` , das in [Exemplarische Vorgehensweise: Automatisches Laden von Toolboxelementen](../misc/walkthrough-autoloading-toolbox-items.md)beschrieben wird.  
  
## Weitere Toolbox\-Steuer Bereitstellungskonfiguration  
 VSPackage können zusätzliche Kontrolle darüber, wann und wie ein Toolbox die Steuerung durch **Toolbox**, durch die Implementierung von <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>und Verwendung von <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute>angezeigt wird, und <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute>abdecken.  
  
 Das Anwenden von <xref:System.ComponentModel.ToolboxItemFilterAttribute>\-Instanzen einer Klasse stellt nur statisches Steuerelement darüber, ob und wie ein **Toolbox**\-Steuerelement verfügbar ist.  
  
#### Um dynamische Steuerelemente Toolbox Unterstützung für Konfiguration erstellen  
  
1.  Erstellen Sie eine Klasse, die die Schnittstelle als Teil <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> VSPackages implementiert.  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem>\-Schnittstelle darf nicht in derselben Klasse implementiert werden, die eine Implementierung von VSPackages <xref:Microsoft.VisualStudio.Shell.Package>bereitstellt.  
  
2.  Ordnen Sie die Implementierung von <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> mit den Objekten in bestimmten Assembly zu, indem Sie eine Instanz <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> darauf anwenden.  
  
     Das Beispiel stellt den nachfolgenden steuer Toolbox Konfiguration für eine dynamische Assemblys Objekt innerhalb des `Vsip.*`\-Namespace und \- Objekte c$benötigens, dass bestimmte <xref:System.Drawing.Design.ToolboxItem> \- Designern sichtbar nur mit <xref:System.Windows.Forms.UserControl>und andere, die nie <xref:System.Windows.Forms.UserControl>\- Designern sichtbar sind.  
  
    ```vb#  
    <ProvideAssemblyFilterAttribute("Vsip.*, Version=*, Culture=*, PublicKeyToken=*")> _   
    <GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Public NotInheritable Class ToolboxConfig   
        Implements IConfigureToolboxItem   
        Public Sub New()   
        End Sub  
  
        ''' <summary>   
        ''' Adds extra configuration information to this toolbox item.   
        ''' </summary>   
        Public Sub ConfigureToolboxItem(ByVal item As ToolboxItem)   
            If item Is Nothing Then   
                Exit Sub   
            End If   
  
            'hide from .NET Compact Framework on the device designer.   
            Dim newFilter As ToolboxItemFilterAttribute = Nothing   
            If item.TypeName = GetType(ToolboxControl1).ToString() Then   
                newFilter = New ToolboxItemFilterAttribute("System.Windows.Forms.UserControl", ToolboxItemFilterType.Require)   
            ElseIf item.TypeName = GetType(ToolboxControl2).ToString() Then   
  
                newFilter = New ToolboxItemFilterAttribute("System.Windows.Forms.UserControl", ToolboxItemFilterType.Prevent)   
            End If   
            If newFilter IsNot Nothing Then   
                Dim array As New ArrayList()   
                array.Add(newFilter)   
                item.Filter = DirectCast(array.ToArray(GetType(ToolboxItemFilterAttribute)), ToolboxItemFilterAttribute())   
            End If   
        End Sub   
    End Class  
    ```  
  
    ```c#  
    [ProvideAssemblyFilterAttribute("Vsip.*, Version=*, Culture=*, PublicKeyToken=*")]  
        [GuidAttribute("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
        public sealed class ToolboxConfig : IConfigureToolboxItem {  
            public ToolboxConfig() {  
            }  
  
            /// <summary>  
            ///     Adds extra configuration information to this toolbox item.  
            /// </summary>  
            public void ConfigureToolboxItem(ToolboxItem item) {  
                if (item == null)  
                    return;  
  
                //hide from .NET Compact Framework  on the device designer.  
                ToolboxItemFilterAttribute newFilter = null;  
                if (item.TypeName == typeof(ToolboxControl1).ToString()) {  
                    newFilter = new ToolboxItemFilterAttribute("System.Windows.Forms.UserControl",  
                                                          ToolboxItemFilterType.Require);  
                }   
                else if (item.TypeName == typeof(ToolboxControl2).ToString()) {  
  
                    newFilter = new ToolboxItemFilterAttribute("System.Windows.Forms.UserControl",  
                                                          ToolboxItemFilterType.Prevent);  
                }  
                if (newFilter != null) {  
                    ArrayList array = new ArrayList();  
                    array.Add(newFilter);  
                    item.Filter = (ToolboxItemFilterAttribute[])  
                            array.ToArray(typeof(ToolboxItemFilterAttribute));  
                }  
            }  
        }  
    }  
    ```  
  
3.  Registrieren von VSPackages als Bereitstellen einer bestimmten Implementierung von <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> , indem Sie eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> zur Implementierung von VSPackages <xref:Microsoft.VisualStudio.Shell.Package>anwenden.  
  
     Im folgenden Beispiel wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung informieren, dass das Paket, das von `Vsip.ItemConfiguration.ItemConfiguration`\-Klasse implementiert wird, die `Vsip.ItemConfiguration.ToolboxConfiguration` bereitstellt, um dynamisches <xref:System.Drawing.Design.ToolboxItem>zu unterstützen.  
  
    ```vb#  
    <ProvideToolboxItemsAttribute(3)> _   
    <DefaultRegistryRoot("Software\Microsoft\VisualStudio\8.0")> _   
    <InstalledProductRegistration(False, "#100", "#102", "1.0", IconResourceID := 400)> _   
    <ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)> _   
    <ProvideMenuResource(1000, 1)> _   
    <ProvideToolboxItemConfigurationAttribute(GetType(ToolboxConfig))> _   
    <GuidAttribute("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Public Class ItemConfiguration   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideToolboxItemsAttribute(3)]  
    [DefaultRegistryRoot("Software\\Microsoft\\VisualStudio\\8.0")]  
    [InstalledProductRegistration(false, "#100", "#102", "1.0", IconResourceID = 400)]  
    [ProvideLoadKey("Standard", "1.0", "Package Name", "Company", 1)]  
    [ProvideMenuResource(1000, 1)]  
    [ProvideToolboxItemConfigurationAttribute(typeof(ToolboxConfig))]  
  
    [GuidAttribute("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    public class ItemConfiguration : Package  
    ```  
  
## Benutzerdefinierte Drag & Drop  
 Neben zu **Toolbox** selbst hinzugefügt werden, können <xref:System.Drawing.Design.ToolboxItem>\-Objekte und ihre Implementierungen verwendet werden, um die Drag & Drop\-Unterstützung im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE zu erweitern.  Dies kann zu **Toolbox** und in Editoren verfügbar gemacht werden sollen, die beliebige Zwischenablageformate ermöglichen.  
  
 VSPackages auf das verwaltete Paketframework muss als Bereitstellen von benutzerdefinierten Toolboxelement\-Zwischenablageformaten registrieren, indem er eine Instanz von <xref:Microsoft.VisualStudio.Shell.ProvideToolboxFormatAttribute> auf die Klasse angewendet wird, die <xref:Microsoft.VisualStudio.Shell.Package>implementiert.  
  
 Weitere Informationen zum Registrieren **Toolbox** als Anbieter finden Sie unter [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md).  
  
#### Um benutzerdefinierte Zwischenablageformate und Drag & Drop\-Unterstützung in Toolbox Steuerelemente unterstützen  
  
1.  Erstellen Sie eine Implementierung des <xref:System.Drawing.Design.ToolboxItemCreatorCallback> Delegaten.  
  
     Diese Implementierung sollte ein <xref:System.Drawing.Design.ToolboxItem>\-Objekt zurückgeben, das das nichtstandardisierte Zwischenablageformat unterstützt.  
  
     Ein Beispiel finden <xref:System.Drawing.Design.ToolboxItemCreatorCallback> Implementierung eines Delegaten, die <xref:System.Drawing.Design.ToolboxItem> und <xref:System.Drawing.Design.ToolboxItemCreatorCallback> Referenzseiten.  
  
2.  Führen Sie diese Implementierung der <xref:System.Drawing.Design.ToolboxItemCreatorCallback> Delegaten, der auf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Toolbox** für eine nichtstandardisierte Toolbox verfügbar ist, indem Sie <xref:System.Drawing.Design.IToolboxService.AddCreator%2A>aufrufen.  
  
    ```vb#  
    <GuidAttribute("7D91995B-A799-485e-BFC7-C52545DFB5DD")> _   
    <ProvideToolboxFormatAttribute("MyFormat")> _   
    Public Class ItemConfiguration   
        Inherits MSVSIP.Package   
        Public Overloads Overrides Sub Initialize()   
            '"Adding this class as a ToolboxItemCreator");   
            Dim toolbox As IToolboxService = DirectCast(host.GetService(GetType(IToolboxService)), IToolboxService)   
            If toolbox IsNot Nothing Then   
                toolboxCreator = New ToolboxItemCreatorCallback(Me.OnCreateToolboxItem)   
                toolbox.AddCreator(toolboxCreator, "MyFormat", host)   
            End If   
        End Sub   
    End Class  
    ```  
  
    ```c#  
    [GuidAttribute("7D91995B-A799-485e-BFC7-C52545DFB5DD")]  
    [ProvideToolboxFormatAttribute("MyFormat")]  
    public class ItemConfiguration : MSVSIP.Package  
    {  
        public override void Initialize() {   
            /*  
            *  
            */  
            //"Adding this class as a ToolboxItemCreator");  
            IToolboxService toolbox = (IToolboxService)host.GetService(typeof(IToolboxService));  
            if (toolbox != null) {  
                toolboxCreator = new ToolboxItemCreatorCallback(this.OnCreateToolboxItem);  
                toolbox.AddCreator(toolboxCreator, "MyFormat", host);  
            }  
            private ToolboxItem OnCreateToolboxItem(object serializedData, string format) {  
               /*  
                *  
                */  
            }  
        }  
    }  
    ```  
  
### In diesem Abschnitt  
 [Gewusst wie: Unterstützen der Drag & Drop\-Funktionalität der Toolbox](../misc/how-to-support-toolbox-drag-and-drop-functionality.md)  
 Beschreibt, wie Drag & Drop\-Unterstützung in einer Ansicht des Dokuments implementiert.  
  
 [Gewusst wie: Bereitstellen von benutzerdefinierten Werkzeugkastenelementen mithilfe von Interopassemblys](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)  
 Beschreibt neue ActiveX\-Steuerelemente und \-**Toolbox**zu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neue Elemente hinzuzufügen.  Diese neuen Artikel können entweder ein Standardwert zwischenablageformat oder ein benutzerdefiniertes Format aufweisen, die von einem VSPackage unterstützt werden.  
  
 [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)  
 Beschreibt, wie ein VSPackage Toolbox als Anbieter registriert.  Befasst sich auch dem Sichern oder der Anwendung weiterer Toolbox.  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)   
 [Werkzeugkasten, exemplarische Vorgehensweisen](../misc/toolbox-walkthroughs.md)   
 [Registrieren von Funktionen zur Toolbox\-Unterstützung](../misc/registering-toolbox-support-features.md)   
 [Gewusst wie: Bereitstellen von benutzerdefinierten Werkzeugkastenelementen mithilfe von Interopassemblys](../misc/how-to-provide-custom-toolbox-items-by-using-interop-assemblies.md)   
 [Verwalten der Toolbox](../misc/managing-the-toolbox.md)   
 [Gewusst wie: Steuern der Toolbox](../Topic/How%20to:%20Control%20the%20Toolbox.md)