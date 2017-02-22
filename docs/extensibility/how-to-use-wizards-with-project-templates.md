---
title: "Gewusst wie: Verwenden von Assistenten mit Projektvorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IWizard-Schnittstelle"
  - "Projektvorlagen [Visual Studio], Assistenten"
  - "Vorlagen [Visual Studio], Assistenten"
  - "Visual Studio-Vorlagen, Assistenten"
  - "Assistenten [Visual Studio], Projektvorlagen"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Verwenden von Assistenten mit Projektvorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio stellt die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle bereit, die, falls sie implementiert ist, das Ausführen von benutzerdefiniertem Code beim Erstellen eines Projekts aus einer Vorlage ermöglicht.  
  
 Durch das Anpassen von Projektvorlagen können Sie folgende Aufgaben ausführen:  
  
-   Anzeigen einer benutzerdefinierten Benutzeroberfläche, die Benutzereingaben zur Parametrisierung der Vorlage erfasst  
  
-   Hinzufügen von Parameterwerten zur Verwendung in der Vorlage  
  
-   Hinzufügen von zusätzlichen Dateien zur Vorlage  
  
-   Ausführen praktisch aller im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Automatisierungsobjektmodell zulässigen Aktionen für ein Projekt  
  
 Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstellenmethoden werden zu verschiedenen Zeitpunkten während der Erstellung des Projekts aufgerufen, wenn ein Benutzer im Dialogfeld **Neues Projekt** auf **OK** klickt.  Die Namen der einzelnen Methoden der Schnittstelle beschreiben jeweils den Zeitpunkt, zu dem sie aufgerufen werden.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ruft <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> beispielsweise auf, wenn das Erstellen des Projekts gestartet wird. Daher eignet sich diese Position gut für benutzerdefinierten Code zur Erfassung von Benutzereingaben.  
  
 In Code, den Sie für benutzerdefinierte Assistenten schreiben, wird meistens das <xref:EnvDTE.DTE>\-Objekt zum Anpassen des Projekts verwendet. Dies ist das wichtigste Objekt im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Automatisierungsobjektmodell.  Weitere Informationen über das Automatisierungsobjektmodell finden Sie unter [Erweitern der Visual Studio\-Umgebung](../Topic/Extending%20the%20Visual%20Studio%20Environment.md) und [Referenz zur Automatisierung und Erweiterbarkeit](../Topic/Automation%20and%20Extensibility%20Reference.md)  
  
## Erstellen eines benutzerdefinierten Vorlagen\-Assistenten  
 In diesem Thema wird das Erstellen eines benutzerdefinierten Vorlagen\-Assistenten veranschaulicht, der vor dem Erstellen des Projekts ein Windows Form öffnet.  Das Formular ermöglicht Benutzern das Hinzufügen eines benutzerdefinierten Parameterwerts, der während der Erstellung des Projekts dem Quellcode hinzugefügt wird.  Im Folgenden werden die einzelnen Hauptschritte im Detail beschrieben.  
  
#### So erstellen Sie einen benutzerdefinierten Vorlagen\-Assistenten  
  
1.  Erstellen Sie eine Assembly, die die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementiert.  
  
2.  Installieren Sie die Assembly im globalen Assemblycache.  
  
3.  Erstellen Sie ein Projekt, und erstellen Sie mithilfe des **Assistenten zum Exportieren von Vorlagen** eine Vorlage aus dem Projekt.  
  
4.  Bearbeiten Sie die Vorlage, indem Sie der VSTEMPLATE\-Datei ein `WizardExtension`\-Element hinzufügen, um die Vorlage mit der Assembly zu verknüpfen, die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> implementiert.  
  
5.  Erstellen Sie mit dem benutzerdefinierten Assistenten ein neues Projekt.  
  
## Implementieren von IWizard  
 Der erste Schritt besteht darin, eine Assembly zu erstellen, die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> implementiert.  Diese Assembly zeigt mithilfe der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>\-Methode ein Windows Form an, das Benutzern das Hinzufügen eines benutzerdefinierten Parameterwerts ermöglicht, der während der Erstellung des Projekts verwendet wird.  
  
