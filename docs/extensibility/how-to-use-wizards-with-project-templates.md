---
title: 'Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d77cd34345055f6bcb4b8ea19631aa9a3a6780e3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499685"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Gewusst wie: Verwenden von Assistenten mit Projektvorlagen
Visual Studio stellt die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle bereit, die, falls sie implementiert ist, das Ausführen von benutzerdefiniertem Code beim Erstellen eines Projekts aus einer Vorlage ermöglicht.  
  
 Anpassen von Projektvorlagen kann verwendet werden, um benutzerdefinierte Benutzeroberfläche anzuzeigen, von dem Benutzer, die Eingabe für die Vorlage anpassen, die Vorlage Weitere Dateien hinzufügen oder eine andere Aktion zulässig gesammelt, an einem Projekt.  
  
 Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstellenmethoden werden zu verschiedenen Zeiten aufgerufen, während das Projekt gestartet erstellt wird, sobald ein Benutzer klickt, **OK** auf die **neues Projekt** Dialogfeld. Die Namen der einzelnen Methoden der Schnittstelle beschreiben jeweils den Zeitpunkt, zu dem sie aufgerufen werden. Visual Studio ruft z. B. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> sofort beim Starten sie zum Erstellen des Projekts, wodurch einen guten Speicherort zum Schreiben von benutzerdefinierten Codes, um Benutzereingaben zu sammeln.  
  
## <a name="create-a-project-template-project-with-a-vsix-project"></a>Erstellen Sie ein Projektvorlagenprojekt mit einem VSIX-Projekt  
 Sie beginnen, erstellen eine benutzerdefinierte Vorlage, mit der Standardprojektvorlage-Projekt., die Teil von Visual Studio SDK ist. In diesem Verfahren verwenden wir ein C#-Projekt-Vorlagenprojekt, aber es gibt auch ein Vorlagenprojekt für Visual Basic-Projekt. Dann fügen Sie ein VSIX-Projekt der Projektmappe, die das Projektvorlagenprojekt enthält.  
  
1.  Erstellen Sie ein C#-Projekt-Vorlagenprojekt (in Visual Studio **Datei** > **neu** > **Projekt** > **Visual c#**   >  **Erweiterbarkeit** > **C#-Projektvorlage**). Nennen Sie sie **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Möglicherweise werden Sie aufgefordert, die Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Fügen Sie ein neues VSIX-Projekt (**Datei** > **neu** > ** Projekt > **Visual C#-** > ** Erweiterbarkeit > **VSIX-Projekt**) in der gleichen Projektmappe wie das Projektvorlagenprojekt (in der **Projektmappen-Explorer**, wählen Sie den Knoten "Projektmappe", mit der rechten Maustaste und wählen Sie **hinzufügen** > **neues Projekt** ). Nennen Sie sie **MyProjectWizard.**  
  
3.  Festlegen Sie das VSIX-Projekt als Startprojekt. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten, mit der rechten Maustaste und wählen Sie **als Startprojekt festlegen**.  
  
4.  Fügen Sie die Vorlagen-Projekt als Ressource des VSIX-Projekts hinzu. In der **Projektmappen-Explorer**, finden Sie unter dem VSIX-Projektknoten angezeigt, die *"Source.Extension.vsixmanifest"* Datei. Doppelklicken Sie darauf, um sie im manifest-Editor zu öffnen.  
  
5.  Wählen Sie im manifest-Editor die **Assets** Registerkarte auf der linken Seite des Fensters.  
  
6.  In der **Assets** Registerkarte **neu**. In der **neue Anlage hinzufügen** -Fenster, für das Typfeld **Microsoft.VisualStudio.ProjectTemplate**. In der **Quelle** die Option **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** die Option **MyProjectTemplate**. Klicken Sie dann auf **OK**.  
  
7.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio wird geöffnet. (Dies kann einige Minuten dauern.)  
  
