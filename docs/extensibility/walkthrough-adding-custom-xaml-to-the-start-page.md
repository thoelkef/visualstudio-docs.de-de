---
title: 'Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML zur Startseite | Microsoft-Dokumentation'
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
ms.openlocfilehash: b0b6d095ad9fb45d5cc9bd8979a267cb2ccf961f
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495621"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Exemplarische Vorgehensweise: Hinzufügen von benutzerdefinierten XAML zur Startseite
Diese exemplarische Vorgehensweise veranschaulicht eine benutzerdefinierte Visual Studio-Startseite zu erstellen, enthält einen Webbrowser.  
  
## <a name="adding-custom-xaml"></a>Hinzufügen von benutzerdefinierten XAML  
  
1.  Erstellen Sie eine Startseite mithilfe der Anweisungen in [erstellen eine benutzerdefinierten Startseite](../extensibility/creating-a-custom-start-page.md).  
  
2.  In der *"MainWindow.xaml"* Datei, suchen die \<Raster > Abschnitt.  
  
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
  
## <a name="testing-the-custom-start-page"></a>Testen die benutzerdefinierte Startseite  
  
1.  Drücken Sie **F5**.  
  
     Die experimentelle Instanz von Visual Studio wird geöffnet, mit der benutzerdefinierten Startseite installiert, aber nicht ausgewählt ist.  
  
2.  Öffnen Sie in der experimentellen Instanz von Visual Studio die **Extras/Optionen / Umgebung** Seite.  
  
3.  Wählen Sie **Start**. Auf der **Customize Start Page** Liste Ihrer *XAML* Datei, und klicken Sie auf **OK**.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Startseite**.  
  
5.  Klicken Sie auf die **Bing** Registerkarte.  
  
     Daraufhin sollte eine Bing-Webseite.  
  
6.  Klicken Sie auf die **MyButton** Registerkarte.  
  
     Daraufhin sollte eine **"meinProjekt"** Schaltfläche daraufhin die **neues Projekt** Dialogfeld.  
  
7.  Schließen Sie die experimentelle Instanz.  
  
## <a name="apply-the-custom-start-page"></a>Anwenden der benutzerdefinierten Startseite  
  
### <a name="to-test-the-custom-start-page"></a>Zum Testen der benutzerdefinierten Startseite  
  
1.  In **Extras / Optionen / Umgebung**Option **Start**. Auf der **Customize Start Page** Liste Ihrer *XAML* Datei, und klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Der Visual Studio-Startseite enthält jetzt eine Registerkarte, die eine Registerkarte des Webbrowsers und eine Registerkarte "MyButton" angezeigt. Sie können benutzerdefinierte Startseiten mithilfe von denen andere Funktionen erstellen den *Code-Behind* Modell eine benutzerdefinierte DLL-Datei hinzufügen, siehe [Benutzersteuerelement hinzufügen, um die Startseite](../extensibility/adding-user-control-to-the-start-page.md). Sie können benutzerdefinierte Startseiten für andere Benutzer freigeben, veröffentlichen Sie die resultierende VSIX-Datei in die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) -Website oder eine andere Website oder Netzwerk. Weitere Informationen finden Sie unter [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Startseite](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF-Container-Steuerelemente](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)