> [!NOTE]
>  In diesem Beispiel wird [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verwendet, um <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> zu implementieren. Alternativ können Sie auch [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] verwenden.  
  
#### So implementieren Sie IWizard  
  
1.  Erstellen Sie ein neues Klassenbibliotheksprojekt.  
  
2.  Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementiert.  Ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Beispiel für eine vollständig implementierte <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle finden Sie im nachfolgenden Code.  
  
 Dieses Beispiel umfasst zwei Codedateien: `IWizardImplementation`, eine Klasse, die die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementiert, sowie `UserInputForm`, das Windows Form für Benutzereingaben.  
  
### IWizardImplementation\-Klasse  
 Die `IWizardImplementation`\-Klasse enthält Methodenimplementierungen für alle Member von <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  In diesem Beispiel führt nur die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>\-Methode eine Aufgabe aus.  Alle anderen Methoden bleiben entweder ohne Wirkung oder geben `true` zurück.  
  
 Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>\-Methode nimmt vier Parameter an:  
  
-   Einen <xref:System.Object>\-Parameter, der in das <xref:EnvDTE._DTE>\-Stammobjekt umgewandelt werden kann, um die Anpassung des Projekts zu ermöglichen.  
  
-   Einen <xref:System.Collections.Generic.Dictionary%602>\-Parameter, der eine Auflistung aller vordefinierten Parameter in der Vorlage enthält.  Weitere Informationen zu Vorlagenparametern finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
-   Einen <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>\-Parameter, der Informationen zur Art der verwendeten Vorlage enthält.  
  
-   Ein <xref:System.Object>\-Array, das einen Satz von Parametern enthält, die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] an den Assistenten übergeben werden.  
  
 In diesem Beispiel wird dem <xref:System.Collections.Generic.Dictionary%602>\-Parameter ein Parameterwert aus dem Benutzereingabeformular hinzugefügt.  Jede Instanz des `$custommessage$`\-Parameters im Projekt wird durch den vom Benutzer eingegebenen Text ersetzt.  Sie müssen dem Projekt die folgenden Assemblys hinzufügen:  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  Das in diesem Beispiel verwendete UserInputForm\-Element wird im folgenden Abschnitt definiert.  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
    {  
        private UserInputForm inputForm;  
        private string customMessage;  
  
        // This method is called before opening any item that   
        // has the OpenInEditor attribute.  
        public void BeforeOpeningFile(ProjectItem projectItem)  
        {  
        }  
  
        public void ProjectFinishedGenerating(Project project)  
        {  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public void ProjectItemFinishedGenerating(ProjectItem   
            projectItem)  
        {  
        }  
  
        // This method is called after the project is created.  
        public void RunFinished()  
        {  
        }  
  
        public void RunStarted(object automationObject,  
            Dictionary<string, string> replacementsDictionary,  
            WizardRunKind runKind, object[] customParams)  
        {  
            try  
            {  
                // Display a form to the user. The form collects   
                // input for the custom message.  
                inputForm = new UserInputForm();  
                inputForm.ShowDialog();  
  
                customMessage = inputForm.get_CustomMessage();  
  
                // Add custom parameters.  
                replacementsDictionary.Add("$custommessage$",   
                    customMessage);  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.ToString());  
            }  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public bool ShouldAddProjectItem(string filePath)  
        {  
            return true;  
        }          
    }  
}  
```  
  
### Benutzereingabeformular  
 Das Benutzereingabeformular stellt ein einfaches Formular zur Eingabe eines benutzerdefinierten Parameters bereit.  Das Formular enthält ein Textfeld mit dem Namen `textBox1` und eine Schaltfläche mit dem Namen `button1`.  Wenn auf die Schaltfläche geklickt wird, wird der Text aus dem Textfeld im `customMessage`\-Parameter gespeichert.  
  
##### So fügen Sie der Projektmappe ein Windows Form hinzu  
  
1.  Fügen Sie den folgenden Code der Datei hinzu, in der die Assistentenimplementierung enthalten ist.  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## Installieren der Assembly in den globalen Assemblycache  
 Die Assembly, die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> implementiert, muss mit einem starken Namen signiert und im globalen Assemblycache installiert werden.  
  
#### So installieren Sie die Assembly im globalen Assemblycache  
  
1.  Signieren Sie die Assembly mit einem starkem Namen.  Weitere Informationen finden Sie unter [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md) oder [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/de-de/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
2.  Installieren Sie die mit einem starkem Namen signierte Assembly im globalen Assemblycache.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren einer Assembly in den globalen Assemblycache](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md).  
  
## Erstellen eines als Vorlage zu verwendenden Projekts  
 Das in diesem Beispiel als Vorlage verwendete Projekt ist eine Konsolenanwendung, die die im Benutzereingabeformular des benutzerdefinierten Assistenten angegebene Meldung anzeigt.  
  
#### So erstellen Sie das Beispielprojekt  
  
1.  Erstellen Sie eine neue [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Konsolenanwendung.  
  
2.  Fügen Sie der `Main`\-Methode der Anwendung die folgende Codezeile hinzu.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Der `$custommessage$`\-Parameter wird beim Erstellen eines Projekts aus der Vorlage durch den im Benutzereingabeformular eingegebenen Text ersetzt.  
  
3.  Klicken Sie im Menü **Datei** auf **Vorlage exportieren**.  
  
4.  Klicken Sie im **Assistenten zum Exportieren von Vorlagen** auf **Projektvorlage**, wählen Sie das zutreffende Projekt aus, und klicken Sie auf **Weiter**.  
  
5.  Geben Sie im **Assistenten zum Exportieren von Vorlagen** eine Beschreibung der Vorlage ein, aktivieren Sie das Kontrollkästchen **Vorlage automatisch in Visual Studio importieren**, und klicken Sie auf **Fertig stellen**.  
  
     Die Vorlage wird nun im Dialogfeld **Neues Projekt** angezeigt, sie verwendet jedoch nicht den benutzerdefinierten Assistenten.  
  
 Im folgenden Beispiel wird die vollständige Codedatei vor dem Exportieren in eine Vorlage dargestellt.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## Ändern der Vorlage  
 Nachdem die Vorlage erstellt wurde und im Dialogfeld **Neues Projekt** angezeigt wird, müssen Sie sie ändern, damit sie die in den vorhergehenden Schritten erstellte Assembly verwendet.  
  
#### So fügen Sie der Vorlage den benutzerdefinierten Assistenten hinzu  
  
1.  Suchen Sie die ZIP\-Datei, die die Vorlage enthält.  
  
    1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
    2.  Klicken Sie auf **Projekte und Projektmappen**.  
  
    3.  Lesen Sie das Textfeld **Speicherort von Visual Studio\-Benutzerprojektvorlagen**.  
  
     Dieses Verzeichnis lautet standardmäßig Eigene Dateien\\Visual Studio *Version*\\Templates\\ProjectTemplates.  
  
2.  Extrahieren Sie die ZIP\-Datei.  
  
3.  Öffnen Sie die VSTEMPLATE\-Datei in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Fügen Sie hinter dem `TemplateContent`\-Element ein [WizardExtension\-Element \(Visual Studio\-Vorlagen\)](../extensibility/wizardextension-element-visual-studio-templates.md)\-Element mit dem starken Namen der benutzerdefinierten Assistentenassembly hinzu.  Weitere Informationen zum Suchen des starken Namens der Assembly finden Sie unter [Gewusst wie: Anzeigen der Inhalte des globalen Assemblycaches](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md) und [Gewusst wie: Verweisen auf eine Assembly mit starkem Namen](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md)  
  
     Im folgenden Beispiel wird ein `WizardExtension`\-Element veranschaulicht.  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## Verwenden des benutzerdefinierten Assistenten  
 Nun können Sie ein Projekt aus der Vorlage erstellen und den benutzerdefinierten Assistenten verwenden.  
  
#### So verwenden Sie den benutzerdefinierten Assistenten  
  
1.  Klicken Sie im Menü **Datei** auf **Neues Projekt**.  
  
2.  Suchen Sie im Dialogfeld **Neues Projekt** nach der Vorlage, geben Sie einen Namen ein, und klicken Sie auf **OK**.  
  
     Das Benutzereingabeformular des Assistenten wird geöffnet.  
  
3.  Geben Sie einen Wert für den benutzerdefinierten Parameter ein, und klicken Sie auf die Schaltfläche.  
  
     Das Benutzereingabeformular des Assistenten wird geschlossen, und aus der Vorlage wird ein Projekt erstellt.  
  
4.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Quellcodedatei, und wählen Sie **Code anzeigen** aus.  
  
     Beachten Sie, dass `$custommessage$` durch den im Benutzereingabeformular des Assistenten eingegebenen Text ersetzt wurde.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension\-Element \(Visual Studio\-Vorlagen\)](../extensibility/wizardextension-element-visual-studio-templates.md)