8.  Versuchen Sie in der zweiten Instanz von Visual Studio, ein neues Projekt mit Ihrer neuen Vorlage zu erstellen. (**Datei** > **neue** > **Projekt > Visual C#-** > **"meinProjekt" Vorlage**). Das neue Projekt sollte angezeigt werden, mit einer Klasse namens **Class1**. Sie haben nun eine benutzerdefinierte Projektvorlage erstellt! Beenden Sie debugging jetzt.  
  
## <a name="create-a-custom-template-wizard"></a>Erstellen Sie einen benutzerdefinierten Vorlagen-Assistenten  
 In diesem Thema wird das Erstellen eines benutzerdefinierten Vorlagen-Assistenten veranschaulicht, der vor dem Erstellen des Projekts ein Windows Form öffnet. Das Formular ermöglicht das Hinzufügen ein benutzerdefinierten Parameterwerts, das auf den Quellcode, während der projekterstellung hinzugefügt wird.  
  
1.  Richten Sie das VSIX-Projekt aus, um eine Assembly erstellt werden kann.  
  
2.  In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten. Unten im Projektmappen-Explorer sollte die **Eigenschaften** Fenster. Wenn Sie nicht, wählen Sie **Ansicht** > **Fenster "Eigenschaften"**, oder drücken Sie **F4**. In der **Eigenschaften** wählen Sie im Fenster die folgenden Felder `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Fügen Sie die Assembly zum VSIX-Projekt als Ressource hinzu. Öffnen der *"Source.Extension.vsixmanifest"* und wählen Sie die **Assets** Registerkarte. In der **neue Anlage hinzufügen** Fenster für **Typ** wählen **Microsoft.VisualStudio.Assembly**, für die **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**, und für **Projekt** wählen **MyProjectWizard**.  
  
4.  Fügen Sie die folgenden Verweise auf das VSIX-Projekt hinzu. (In der **Projektmappen-Explorer**, unter der VSIX project wählen **Verweise**, mit der rechten Maustaste, und wählen **Verweis hinzufügen**.) In der **Verweis hinzufügen** Dialogfeld in der **Framework** Registerkarte die **System.Windows Forms** Assembly und wählen Sie ihn. Wählen Sie jetzt die **Erweiterungen** Registerkarte Suchen den **EnvDTE** Assembly und wählen Sie ihn. Auch die **Microsoft.VisualStudio.TemplateWizardInterface** Assembly und wählen Sie ihn. Klicken Sie auf **OK**.  
  
5.  Fügen Sie eine Klasse für die Implementierung des Assistenten zum VSIX-Projekt ein. (In der **Projektmappen-Explorer**mit der rechten Maustaste auf den VSIX-Projektknoten, und wählen Sie **hinzufügen**, klicken Sie dann **neues Element**, klicken Sie dann **Klasse**.) Nennen Sie die Klasse **WizardImplementation**.  
  
6.  Ersetzen Sie den Code in die *WizardImplementationClass.cs* -Datei mit den folgenden Code:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
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
  
                    customMessage = UserInputForm.CustomMessage;  
  
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
  
     Die **UserInputForm** verwiesen wird, in diesem Code wird später implementiert werden.  
  
     Die `WizardImplementation`-Klasse enthält Methodenimplementierungen für alle Member von <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. In diesem Beispiel führt nur die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode eine Aufgabe aus. Alle anderen Methoden bleiben entweder ohne Wirkung oder geben `true` zurück.  
  
     Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode nimmt vier Parameter an:  
  
    -   Einen <xref:System.Object>-Parameter, der in das <xref:EnvDTE._DTE>-Stammobjekt umgewandelt werden kann, um die Anpassung des Projekts zu ermöglichen.  
  
    -   Einen <xref:System.Collections.Generic.Dictionary%602>-Parameter, der eine Auflistung aller vordefinierten Parameter in der Vorlage enthält. Weitere Informationen zu Vorlagenparametern finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
    -   Einen <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>-Parameter, der Informationen zur Art der verwendeten Vorlage enthält.  
  
    -   Ein <xref:System.Object> Array, das einen Satz von Parametern enthält, die an den Assistenten von Visual Studio übergeben.  
  
     In diesem Beispiel wird dem <xref:System.Collections.Generic.Dictionary%602>-Parameter ein Parameterwert aus dem Benutzereingabeformular hinzugefügt. Jede Instanz des `$custommessage$`-Parameters im Projekt wird durch den vom Benutzer eingegebenen Text ersetzt. Sie müssen die folgenden Assemblys hinzufügen, zu Ihrem Projekt: **System** und **"System.Drawing"**.
  
7.  Erstellen Sie jetzt die **UserInputForm**. In der *WizardImplementation.cs* Datei, fügen Sie den folgenden Code nach dem Ende der `WizardImplementation` Klasse.  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
                this.Close();
            }  
        }  
    ```  
  
     Das Benutzereingabeformular stellt ein einfaches Formular zur Eingabe eines benutzerdefinierten Parameters bereit. Das Formular enthält ein Textfeld mit dem Namen `textBox1` und eine Schaltfläche mit dem Namen `button1`. Wenn auf die Schaltfläche geklickt wird, wird der Text aus dem Textfeld im `customMessage`-Parameter gespeichert.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>Verbinden Sie den Assistenten mit der benutzerdefinierten Vorlage  
 In der Reihenfolge für Ihre benutzerdefinierte Projektvorlage des benutzerdefinierten Assistenten verwenden müssen Sie die Assistenten-Assembly zu signieren und einige Zeilen hinzufügen, um Ihre benutzerdefinierte Projektvorlage können sie wissen, wo Sie die Implementierung des Assistenten zu finden, wenn ein neues Projekt erstellt wird.  
  
1.  Signieren der Assembly. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projekt, mit der rechten Maustaste und wählen Sie **Projekteigenschaften**.  
  
2.  In der **Projekteigenschaften** wählen Sie im Fenster der **Signierung** Registerkarte in der **Signierung** Registerkarte **Assembly signieren**. In der **Schlüsseldatei mit starkem Namen auswählen** die Option  **\<neu >**. In der **Schlüssel für einen starken Namen erstellen** Fenster in der **Schlüsseldateiname** Feld **"Key.snk"**. Deaktivieren Sie die **Schlüsseldatei mit Kennwort schützen** Feld.  
  
3.  In der **Projektmappen-Explorer**, wählen Sie das VSIX-Projekt, und suchen die **Eigenschaften** Fenster.  
  
4.  Legen Sie die **Kopie Ausgabe zum Buildausgabeverzeichnis** Feld **"true"**. Dadurch wird die Assembly, in das Ausgabeverzeichnis kopiert werden, wenn die Projektmappe neu erstellt wird. Es ist immer noch Bestandteil der `.vsix` Datei. Sie müssen die Assembly finden Sie unter, um herauszufinden, die Signaturschlüssel.  
  
5.  Generieren Sie die Projektmappe neu.  
  
6.  Sie können die key.snk-Datei im Projektverzeichnis MyProjectWizard finden (*\<Ihr Speicherort > \MyProjectTemplate\MyProjectWizard\key.snk*). Kopieren der *"Key.snk"* Datei.  
  
7.  Wechseln Sie in das Ausgabeverzeichnis, und suchen Sie die Assembly (*\<Ihr Speicherort > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Fügen Sie der *"Key.snk"* Datei hier. (Dies ist nicht unbedingt erforderlich, aber es erleichtert die folgenden Schritte aus.)  
  
8.  Öffnen Sie ein Befehlsfenster, und ändern Sie in das Verzeichnis, in dem die Assembly erstellt wurde.  
  
9. Suchen der *sn.exe* Tool signieren. Auf einem Windows 10 64-Bit-Betriebssystem, wäre ein typischer Pfad z. B. Folgendes sein:  
  
     *C:\Programme (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*  
  
     Wenn Sie nicht, dass das Tool finden, führen Sie **, in dem/r.  Sn.exe** im Befehlsfenster angezeigt. Notieren Sie sich den Pfad an.  
  
10. Extrahiert den öffentlichen Schlüssel aus der *"Key.snk"* Datei. Geben Sie im Befehlsfenster  
  
     **\<Speicherort von "sn.exe" > \sn.exe -p "Key.snk" outfile.key.**  
  
     Vergessen Sie nicht, setzen Sie den Pfad des *sn.exe* in Anführungszeichen ein, wenn Leerzeichen in die Namen der Verzeichnisse vorhanden sind.  
  
11. Abrufen des öffentlichen Schlüssels aus der Outfile token:  
  
     **\<Speicherort von "sn.exe" > \sn.exe -t outfile.key.**  
  
     Vergessen Sie nicht in diesem Fall die Anführungszeichen ein. Eine Zeile in die Ausgabe wie die folgende sollte angezeigt werden.  
  
     **Token des öffentlichen Schlüssels ist. <token>**  
  
     Notieren Sie sich dieses Werts.  
  
12. Den Verweis auf den benutzerdefinierten Assistenten zum Hinzufügen der *VSTEMPLATE* Datei der Projektvorlage. In der **Projektmappen-Explorer**, suchen Sie die Datei mit dem Namen *MyProjectTemplate.vstemplate*, und öffnen Sie sie. Nach dem Ende der \<TemplateContent > im Abschnitt, fügen Sie folgenden Abschnitt:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Wo **MyProjectWizard** ist der Name der Assembly und **token** ist das Token, die Sie im vorherigen Schritt kopiert haben.  
  
13. Speichern Sie alle Dateien im Projekt, und erstellen Sie neu.  
  
## <a name="add-the-custom-parameter-to-the-template"></a>Fügen Sie den benutzerdefinierten Parameter der Vorlage  
 In diesem Beispiel zeigt das Projekt, das als Vorlage verwendet die in das Benutzereingabeformular des benutzerdefinierten Assistenten angegebene Meldung.  
  
1.  In der **Projektmappen-Explorer**, wechseln Sie zu der **MyProjectTemplate** Projekt, und öffnen Sie *"Class1.cs"*.  
  
2.  Fügen Sie der `Main`-Methode der Anwendung die folgende Codezeile hinzu.  
  
    ```csharp  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Der `$custommessage$`-Parameter wird beim Erstellen eines Projekts aus der Vorlage durch den im Benutzereingabeformular eingegebenen Text ersetzt.  
  
 Hier ist der vollständige Codedatei zu verlassen, bevor er zu einer Vorlage exportiert wurde.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="use-the-custom-wizard"></a>Verwenden Sie den benutzerdefinierten Assistenten  
 Nun können Sie ein Projekt aus der Vorlage erstellen und den benutzerdefinierten Assistenten verwenden.  
  
1.  Erstellen Sie die Projektmappe neu, und starten Sie das Debuggen. Eine zweite Instanz von Visual Studio sollte angezeigt werden.  
  
2.  Erstellen Sie ein neues MyProjectTemplate-Projekt. (**Datei** > **neue** > **Projekt** > **Visual C#-**  >  **MyProjectTemplate**)  
  
3.  In der **neues Projekt** Dialogfeld Suchen Ihrer Vorlage, geben Sie einen Namen, und klicken Sie auf **OK**.  
  
     Das Benutzereingabeformular des Assistenten wird geöffnet.  
  
4.  Geben Sie einen Wert für den benutzerdefinierten Parameter ein, und klicken Sie auf die Schaltfläche.  
  
     Das Benutzereingabeformular des Assistenten wird geschlossen, und aus der Vorlage wird ein Projekt erstellt.  
  
5.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Quellcodedatei, und klicken Sie auf **Ansichtscode**.  
  
     Beachten Sie, dass `$custommessage$` durch den im Benutzereingabeformular des Assistenten eingegebenen Text ersetzt wurde.  
  
## <a name="see-also"></a>Siehe auch  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)  
[WizardExtension-Element (Visual Studio-Vorlagen)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)
