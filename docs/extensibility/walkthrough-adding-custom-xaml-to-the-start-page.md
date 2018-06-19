---
title: 'Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML an die Startseite | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18e6e782e703282f9eb4e189671c086eb17db427
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140058"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML an die Startseite
In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine benutzerdefinierte Visual Studio-Startseite zu erstellen, die einen Webbrowser enthält.  
  
## <a name="adding-custom-xaml"></a>Hinzufügen von benutzerdefinierten XAML-Elementen  
  
1.  Erstellen Sie eine Startseite mithilfe der Anweisungen in [erstellen eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md).  
  
2.  Suchen Sie in der Datei "MainWindow.xaml" die \<Raster > Abschnitt.  
  
3.  Hinzufügen einer \<TabControl > Element und ein \<TabItem > innerhalb der \< Raster > Element, wie im folgenden Beispiel dargestellt.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4.  Fügen Sie eine zweite \<TabItem >, mit einem \<Schaltfläche >-Element, das ein neues Projekt wird geöffnet:  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="MyButton" Height="Auto">  
                <Button Name="btnNewProj" Content="New Project"   
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
                    CommandParameter="File.NewProject" >  
                </Button>  
            </TabItem>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
## <a name="testing-the-custom-start-page"></a>Testen der benutzerdefinierten Startseite  
  
1.  Drücken Sie F5.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet, mit der benutzerdefinierten Startseite installiert, aber nicht ausgewählt ist.  
  
2.  Öffnen Sie in der experimentellen Instanz von Visual Studio, die **Tools öffnen / Umgebung** Seite.  
  
3.  Wählen Sie **Start**. Auf der **Startseite anpassen** aus, wählen Sie die XAML-Datei, und klicken Sie auf **OK**.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
5.  Klicken Sie auf die **Bing** Registerkarte.  
  
     Daraufhin sollte eine Bing-Webseite.  
  
6.  Klicken Sie auf die **MyButton** Registerkarte.  
  
     Daraufhin sollte eine **"meinProjekt"** Schaltfläche daraufhin die **neues Projekt** Dialogfeld.  
  
7.  Schließen Sie die experimentelle Instanz.  
  
## <a name="applying-the-custom-start-page"></a>Anwenden der benutzerdefinierten Startseite  
  
#### <a name="to-test-the-custom-start-page"></a>So testen Sie die benutzerdefinierte Startseite  
  
1.  In **Extras / Optionen / Umgebung**Option **Start**. Auf der **Startseite anpassen** aus, wählen Sie die XAML-Datei, und klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Der Visual Studio-Startseite enthält jetzt eine Registerkarte, die einen Webbrowser eine Registerkarte und eine Registerkarte "MyButton" angezeigt. Können Sie benutzerdefinierte Startseiten mit denen andere Funktionen erstellen die *CodeBehind* Modell, um eine benutzerdefinierte DLL-Datei hinzufügen, wie gezeigt in [Benutzersteuerelement hinzufügen, um die Startseite](../extensibility/adding-user-control-to-the-start-page.md). Sie können benutzerdefinierte Startseiten für andere Benutzer freigeben, indem Sie die resultierende VSIX-Datei zu veröffentlichen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) -Website oder auf einer anderen Website oder Netzwerk freigeben. Weitere Informationen finden Sie unter [Bereitstellen von benutzerdefinierten Startseiten](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF-Containersteuerelemente](http://msdn.microsoft.com/en-us/a0177167-d7db-4205-9607-8ae316952566)