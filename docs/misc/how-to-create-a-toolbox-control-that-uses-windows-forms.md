---
title: "Gewusst wie: Erstellen eines Toolbox-Steuerelements, das Windows Forms verwendet | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolbox-Steuerelement"
  - "winforms"
  - "Toolbox"
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Gewusst wie: Erstellen eines Toolbox-Steuerelements, das Windows Forms verwendet
Mit der Vorlage „Windows Forms\-Toolbox\-Steuerelement“, die im [!INCLUDE[vssdk_dev11_long](../misc/includes/vssdk_dev11_long_md.md)] enthalten ist, können Sie die Windows Forms\-Steuerelemente erstellen, die beim Installieren der Extension automatisch zur **Toolbox** hinzugefügt werden. Dieses Thema veranschaulicht, wie Sie die Vorlage verwenden, um ein **Toolbox**\-Steuerelement zu erstellen, das Sie an andere Benutzer verteilen können.  
  
> [!NOTE]
>  Informationen zum Herunterladen des Visual Studio SDK finden Sie im [Visual Studio Extensibility Developer Center](http://go.microsoft.com/fwlink/?linkid=121964) auf der MSDN\-Website.  
  
## Erstellen eines Toolbox\-Steuerelements  
 Verwenden Sie die Vorlage „Windows Forms\-Toolbox\-Steuerelement“ zum Erstellen des Projekts, und erstellen Sie dann eine Benutzeroberfläche \(User Interface, UI\) im Designer.  
  
#### So erstellen Sie ein Windows Forms\-Toolbox\-Steuerelementprojekt  
  
1.  Klicken Sie im Menü **Datei** auf **Neu** und dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **Installierte Vorlagen** auf den Knoten für Ihre bevorzugte Programmiersprache, und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie in der Liste der Projekttypen **Windows Forms\-Toolbox\-Steuerelement** aus.  
  
3.  Geben Sie im Feld **Name** den Namen für das Projekt ein. Klicken Sie auf **OK**.  
  
     Visual Studio erstellt eine Projektmappe, die ein Benutzersteuerelement, ein Attribut zum Platzieren des Steuerelements in der **Toolbox** und ein VSIX\-Manifest für die Bereitstellung enthält.  
  
#### So erstellen Sie die Steuerelement\-Benutzeroberfläche  
  
1.  Doppelklicken Sie im **Projektmappen\-Explorer** auf die Datei „ToolboxControl.cs“, um sie im Designer zu öffnen.  
  
2.  Ziehen Sie alle gewünschten Steuerelemente aus der **Toolbox** auf die Entwurfsoberfläche, und ordnen Sie sie gemäß Ihrem Entwurf an.  
  
3.  Legen Sie im Fenster **Eigenschaften** öffentliche Eigenschaften für das Benutzersteuerelement und für die untergeordneten Steuerelemente fest.  
  
## Codieren des Steuerelements  
 Standardmäßig wird das Steuerelement in der **Toolbox** als **ToolboxControl1** in einer **Toolbox**\-Elementgruppe angezeigt, die den gleichen Namen wie Ihre Projektmappe aufweist. Sie können diese Namen in der Datei „ToolboxControl.cs“ ändern.  
  
#### So codieren Sie das Steuerelement  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf „ToolboxControl.cs“, und klicken Sie dann auf **Code anzeigen**, um die Datei in der Codeansicht zu öffnen.  
  
2.  Klicken Sie in der Definition der partiellen Klasse, die das Steuerelement implementiert, mit der rechten Maustaste auf den Klassennamen, klicken Sie auf **Umgestalten**, und klicken Sie dann auf **Umbenennen**. Ändern Sie den Namen der Klasse in den Namen, der in der **Toolbox** angezeigt werden soll, wenn das Steuerelement installiert ist.  
  
3.  Ändern Sie direkt über der Klassendefinition in der `ProvideToolboxControl`\-Attributdeklaration den Wert des ersten Parameters in den Namen der Elementgruppe, die das Steuerelement in der **Toolbox** hostet.  
  
     Das folgende Beispiel zeigt das `ProvideToolboxControl`\-Attribut und die angepasste Klassendefinition für ein Steuerelement namens  `Counter` in der `General`\-Elementgruppe.  
  
     [!code-cs[ToolboxControlWinForms#07](../misc/codesnippet/CSharp/how-to-create-a-toolbox-control-that-uses-windows-forms_1.cs)]  
  
4.  Implementieren Sie die Eigenschaften, Methoden und Ereignisse für das Steuerelement.  
  
## Erstellen, Tests und Bereitstellung  
 Durch Drücken von F5 wird das Projekt erstellt \(das eine VSIX\-Bereitstellungsdatei enthält\) und eine zweite Instanz von Visual Studio geöffnet, in der das Steuerelement in der **Toolbox** installiert ist.  
  
#### So erstellen Sie das Steuerelement und testen es  
  
1.  Drücken Sie F5.  
  
2.  Erstellen Sie in der neuen Instanz von Visual Studio ein Windows Forms\-Anwendungsprojekt.  
  
3.  Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.  
  
4.  Stellen Sie im Fenster **Eigenschaften** sicher, dass die Eigenschaften wie erwartet angezeigt werden.  
  
5.  Fügen Sie Code oder weitere Steuerelemente hinzu, die erforderlich sind, um Ihre Methoden und Ereignisse zu testen.  
  
6.  Drücken Sie F5, um die Windows Forms\-Anwendung zu öffnen.  
  
7.  Stellen Sie sicher, dass die Eigenschaften, Methoden und Ereignisse des Steuerelements sich wie erwartet verhalten.  
  
#### So stellen Sie das Steuerelement bereit  
  
1.  Nachdem Sie das getestete Projekt erstellt haben, öffnen Sie den Ordner „\\bin\\debug\\“ des Projekts im Datei\-Explorer, und suchen Sie nach der VSIX\-Datei.  
  
2.  Laden Sie die VSIX\-Datei in ein Netzwerk oder auf einer Website hoch.  
  
     Wenn Sie die Datei auf die Website [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) hochladen, können andere Benutzer den **Extension\-Manager** in Visual Studio zum Suchen nach dem Steuerelement sowie zum Installieren des Steuerelements verwenden.  
  
## Siehe auch  
 [Erstellen ein WPF\-Toolbox\-Steuerelement](../extensibility/creating-a-wpf-toolbox-control.md)