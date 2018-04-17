---
title: 'Vorgehensweise: Verwenden von Assistenten mit Projektvorlagen | Microsoft Docs'
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
ms.openlocfilehash: d29d2a1313bdb4e8a5e8654068984893578af4a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-wizards-with-project-templates"></a>Gewusst wie: Verwenden von Assistenten mit Projektvorlagen
Visual Studio stellt die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle bereit, die, falls sie implementiert ist, das Ausführen von benutzerdefiniertem Code beim Erstellen eines Projekts aus einer Vorlage ermöglicht.  
  
 Anpassen von Projektvorlagen kann verwendet werden, um benutzerdefinierte Benutzeroberfläche anzuzeigen, die Benutzereingaben passen Sie die Vorlage, zusätzliche Dateien zur Vorlage hinzufügen oder eine andere Aktion, die zulässig an einem Projekt erfasst.  
  
 Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstellenmethoden heißen zu verschiedenen Zeitpunkten während des Projekts gestartet erstellt wird, sobald ein Benutzer klickt, **OK** auf die **neues Projekt** (Dialogfeld). Die Namen der einzelnen Methoden der Schnittstelle beschreiben jeweils den Zeitpunkt, zu dem sie aufgerufen werden. Visual Studio ruft z. B. <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> sofort beim Starten sie zum Erstellen des Projekts, wodurch eignet sich diese Position zum Schreiben von benutzerdefiniertem Code, um Benutzereingaben zu erfassen.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Erstellen ein Projektvorlagenprojekt mit einem VSIX-Projekt  
 Sie starten mit dem Projekt Vorlage Projekt, das Teil der Visual Studio SDK ist eine benutzerdefinierte Vorlage erstellen. In diesem Verfahren verwenden wir ein C#-Projekt-Vorlagenprojekt, aber es gibt auch eine Visual Basic-Projektvorlagenprojekt. Dann fügen Sie ein VSIX-Projekt der Projektmappe, die das Projektvorlagenprojekt enthält.  
  
1.  Erstellen Sie ein C#-Projekt-Vorlagenprojekt (in Visual Studio **Datei > Neu > Projekt > Visual c# > Erweiterbarkeit > C#-Projektvorlage**). Nennen Sie sie **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Möglicherweise werden Sie aufgefordert, die Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Ein neues VSIX-Projekt hinzufügen (**Datei > Neu > Projekt > Visual c# > Erweiterbarkeit > VSIX-Projekt**) in der gleichen Lösung wie das Projektvorlagenprojekt (in der **Projektmappen-Explorer**, wählen die Knoten "Projektmappe", mit der rechten Maustaste und wählen Sie **hinzufügen > Neues Projekt**). Nennen Sie sie **MyProjectWizard.**  
  
3.  Legen Sie das VSIX-Projekt als Startprojekt. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten, mit der rechten Maustaste, und wählen **als Startprojekt festlegen**.  
  
4.  Fügen Sie der Projektvorlage als ein Medienobjekt des VSIX-Projekts hinzu. In der **Projektmappen-Explorer**, finden Sie unter den Knoten des VSIX-Projekt, das **"Source.Extension.vsixmanifest"** Datei. Doppelklicken Sie darauf, um sie im manifest-Editor zu öffnen.  
  
5.  Wählen Sie im manifest-Editor die **Bestand** Registerkarte auf der linken Seite des Fensters.  
  
6.  In der **Bestand** Registerkarte **neu**. In der **neue Anlage hinzufügen** Fenster für das Typfeld **Microsoft.VisualStudio.ProjectTemplate**. In der **Quelle** Feld **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** Feld **MyProjectTemplate**. Klicken Sie dann auf **OK**.  
  
7.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio wird geöffnet. (Dies kann einige Minuten dauern.)  
  
