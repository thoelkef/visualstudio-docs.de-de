---
title: 'Exemplarische Vorgehensweise: Debuggen eines Web Forms | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 344ba292f16098c969d287a88a5d441acc950de1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-a-web-form"></a>Exemplarische Vorgehensweise: Debuggen eines Web Forms
Die Schritte in dieser exemplarischen Vorgehensweise enthalten eine Anleitung zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendungen (auch bekannt als Web Forms). Hier erfahren Sie zum Starten und Beenden der Ausführung, Haltepunkte festlegen und Untersuchen von Variablen in der **Überwachen** Fenster.  
  
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
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt ein neues Projekt und zeigt den standardmäßigen HTML-Quellcode an. Erstellt ein neues virtuelles Verzeichnis mit dem Namen auch **WebSite** unter **Default Web Site** in IIS.  
  
7.  Klicken Sie auf die **Entwurf** Registerkarte am unteren Seitenrand.  
  
8.  Klicken Sie auf die **Toolbox** Registerkarte am linken Rand aus, oder wählen Sie ihn auf die **Ansicht** Menü.  
  
     Die **Toolbox** wird geöffnet.  
  
9. In der **Toolbox**, klicken Sie auf die **Schaltfläche** Steuerelement und fügen es der Hauptentwurfsoberfläche "default.aspx" hinzu.  
  
10. In der **Toolbox**, klicken Sie auf die **Textfeld** steuern, und ziehen Sie das Steuerelement der Hauptentwurfsoberfläche "default.aspx".  
  
11. Doppelklicken Sie auf das abgelegte Button-Steuerelement.  
  
     Dadurch wechseln Sie zur Codepage: Default.aspx.cs bei C# oder Default.aspx.vb bei [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Der Cursor sollte sich in der `Button1_Click`-Funktion befinden.  
  
12. Fügen Sie folgenden Code in die `Button1_Click`-Funktion ein:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Das Projekt wird fehlerfrei erstellt.  
  
     Jetzt können Sie mit dem Debuggen beginnen.  
  
### <a name="to-debug-the-web-form"></a>So debuggen Sie das Web Form  
  
1.  Klicken Sie im Fenster Default.aspx.cs oder Default.aspx.vb auf den linken Rand der Zeile, der Sie Text hinzugefügt haben:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen. Weitere Informationen finden Sie unter [Haltepunkte](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Klicken Sie im Menü **Debuggen** auf **Debuggen starten**.  
  
3.  Die **Debuggen nicht aktiviert** Dialogfeld wird angezeigt. Wählen Sie **ändern Sie die Datei "Web.config" zum Aktivieren des Debuggens** aus, und klicken Sie auf **OK**.  
  
     Internet Explorer wird gestartet, und die zuvor entworfene Seite wird angezeigt.  
  
4.  Klicken Sie im Internet Explorer auf die erstellte Schaltfläche.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gelangen Sie damit in die Zeile, in der Sie den Haltepunkt auf der Codepage Default.aspx.cs oder Default.aspx.vb festlegen. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf einen Befehl.  
  
5.  Auf der **Debuggen** Menü klicken Sie auf **Windows**, klicken Sie dann auf **Überwachen**, und klicken Sie dann auf **Überwachen 1**.  
  
6.  In der **Überwachen** geben **TextBox1.Text**.  
  
     Die **Überwachen** Fenster zeigt den Wert der Variablen `TextBox1.Text`:  
  
    ```  
    ""  
    ```  
  
7.  Auf der **Debuggen** Menü klicken Sie auf **Prozedurschritt**.  
  
     Der Wert der `TextBox1.Text` Änderungen in der **Überwachen** Fenster zum Lesen:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  Auf der **Debuggen** Menü klicken Sie auf **Fortfahren**.  
  
9. Klicken Sie im Internet Explorer erneut auf die erstellte Schaltfläche.  
  
     Die Ausführung hält wieder am Haltepunkt an.  
  
10. Klicken Sie im Fenster Default.aspx.cs bzw. Default.aspx.vb im linken Rand auf den roten Punkt.  
  
     Dadurch wird der Haltpunkt entfernt.  
  
11. Auf der **Debuggen** Menü klicken Sie auf **Beenden des Debuggens**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>So stellen Sie zum Debuggen eine Verbindung mit dem Web Form her  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Für möglichst effektives Debuggen kompilieren Sie die ausführbare Datei als Debugversion mit Symboldateien (.pdb).  
  
2.  Klicken Sie im Fenster Default.aspx.cs bzw. Default.aspx.vb auf den linken Rand der Zeile, um erneut einen Haltepunkt in der hinzugefügten Zeile festzulegen:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  Auf der **Debuggen** Menü klicken Sie auf **Starten ohne Debugging**.  
  
     Das Web Form wird in Internet Explorer gestartet, der Debugger ist jedoch nicht angehängt.  
  
4.  Fügen Sie den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Prozess an. Weitere Informationen finden Sie unter [Debuggen bereitgestellt Webanwendungen](../debugger/debugging-deployed-web-applications.md).  
  
5.  Klicken Sie im Internet Explorer auf die Schaltfläche im Formular.  
  
     In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sollten Sie den Haltepunkt in Default.aspx.cs, Default.aspx.vb oder Default.aspx erreichen.  
  
6.  Wenn Sie fertig sind Debuggen, die **Debuggen** Menü klicken Sie auf **Beenden des Debuggens**.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)