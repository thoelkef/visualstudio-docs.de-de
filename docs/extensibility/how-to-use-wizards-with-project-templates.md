---
title: 'Gewusst wie: Verwenden von Assistenten mit Projektvorlagen'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710544"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Gewusst wie: Verwenden von Assistenten mit Projektvorlagen

Visual Studio stellt die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>-Schnittstelle bereit, die, falls sie implementiert ist, das Ausführen von benutzerdefiniertem Code beim Erstellen eines Projekts aus einer Vorlage ermöglicht.

Die Anpassung von Projektvorlagen kann verwendet werden, um eine benutzerdefinierte Benutzeroberfläche anzuzeigen, die Benutzereingaben zum Anpassen der Vorlage, zum Hinzufügen zusätzlicher Dateien zur Vorlage oder zu einer anderen für ein Projekt zulässigen Aktion sammelt.

Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Schnittstellenmethoden werden zu verschiedenen Zeiten aufgerufen, während das Projekt erstellt wird, beginnend, sobald ein Benutzer im Dialogfeld **Neues Projekt** auf **OK** klickt. Die Namen der einzelnen Methoden der Schnittstelle beschreiben jeweils den Zeitpunkt, zu dem sie aufgerufen werden. Visual Studio ruft <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> z. B. sofort auf, wenn das Projekt erstellt wird, was es zu einem guten Speicherort macht, um benutzerdefinierten Code zum Sammeln von Benutzereingaben zu schreiben.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Erstellen eines Projektvorlagenprojekts mit einem VSIX-Projekt

Sie beginnen mit dem Erstellen einer benutzerdefinierten Vorlage mit dem Projektvorlagenprojekt, das Teil des Visual Studio SDK ist. In diesem Verfahren verwenden wir ein Projektvorlagenprojekt für C-Projekte, aber es gibt auch ein Visual Basic-Projektvorlagenprojekt. Anschließend fügen Sie der Projektmappe ein VSIX-Projekt hinzu, das das Projektvorlagenprojekt enthält.

1. Erstellen Sie ein Projektvorlagenprojekt für C-Projekte (in Visual Studio, wählen Sie**Neues** > **Projekt** **aus,** > und suchen Sie nach "Projektvorlage"). Nennen Sie es **MyProjectTemplate**.

   > [!NOTE]
   > Möglicherweise werden Sie aufgefordert, das Visual Studio SDK zu installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

2. Fügen Sie ein neues VSIX-Projekt in derselben Projektmappe wie das Projektvorlagenprojekt hinzu (wählen Sie im **Projektmappen-Explorer**den Projektmappenknoten aus, klicken Sie mit der rechten **Maustaste,** > und wählen Sie**Neues Projekt** hinzufügen aus, und suchen Sie nach "vsix"). Nennen Sie es **MyProjectWizard.**

3. Legen Sie das VSIX-Projekt als Startprojekt fest. Wählen Sie im **Projektmappen-Explorer**den VSIX-Projektknoten aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Als Startprojekt festlegen**aus.

4. Fügen Sie das Vorlagenprojekt als Asset des VSIX-Projekts hinzu. Suchen Sie im **Projektmappen-Explorer**unter dem VSIX-Projektknoten die Datei *source.extension.vsixmanifest.* Doppelklicken Sie darauf, um es im Manifesteditor zu öffnen.

5. Wählen Sie im Manifest-Editor die Registerkarte **Assets** auf der linken Seite des Fensters aus.

6. Wählen Sie auf der Registerkarte **Assets** die Option **Neu**aus. Wählen Sie im Fenster **Neues Objekt hinzufügen** für das Feld Typ **Microsoft.VisualStudio.ProjectTemplate**aus. Wählen Sie im Feld **Quelle** **ein Projekt in der aktuellen Projektmappe**aus. Wählen Sie im Feld **Projekt** **MyProjectTemplate**aus. Klicken Sie dann auf **OK**.

7. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio wird geöffnet. (Dies kann einige Minuten dauern.)

8. Versuchen Sie in der zweiten Instanz von Visual Studio, ein neues Projekt mit Ihrer neuen Vorlage zu erstellen **(Datei** > **neues** > **Projekt**, suchen Sie nach "myproject"). Das neue Projekt sollte mit einer Klasse mit dem Namen **Class1**angezeigt werden. Sie haben jetzt eine benutzerdefinierte Projektvorlage erstellt! Beenden Sie das Debuggen jetzt.

## <a name="create-a-custom-template-wizard"></a>Erstellen eines benutzerdefinierten Vorlagen-Assistenten

In diesem Verfahren wird gezeigt, wie Sie einen benutzerdefinierten Assistenten erstellen, der ein Windows-Formular öffnet, bevor das Projekt erstellt wird. Mit dem Formular können Benutzer einen benutzerdefinierten Parameterwert hinzufügen, der dem Quellcode während der Projekterstellung hinzugefügt wird.

1. Richten Sie das VSIX-Projekt ein, damit es eine Baugruppe erstellen kann.

2. Wählen Sie im **Projektmappen-Explorer**den VSIX-Projektknoten aus. Unter **Projektmappen-Explorer**sollte das **Eigenschaftenfenster** angezeigt werden. Wenn Sie dies nicht tun, wählen Sie**Eigenschaftenfenster** **anzeigen** > aus , oder drücken Sie **F4**. Wählen Sie im **Fenster Eigenschaften** `true`die folgenden Felder aus, um:

   - **Assembly in VSIX Container einschließen**

   - **Debugsymbole in VSIX-Container einschließen**

   - **Debugsymbole in die lokale VSIX-Bereitstellung einschließen**

3. Fügen Sie die Baugruppe als Asset zum VSIX-Projekt hinzu. Öffnen Sie die Datei *source.extension.vsixmanifest,* und wählen Sie die Registerkarte **Assets** aus. Wählen Sie im Fenster **Neues Objekt hinzufügen** für **Typ** **Microsoft.VisualStudio.Assembly**aus, wählen Sie für **Quelle** **Ein Projekt in der aktuellen Projektmappe**aus, und für **Project** wählen Sie **MyProjectWizard**aus.

4. Fügen Sie die folgenden Verweise auf das VSIX-Projekt hinzu. (Wählen Sie im **Projektmappen-Explorer**unter dem VSIX-Projektknoten **Referenzen**aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Referenz hinzufügen**aus.) Suchen Sie im Dialogfeld **Referenz hinzufügen** auf der Registerkarte **Framework** die **System.Windows** Forms-Assembly, und wählen Sie sie aus. Suchen und wählen Sie auch die **Baugruppen System** und **System.Drawing** aus. Wählen Sie nun die Registerkarte **Erweiterungen** aus. Suchen Sie die **EnvDTE-Baugruppe** und wählen Sie sie aus. Suchen Sie auch die **Microsoft.VisualStudio.TemplateWizardInterface-Assembly,** und wählen Sie sie aus. Klicken Sie auf **OK**.

5. Fügen Sie dem VSIX-Projekt eine Klasse für die Assistentenimplementierung hinzu. (Im **Projektmappen-Explorer**klicken Sie mit der rechten Maustaste auf den VSIX-Projektknoten, und wählen Sie **Hinzufügen**, dann **Neues Element**, dann **Klasse**.) Benennen Sie die Klasse **WizardImplementation**.

