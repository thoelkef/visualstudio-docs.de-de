---
title: 'Vorgehensweise: erstellen ein Toolbox-Steuerelements, das Windows Forms verwendet | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 2860f3fca32b3a87967a404fb47626416d9f5dce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263717"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Gewusst wie: Erstellen eines Toolbox-Steuerelements, das Windows Forms verwendet
Mit der Vorlage „Windows Forms-Toolbox-Steuerelement“, die im [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] enthalten ist, können Sie die Windows Forms-Steuerelemente erstellen, die beim Installieren der Extension automatisch zur **Toolbox** hinzugefügt werden. Dieses Thema veranschaulicht, wie Sie die Vorlage verwenden, um ein **Toolbox** -Steuerelement zu erstellen, das Sie an andere Benutzer verteilen können.  
  
> [!NOTE]
>  Informationen zum Herunterladen des Visual Studio SDK finden Sie im [Visual Studio Extensibility Developer Center](http://go.microsoft.com/fwlink/?linkid=121964) auf der MSDN-Website.  
  
## <a name="creating-a-toolbox-control"></a>Erstellen eines Toolbox-Steuerelements  
 Verwenden Sie die Vorlage „Windows Forms-Toolbox-Steuerelement“ zum Erstellen des Projekts, und erstellen Sie dann eine Benutzeroberfläche (User Interface, UI) im Designer.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>So erstellen Sie ein Windows Forms-Toolbox-Steuerelementprojekt  
  
1.  Klicken Sie im Menü **Datei** auf **Neu**und dann auf **Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt** unter **Installierte Vorlagen**auf den Knoten für Ihre bevorzugte Programmiersprache, und klicken Sie dann auf **Erweiterbarkeit**. Wählen Sie in der Liste der Projekttypen **Windows Forms-Toolbox-Steuerelement**aus.  
  
3.  Geben Sie im Feld **Name** den Namen für das Projekt ein. Klicken Sie auf **OK**.  
  
     Visual Studio erstellt eine Projektmappe, die ein Benutzersteuerelement, ein Attribut zum Platzieren des Steuerelements in der **Toolbox**und ein VSIX-Manifest für die Bereitstellung enthält.  
  
#### <a name="to-build-the-control-ui"></a>So erstellen Sie die Steuerelement-Benutzeroberfläche  
  
1.  Doppelklicken Sie im **Projektmappen-Explorer**auf die Datei „ToolboxControl.cs“, um sie im Designer zu öffnen.  
  
2.  Ziehen Sie alle gewünschten Steuerelemente aus der **Toolbox**auf die Entwurfsoberfläche, und ordnen Sie sie gemäß Ihrem Entwurf an.  
  
3.  Legen Sie im Fenster **Eigenschaften** öffentliche Eigenschaften für das Benutzersteuerelement und für die untergeordneten Steuerelemente fest.  
  
## <a name="coding-the-control"></a>Codieren des Steuerelements  
 Standardmäßig wird das Steuerelement in der **Toolbox** als **ToolboxControl1** in einer **Toolbox** -Elementgruppe angezeigt, die den gleichen Namen wie Ihre Projektmappe aufweist. Sie können diese Namen in der Datei „ToolboxControl.cs“ ändern.  
  
#### <a name="to-code-the-control"></a>So codieren Sie das Steuerelement  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf „ToolboxControl.cs“, und klicken Sie dann auf **Code anzeigen** , um die Datei in der Codeansicht zu öffnen.  
  
2.  Klicken Sie in der Definition der partiellen Klasse, die das Steuerelement implementiert, mit der rechten Maustaste auf den Klassennamen, klicken Sie auf **Umgestalten**, und klicken Sie dann auf **Umbenennen**. Ändern Sie den Namen der Klasse in den Namen, der in der **Toolbox** angezeigt werden soll, wenn das Steuerelement installiert ist.  
  
3.  Ändern Sie direkt über der Klassendefinition in der `ProvideToolboxControl` -Attributdeklaration den Wert des ersten Parameters in den Namen der Elementgruppe, die das Steuerelement in der **Toolbox**hostet.  
  
     Das folgende Beispiel zeigt das `ProvideToolboxControl` -Attribut und die angepasste Klassendefinition für ein Steuerelement namens `Counter` in der `General` -Elementgruppe.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4.  Implementieren Sie die Eigenschaften, Methoden und Ereignisse für das Steuerelement.  
  
## <a name="building-testing-and-deployment"></a>Erstellen, Tests und Bereitstellung  
 Durch Drücken von F5 wird das Projekt erstellt (das eine VSIX-Bereitstellungsdatei enthält) und eine zweite Instanz von Visual Studio geöffnet, in der das Steuerelement in der **Toolbox**installiert ist.  
  
#### <a name="to-build-and-test-the-control"></a>So erstellen Sie das Steuerelement und testen es  
  
1.  Drücken Sie F5.  
  
2.  Erstellen Sie in der neuen Instanz von Visual Studio ein Windows Forms-Anwendungsprojekt.  
  
3.  Suchen Sie in der **Toolbox** nach dem Steuerelement, und ziehen Sie es dann auf die Entwurfsoberfläche.  
  
4.  Stellen Sie im Fenster **Eigenschaften** sicher, dass die Eigenschaften wie erwartet angezeigt werden.  
  
5.  Fügen Sie Code oder weitere Steuerelemente hinzu, die erforderlich sind, um Ihre Methoden und Ereignisse zu testen.  
  
6.  Drücken Sie F5, um die Windows Forms-Anwendung zu öffnen.  
  
7.  Stellen Sie sicher, dass die Eigenschaften, Methoden und Ereignisse des Steuerelements sich wie erwartet verhalten.  
  
#### <a name="to-deploy-the-control"></a>So stellen Sie das Steuerelement bereit  
  
1.  Nachdem Sie das getestete Projekt erstellt haben, öffnen Sie den Ordner „\bin\debug\“ des Projekts im Datei-Explorer, und suchen Sie nach der VSIX-Datei.  
  
2.  Laden Sie die VSIX-Datei in ein Netzwerk oder auf einer Website hoch.  
  
     Wenn Sie die Datei auf die Website [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) hochladen, können andere Benutzer den **Extension-Manager** in Visual Studio zum Suchen nach dem Steuerelement sowie zum Installieren des Steuerelements verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines WPF-Toolbox-Steuerelements](../extensibility/creating-a-wpf-toolbox-control.md)