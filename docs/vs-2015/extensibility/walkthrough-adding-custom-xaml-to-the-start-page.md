---
title: 'Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Start Seite | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674116"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>Exemplarische Vorgehensweise: Hinzufügen von benutzerdefiniertem XAML zur Startseite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine benutzerdefinierte Visual Studio-Start Seite erstellt wird, die einen Webbrowser enthält.  
  
## <a name="adding-custom-xaml"></a>Benutzerdefiniertes XAML hinzufügen  
  
1. Erstellen Sie eine Startseite, indem Sie die Anweisungen unter [Erstellen einer benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md)befolgen.  
  
2. Suchen Sie in der Datei "MainWindow. XAML" den \<Grid> Abschnitt.  
  
3. Fügen Sie im \<TabControl> -Element ein-Element und ein-Element hinzu \<TabItem> \< Grid> , wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. Fügen Sie eine Sekunde \<TabItem> mit einem-Element hinzu, \<Button> das ein neues Projekt öffnet:  
  
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
  
## <a name="testing-the-custom-start-page"></a>Testen der benutzerdefinierten Start Seite  
  
1. Drücken Sie F5.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet, und die benutzerdefinierte Start Seite ist installiert, aber nicht ausgewählt.  
  
2. Öffnen Sie in der experimentellen Instanz von Visual Studio die Seite Extras **/options/Umgebung** .  
  
3. Wählen Sie **Start**aus. Wählen Sie in der Liste **Start Seite anpassen** die XAML-Datei aus, und klicken Sie auf **OK**.  
  
4. Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
5. Klicken Sie **auf die Register** Karte "von  
  
     Sie sollten eine Seite mit der Seite "Web" sehen.  
  
6. Klicken Sie auf die Registerkarte **myButton** .  
  
     Es sollte eine Schaltfläche " **MyProject** " angezeigt werden, die das Dialogfeld " **Neues Projekt** " öffnet.  
  
7. Schließen Sie die experimentelle Instanz.  
  
## <a name="applying-the-custom-start-page"></a>Anwenden der benutzerdefinierten Start Seite  
  
#### <a name="to-test-the-custom-start-page"></a>So testen Sie die benutzerdefinierte Start Seite  
  
1. Wählen Sie unter Extras **/Optionen/Umgebung die Option** **Start**aus. Wählen Sie in der Liste **Start Seite anpassen** die XAML-Datei aus, und klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Die Visual Studio-Start Seite enthält jetzt eine Registerkarte, auf der eine Registerkarte mit dem Webbrowser und die Registerkarte MyButton angezeigt wird. Sie können benutzerdefinierte Start Seiten mit anderer Funktionalität erstellen, indem Sie das *Code Behind-* Modell zum Hinzufügen einer benutzerdefinierten DLL verwenden, wie unter [Hinzufügen eines Benutzer Steuer Elements zur Start Seite](../extensibility/adding-user-control-to-the-start-page.md)gezeigt. Sie können benutzerdefinierte Start Seiten für andere Benutzer freigeben, indem Sie die resultierende vsix-Datei auf der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website oder auf einer anderen Website oder Netzwerkfreigabe veröffentlichen. Weitere Informationen finden Sie unter [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anpassen der Start Seite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF-Container Steuerelemente](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