6. Ersetzen Sie den Code in der *WizardImplementationClass.cs* Datei durch den folgenden Code:

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

    Das **UserInputForm,** auf das in diesem Code verwiesen wird, wird später implementiert.

    Die `WizardImplementation`-Klasse enthält Methodenimplementierungen für alle Member von <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. In diesem Beispiel führt nur die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode eine Aufgabe aus. Alle anderen Methoden bleiben entweder ohne Wirkung oder geben `true` zurück.

    Die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>-Methode nimmt vier Parameter an:

   - Einen <xref:System.Object>-Parameter, der in das <xref:EnvDTE._DTE>-Stammobjekt umgewandelt werden kann, um die Anpassung des Projekts zu ermöglichen.

   - Einen <xref:System.Collections.Generic.Dictionary%602>-Parameter, der eine Auflistung aller vordefinierten Parameter in der Vorlage enthält. Weitere Informationen zu Vorlagenparametern finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

   - Einen <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>-Parameter, der Informationen zur Art der verwendeten Vorlage enthält.

   - Ein <xref:System.Object> Array, das eine Reihe von Parametern enthält, die von Visual Studio an den Assistenten übergeben werden.

     In diesem Beispiel wird dem <xref:System.Collections.Generic.Dictionary%602>-Parameter ein Parameterwert aus dem Benutzereingabeformular hinzugefügt. Jede Instanz des `$custommessage$`-Parameters im Projekt wird durch den vom Benutzer eingegebenen Text ersetzt.

7. Erstellen Sie nun das **UserInputForm**. Fügen Sie in der *WizardImplementation.cs* Datei den `WizardImplementation` folgenden Code nach dem Ende der Klasse hinzu.

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

## <a name="connect-the-wizard-to-the-custom-template"></a>Verbinden des Assistenten mit der benutzerdefinierten Vorlage

Damit Ihre benutzerdefinierte Projektvorlage Ihren benutzerdefinierten Assistenten verwenden kann, müssen Sie die Ordnerbaugruppe des Assistenten signieren und der benutzerdefinierten Projektvorlage einige Zeilen hinzufügen, damit sie darüber informieren kann, wo die Assistentenimplementierung beim Erstellen eines neuen Projekts zu finden ist.

1. Signieren Sie die Baugruppe. Wählen Sie im **Projektmappen-Explorer**das VSIX-Projekt aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Projekteigenschaften aus.**

2. Wählen Sie im Fenster **Projekteigenschaften** die Registerkarte **Signieren** aus. Aktivieren Sie auf der Registerkarte **Signieren** **die Option Assembly signieren**. Wählen Sie im Feld **Schlüsseldatei mit starkem Namen die** Option ** \<Neue>** aus. Geben Sie im Fenster **Schlüssel für den starken Namen erstellen** im Feld **Schlüsseldateiname** **key.snk**ein. Deaktivieren Sie die **Datei "Meine Schlüsseldatei mit einem Kennwortfeld** schützen".

3. Wählen Sie im **Projektmappen-Explorer**das VSIX-Projekt aus, und suchen Sie das **Eigenschaftenfenster.**

4. Legen Sie das Feld **Buildausgabe auf Ausgabeverzeichnis** kopieren auf **true**fest. Dadurch kann die Assembly beim Neuaufbau der Projektmappe in das Ausgabeverzeichnis kopiert werden. Es ist immer `.vsix` noch in der Datei enthalten. Sie müssen die Assembly sehen, um den Signaturschlüssel zu ermitteln.

5. Erstellen Sie die Projektmappe neu.

6. Sie finden nun die Datei key.snk im Projektverzeichnis MyProjectWizard*\<(Ihr Festplattenspeicherort> .MyProjectTemplate-MyProjectWizard-Key.snk*). Kopieren Sie die Datei *key.snk.*

7. Wechseln Sie zum Ausgabeverzeichnis, und suchen Sie die Assembly*\<(Ihren Festplattenspeicherort> .MyProjectTemplate/MyProjectWizard.bin-Debug-MyProjectWizard.dll*). Fügen Sie hier die Datei *key.snk* ein. (Dies ist nicht unbedingt notwendig, aber es wird die folgenden Schritte einfacher.)

8. Öffnen Sie ein Befehlsfenster, und wechseln Sie in das Verzeichnis, in dem die Assembly erstellt wurde.