8.  Versuchen Sie in der zweiten Instanz von Visual Studio um ein neues Projekt mit Ihrer neuen Vorlage zu erstellen. (**Datei > Neu > Projekt > c# > "meinProjekt" Vorlage**). Das neue Projekt sollte angezeigt werden, mit einer Klasse mit dem Namen **Class1**. Sie haben jetzt eine benutzerdefinierte Projektvorlage erstellt! Beenden des Debuggens jetzt.  
  
## <a name="creating-a-custom-template-wizard"></a>Erstellen eines benutzerdefinierten Vorlagen-Assistenten  
 In diesem Thema wird das Erstellen eines benutzerdefinierten Vorlagen-Assistenten veranschaulicht, der vor dem Erstellen des Projekts ein Windows Form öffnet. Das Formular ermöglicht Benutzern, ein benutzerdefinierten Parameterwerts hinzuzufügen, das auf den Quellcode, während der projekterstellung hinzugefügt wird.  
  
1.  Richten Sie das VSIX-Projekt aus, um die ihm ermöglichen, eine Assembly zu erstellen.  
  
2.  In der **Projektmappen-Explorer**, wählen Sie den VSIX-Projekt-Knoten. Unten im Projektmappen-Explorer sehen Sie die **Eigenschaften** Fenster. Wenn Sie nicht der Fall ist, wählen Sie **Ansicht > Fenster "Eigenschaften"**, oder drücken Sie **F4**. Wählen Sie im Fenster Eigenschaften die folgenden Felder mit `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Fügen Sie die Assembly als ein Medienobjekt, das VSIX-Projekt. Öffnen Sie die Datei "Source.Extension.vsixmanifest", und wählen Sie die **Bestand** Registerkarte. In der **neue Anlage hinzufügen** Fenster für **Typ** wählen **Microsoft.VisualStudio.Assembly**, für **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**, und für **Projekt** wählen **MyProjectWizard**.  
  
4.  Fügen Sie die folgenden Verweise auf die VSIX-Projekt hinzu. (In der **Projektmappen-Explorer**, unter der VSIX project wählen **Verweise**, mit der rechten Maustaste, und wählen **Verweis hinzufügen**.) In der **Verweis hinzufügen** Dialogfeld in der **Framework** Registerkarte aus, suchen Sie die **System.Windows Forms** Assembly und wählen Sie sie. Wählen Sie jetzt die **Erweiterungen** Registerkarte Suchen den **EnvDTE** Assembly und wählen Sie sie. Auch die **Microsoft.VisualStudio.TemplateWizardInterface** Assembly und wählen Sie sie. Klicken Sie auf **OK**.  
  
5.  Fügen Sie eine Klasse für die Implementierung des Assistenten dem VSIX-Projekt. (Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste des Knotens des VSIX-Projekts, und wählen **hinzufügen**, klicken Sie dann **neues Element**, klicken Sie dann **Klasse**.) Benennen Sie die Klasse **WizardImplementation**.  
  
6.  Ersetzen Sie den Code in der **WizardImplementationClass.cs** Datei durch den folgenden Code:  
  
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
  
    -   Ein <xref:System.Object> Array, das einen Satz von Parametern enthält, die von Visual Studio an den Assistenten übergeben.  
  
     In diesem Beispiel wird dem <xref:System.Collections.Generic.Dictionary%602>-Parameter ein Parameterwert aus dem Benutzereingabeformular hinzugefügt. Jede Instanz des `$custommessage$`-Parameters im Projekt wird durch den vom Benutzer eingegebenen Text ersetzt. Sie müssen die folgenden Assemblys dem Projekt hinzufügen: **System** und **"System.Drawing"**.
  
7.  Erstellen Sie jetzt die **UserInputForm**. In der **WizardImplementation.cs** Datei, fügen Sie den folgenden Code nach dem Ende der **WizardImplementation** Klasse.  
  
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
 In der Reihenfolge für Ihre benutzerdefinierte Projektvorlage für Ihren benutzerdefinierten Assistenten verwenden müssen Sie zum Signieren der Assistentenassembly, und fügen Sie einige Zeilen der benutzerdefinierten Projektvorlage, mit der sie wissen, wo die Implementierung des Assistenten zu finden, wenn ein neues Projekt erstellt wird.  
  
1.  Signieren der Assembly an. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projekt, mit der rechten Maustaste und wählen Sie **Projekteigenschaften**.  
  
2.  In der **Projekteigenschaften** wählen die **Signierung** Registerkarte in der **Signierung** Registerkarte **zum Signieren der Assembly**. In der **Schlüsseldatei mit starkem Namen auswählen** Feld  **\<neu >**. In der **Schlüssel für einen starken Namen erstellen** Fenster, in dem **Schlüsseldateiname** Feld **"Key.snk"**. Deaktivieren Sie die **Schlüsseldatei mit Kennwort schützen** Feld.  
  
3.  In der **Projektmappen-Explorer**, wählen Sie das VSIX-Projekt, und suchen die **Eigenschaften** Fenster.  
  
4.  Legen Sie die **Kopie Ausgabe zum Buildausgabeverzeichnis** Feld **"true"**. Dadurch wird die Assembly in das Ausgabeverzeichnis kopiert werden, wenn die Projektmappe neu erstellt wird. Es ist immer noch in die VSIX-Datei enthalten. Sie müssen die Assembly angezeigt werden, um herauszufinden, dessen Signaturschlüssel.  
  
5.  Generieren Sie die Projektmappe neu.  
  
6.  Sie können jetzt suchen Sie die Datei "Key.snk" im Projektverzeichnis MyProjectWizard (**\<Ihre Festplattenspeicherort > \MyProjectTemplate\MyProjectWizard\key.snk**). Kopieren Sie die Datei "Key.snk".  
  
7.  Wechseln Sie in das Ausgabeverzeichnis und die Assembly (**\<Ihre Festplattenspeicherort > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Fügen Sie die key.snk-Datei aus. (Dies ist nicht unbedingt erforderlich, aber sie können die folgenden Schritte einfacher.)  
  
8.  Öffnen Sie ein Befehlsfenster, und wechseln Sie zum Verzeichnis, in dem die Assembly erstellt wurde.  
  
9. Suchen der **sn.exe** Tool signieren. Auf einem Windows 10 64-Bit-Betriebssystem würde ein normaler Pfad z. B. Folgendes sein:  
  
     **C:\Programme (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools**  
  
     Wenn Sie das Tool finden können führen Sie **, in dem/r.  Sn.exe** im Befehlsfenster. Notieren Sie den Pfad.  
  
10. Extrahieren Sie den öffentlichen Schlüssel aus der Datei "Key.snk". Geben Sie im Befehlsfenster  
  
     **\<Speicherort von "sn.exe" > \sn.exe -p "Key.snk" outfile.key.**  
  
     Vergessen Sie nicht den Pfad von "sn.exe" mit Anführungszeichen umschließen, wenn Leerzeichen im Verzeichnisnamen vorliegen.  
  
11. Abrufen des öffentlichen Schlüsseltokens aus der Outfile:  
  
     **\<Speicherort von "sn.exe" > \sn.exe -t outfile.key.**  
  
     Vergessen Sie nicht erneut, die Anführungszeichen. Eine Zeile in der Ausgabe wie folgt sollte angezeigt werden.  
  
     **Token des öffentlichen Schlüssels ist. <token>**  
  
     Notieren Sie sich dieses Werts an.  
  
12. Fügen Sie den Verweis auf den benutzerdefinierten Assistenten zur VSTEMPLATE-Datei der Projektvorlage aus. Klicken Sie im Projektmappen-Explorer suchen Sie die Datei mit dem Namen MyProjectTemplate.vstemplate, und öffnen Sie es. Nach dem Ende der \<TemplateContent >-Abschnitt, fügen Sie folgenden Abschnitt:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Wobei **MyProjectWizard** ist der Name der Assembly und **token** ist das Token, die Sie im vorherigen Schritt kopiert haben.  
  
13. Speichern Sie alle Dateien im Projekt, und erstellen Sie neu.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Hinzufügen des benutzerdefinierten Parameters zur Vorlage  
 In diesem Beispiel zeigt das Projekt, das als Vorlage verwendet den im Benutzereingabeformular des benutzerdefinierten Assistenten angegebene Meldung.  
  
1.  Im Projektmappen-Explorer, wechseln Sie zu der **MyProjectTemplate** Projekt, und öffnen Sie **"Class1.cs"**.  
  
2.  Fügen Sie der `Main`-Methode der Anwendung die folgende Codezeile hinzu.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Der `$custommessage$`-Parameter wird beim Erstellen eines Projekts aus der Vorlage durch den im Benutzereingabeformular eingegebenen Text ersetzt.  
  
 Hier ist die vollständige Codedatei vor dem Exportieren in eine Vorlage.  
  
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
  
## <a name="using-the-custom-wizard"></a>Verwenden des benutzerdefinierten Assistenten  
 Nun können Sie ein Projekt aus der Vorlage erstellen und den benutzerdefinierten Assistenten verwenden.  
  
1.  Die Projektmappe neu erstellen und mit dem Debuggen beginnen. Eine zweite Instanz von Visual Studio sollte angezeigt werden.  
  
2.  Erstellen Sie ein neues MyProjectTemplate-Projekt. (**Datei > Neu > Projekt > c# > MyProjectTemplate**)  
  
3.  In der **neues Projekt** (Dialogfeld), suchen Sie die Vorlage, geben Sie einen Namen und klicken Sie auf **OK**.  
  
     Das Benutzereingabeformular des Assistenten wird geöffnet.  
  
4.  Geben Sie einen Wert für den benutzerdefinierten Parameter ein, und klicken Sie auf die Schaltfläche.  
  
     Das Benutzereingabeformular des Assistenten wird geschlossen, und aus der Vorlage wird ein Projekt erstellt.  
  
5.  In **Projektmappen-Explorer**mit der rechten Maustaste auf die Quellcodedatei, und klicken Sie auf **Code anzeigen**.  
  
     Beachten Sie, dass `$custommessage$` durch den im Benutzereingabeformular des Assistenten eingegebenen Text ersetzt wurde.  
  
## <a name="see-also"></a>Siehe auch  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)  
[WizardExtension-Element (Visual Studio-Vorlagen)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)
