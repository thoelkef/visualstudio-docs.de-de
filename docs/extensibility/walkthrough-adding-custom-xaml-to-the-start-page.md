---
title: "Exemplarische Vorgehensweise: Hinzuf&#252;gen von benutzerdefiniertem XAML zur Startseite | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "benutzerdefinierte Startseite"
  - "Verwendung von XAML-Startseite"
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Exemplarische Vorgehensweise: Hinzuf&#252;gen von benutzerdefiniertem XAML zur Startseite
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise veranschaulicht, wie eine benutzerdefinierte Visual Studio\-Startseite zu erstellen, enthält einen Webbrowser.  
  
## Hinzufügen von benutzerdefinierten XAML\-Elementen  
  
1.  Erstellen Sie eine Startseite mithilfe der Anweisungen in [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md).  
  
2.  Suchen Sie in der Datei "MainWindow.xaml" im Abschnitt \< Grid \>.  
  
3.  Fügen Sie ein Element \< TabControl \> und \< TabItem \> das \< Grid \>\-Element hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Grid> <TabControl> <TabItem Header="Bing" Height="Auto"> <Frame Source="http://www.bing.com" /> </TabItem> </TabControl> </Grid>  
    ```  
  
4.  Fügen Sie ein zweites \< TabItem \>, mit einem \< Button \>\-Element, das ein neues Projekt geöffnet wird:  
  
    ```xml  
    <Grid> <TabControl> <TabItem Header="MyButton" Height="Auto"> <Button Name="btnNewProj" Content="New Project" Command="{x:Static vscom:VSCommands.ExecuteCommand}" CommandParameter="File.NewProject" > </Button> </TabItem> <TabItem Header="Bing" Height="Auto"> <Frame Source="http://www.bing.com" /> </TabItem> </TabControl> </Grid>  
    ```  
  
## Testen die benutzerdefinierte Startseite  
  
1.  Drücken Sie F5.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet, die benutzerdefinierte Startseite installiert, aber nicht aktiviert.  
  
2.  Öffnen Sie in der experimentellen Instanz von Visual Studio, die **Tools\/Options \/ Umgebung** Seite.  
  
3.  Wählen Sie **Start**. Auf der **Startseite anpassen** aus, wählen Sie die XAML\-Datei, und auf **OK**.  
  
4.  Auf der **Ansicht** Menü klicken Sie auf **Startseite**.  
  
5.  Klicken Sie auf die **Bing** Registerkarte.  
  
     Sie sollten eine Bing\-Webseite angezeigt.  
  
6.  Klicken Sie auf die **MyButton** Registerkarte.  
  
     Sollte ein **MyProject** Schaltfläche daraufhin die **Neues Projekt** Dialogfeld.  
  
7.  Schließen Sie die experimentelle Instanz.  
  
## Die benutzerdefinierte Startseite anwenden  
  
#### So testen Sie die benutzerdefinierte Startseite  
  
1.  In **Extras \/ Optionen \/ Umgebung**, auf **Start**. Auf der **Startseite anpassen** aus, wählen Sie die XAML\-Datei, und auf **OK**.  
  
## Nächste Schritte  
 Die Visual Studio\-Startseite enthält jetzt eine Registerkarte, die eine Web\-Browser\-Registerkarte und eine Registerkarte MyButton angezeigt. Können benutzerdefinierte Startseiten mit anderen Funktionen mithilfe der *CodeBehind* Modell eine benutzerdefinierte DLL\-Datei hinzufügen, siehe [Hinzufügen des Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md). Sie können benutzerdefinierte Startseiten für andere Benutzer freigeben, veröffentlichen Sie die resultierende VSIX\-Datei an die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) \-Website oder auf einer anderen Website oder Netzwerk freigeben. Weitere Informationen finden Sie unter [Bereitstellen von benutzerdefinierte Startseiten](../extensibility/deploying-custom-start-pages.md).  
  
## Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF\-Containersteuerelemente](http://msdn.microsoft.com/de-de/a0177167-d7db-4205-9607-8ae316952566)