9. Suchen Sie das Signaturtool *sn.exe.* Unter einem 64-Bit-Betriebssystem von Windows 10 wäre z. B. ein typischer Pfad der folgende:

     *C:-Programmdateien (x86) , Microsoft-SDKs-Windows-V10.0A-Bin-NETFX 4.6.1-Tools*

     Wenn Sie das Tool nicht finden können, führen Sie im Befehlsfenster aus, **wo /R . sn.exe.** Notieren Sie sich den Pfad.

10. Extrahieren Sie den öffentlichen Schlüssel aus der Datei *key.snk.* Geben Sie im Befehlsfenster

     **\<Speicherort von sn.exe>.sn.exe -p key.snk outfile.key.**

     Vergessen Sie nicht, den Pfad von *sn.exe* mit Anführungszeichen zu umgeben, wenn die Verzeichnisnamen Leerzeichen vorhanden sind!

11. Abrufen des öffentlichen Schlüsseltokens aus der Outfile:

     **\<Speicherort von sn.exe>.exe -t outfile.key.**

     Vergessen Sie auch die Anführungszeichen nicht. Sie sollten eine Zeile in der Ausgabe wie diese sehen

     **Das Token \<für öffentliche Schlüssel ist token>**

     Notieren Sie sich diesen Wert.

12. Fügen Sie den Verweis auf den benutzerdefinierten Assistenten zur *.vstemplate-Datei* der Projektvorlage hinzu. Suchen Sie im **Projektmappen-Explorer**die Datei mit dem Namen *MyProjectTemplate.vstemplate*, und öffnen Sie sie. Fügen Sie nach \<dem Ende des Abschnitts TemplateContent> den folgenden Abschnitt hinzu:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Wobei **MyProjectWizard** der Name der Assembly und **Token** das Token ist, das Sie im vorherigen Schritt kopiert haben.

13. Speichern Sie alle Dateien im Projekt, und erstellen Sie sie neu.

## <a name="add-the-custom-parameter-to-the-template"></a>Hinzufügen des benutzerdefinierten Parameters zur Vorlage

In diesem Beispiel zeigt das als Vorlage verwendete Projekt die Meldung an, die im Benutzereingabeformular des benutzerdefinierten Assistenten angegeben ist.

1. Wechseln Sie im **Projektmappen-Explorer**zum **Projekt MyProjectTemplate,** und öffnen *Sie Class1.cs*.

2. Fügen Sie der `Main`-Methode der Anwendung die folgende Codezeile hinzu.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Der `$custommessage$`-Parameter wird beim Erstellen eines Projekts aus der Vorlage durch den im Benutzereingabeformular eingegebenen Text ersetzt.

Hier ist die vollständige Codedatei, bevor sie in eine Vorlage exportiert wurde.

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

## <a name="use-the-custom-wizard"></a>Verwenden des benutzerdefinierten Assistenten

Nun können Sie ein Projekt aus der Vorlage erstellen und den benutzerdefinierten Assistenten verwenden.

1. Erstellen Sie die Lösung neu, und beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio sollte angezeigt werden.

2. Erstellen Sie ein neues MyProjectTemplate-Projekt. (**Datei** > **Neues** > **Projekt**).

3. Suchen Sie im Dialogfeld **Neues Projekt** nach "meinProjekt", um Ihre Vorlage zu suchen, geben Sie einen Namen ein, und klicken Sie auf **OK**.

     Das Benutzereingabeformular des Assistenten wird geöffnet.

4. Geben Sie einen Wert für den benutzerdefinierten Parameter ein, und klicken Sie auf die Schaltfläche.

     Das Benutzereingabeformular des Assistenten wird geschlossen, und aus der Vorlage wird ein Projekt erstellt.

5. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf die Quellcodedatei, und klicken Sie auf **Code anzeigen**.

     Beachten Sie, dass `$custommessage$` durch den im Benutzereingabeformular des Assistenten eingegebenen Text ersetzt wurde.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)
- [WizardExtension-Element (Visual Studio-Vorlagen)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)
