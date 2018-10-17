---
title: 'Exemplarische Vorgehensweise: Debuggen eines Web Forms | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5b9be1d03c8635b1d6b01556c8b4c3963db1d7a2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279335"
---
# <a name="walkthrough-debugging-a-web-form"></a>Exemplarische Vorgehensweise: Debuggen eines Web Forms
Die Schritte in dieser exemplarischen Vorgehensweise enthalten eine Anleitung zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen (auch bekannt als Web Forms). Sie erfahren Sie, wie zum Starten und beenden, legen Sie Haltepunkte fest und Untersuchen von Variablen in der **Watch** Fenster.  
  
> [!NOTE]
>  Um diese exemplarische Vorgehensweise vollständig durchzuarbeiten, müssen Sie auf dem Servercomputer über Administratorrechte verfügen. Standardmäßig wird der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess (entweder aspnet_wp.exe oder w3wp.exe) als [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess ausgeführt. Sie müssen zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] auf dem Computer, auf dem es von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ausgeführt wird, über Administratorrechte verfügen. Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
 Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-create-the-web-form"></a>So erstellen Sie das Web Form  
  
1.  Falls Sie bereits eine Projektmappe geöffnet haben, schließen Sie sie.  
  
2.  Auf der **Datei** Menü klicken Sie auf **neu**, und klicken Sie dann auf **Website**.  
  
     Die **neue Website** Dialogfeld wird angezeigt.  
  
3.  In der **Vorlagen** Bereich, klicken Sie auf **ASP.NET-Website**.  
  
4.  Auf der **Speicherort** Zeile, klicken Sie auf **HTTP** aus der Liste, und klicken Sie im Textfeld geben **http://localhost/WebSite**.  
  
5.  In der **Sprache** auf **Visual C#-** oder **Visual Basic**.  
  
6.  Klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt ein neues Projekt und zeigt den standardmäßigen HTML-Quellcode an. Es erstellt auch ein neues virtuelles Verzeichnis mit dem Namen **WebSite** unter **Default Web Site** in IIS.  
  
7.  Klicken Sie auf die **Entwurf** Registerkarte am unteren Seitenrand.  
  
8.  Klicken Sie auf die **Toolbox** Registerkarte am linken Rand aus, oder wählen Sie ihn auf die **Ansicht** Menü.  
  
     Die **Toolbox** wird geöffnet.  
  
9. In der **Toolbox**, klicken Sie auf die **Schaltfläche** steuern, und fügen Sie es der Hauptentwurfsoberfläche "default.aspx" hinzu.  
  
10. In der **Toolbox**, klicken Sie auf die **Textfeld** steuern, und ziehen Sie das Steuerelement auf der Entwurfsoberfläche Default.aspx.  
  
11. Doppelklicken Sie auf das abgelegte Button-Steuerelement.  
  
     Dadurch wechseln Sie zur Codepage: Default.aspx.cs bei C# oder Default.aspx.vb bei [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Der Cursor sollte sich in der `Button1_Click`-Funktion befinden.  
  
12. Fügen Sie folgenden Code in die `Button1_Click`-Funktion ein:  
  
    ```vb  
    TextBox1.Text = "Button was clicked!"
    ```  
  
    ```csharp
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Das Projekt wird fehlerfrei erstellt.  
  
     Jetzt können Sie mit dem Debuggen beginnen.  
  
### <a name="to-debug-the-web-form"></a>So debuggen Sie das Web Form  
  
1.  Klicken Sie im Fenster Default.aspx.cs oder Default.aspx.vb auf den linken Rand der Zeile, der Sie Text hinzugefügt haben:  
  
    ```vb  
    TextBox1.Text = "Button was clicked!"
    ```  

    ```csharp  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen. Weitere Informationen finden Sie unter [Haltepunkte](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
3.  Die **Debuggen nicht aktiviert** Dialogfeld wird angezeigt. Wählen Sie **ändern Sie die Datei "Web.config" zum Aktivieren von debugging** aus, und klicken Sie auf **OK**.  
  
     Internet Explorer wird gestartet, und die zuvor entworfene Seite wird angezeigt.  
  
4.  Klicken Sie im Internet Explorer auf die erstellte Schaltfläche.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gelangen Sie damit in die Zeile, in der Sie den Haltepunkt auf der Codepage Default.aspx.cs oder Default.aspx.vb festlegen. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf einen Befehl.  
  
5.  Auf der **Debuggen** Menü klicken Sie auf **Windows**, klicken Sie dann auf **Watch**, und klicken Sie dann auf **Überwachen 1**.  
  
6.  In der **Watch** geben **TextBox1.Text**.  
  
     Die **Watch** Fenster zeigt den Wert der Variablen `TextBox1.Text`:  
  
    '""' 
  
7.  Auf der **Debuggen** Menü klicken Sie auf **Prozedurschritt**.  
  
     Der Wert des `TextBox1.Text` Änderungen in der **Watch** Fenster zum Lesen:  
  
    `"Button was clicked!"`  
  
8.  Auf der **Debuggen** Menü klicken Sie auf **Weiter**.  
  
9. Klicken Sie im Internet Explorer erneut auf die erstellte Schaltfläche.  
  
     Die Ausführung hält wieder am Haltepunkt an.  
  
10. Klicken Sie im Fenster Default.aspx.cs bzw. Default.aspx.vb im linken Rand auf den roten Punkt.  
  
     Dadurch wird der Haltpunkt entfernt.  
  
11. Auf der **Debuggen** Menü klicken Sie auf **Debuggen beenden**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>So stellen Sie zum Debuggen eine Verbindung mit dem Web Form her  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Für möglichst effektives Debuggen kompilieren Sie die ausführbare Datei als Debugversion mit Symboldateien (.pdb).  
  
2.  Klicken Sie im Fenster Default.aspx.cs bzw. Default.aspx.vb auf den linken Rand der Zeile, um erneut einen Haltepunkt in der hinzugefügten Zeile festzulegen:  
  
    ```vb  
    TextBox1.Text = "Button was clicked!"
    ```
  
    ```csharp  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Auf der **Debuggen** Menü klicken Sie auf **Starten ohne Debugging**.  
  
     Das Web Form wird in Internet Explorer gestartet, der Debugger ist jedoch nicht angehängt.  
  
4.  Fügen Sie den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess an. Weitere Informationen finden Sie unter [bereitgestellte Web-Anwendungen Debuggen](../debugger/debugging-deployed-web-applications.md).  
  
5.  Klicken Sie im Internet Explorer auf die Schaltfläche im Formular.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sollten Sie den Haltepunkt in Default.aspx.cs, Default.aspx.vb oder Default.aspx erreichen.  
  
6.  Wenn Sie fertig sind Debuggen, auf die **Debuggen** Menü klicken Sie auf **Debuggen beenden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)