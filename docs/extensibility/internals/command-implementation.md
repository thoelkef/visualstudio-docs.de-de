---
title: "Befehl-Implementierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Befehle, die Implementierung"
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Befehl-Implementierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um einen Befehl in einem VSPackage implementieren, müssen Sie die folgenden Aufgaben ausführen:  
  
1.  In der VSCT\-Datei eine Befehlsgruppe einrichten und dann den Befehl hinzuzufügen. Weitere Informationen finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)"  
  
2.  Registrieren Sie den Befehl mit Visual Studio.  
  
3.  Implementieren Sie den Befehl.  
  
 In den folgenden Abschnitten wird erläutert, wie zum Registrieren und Befehle implementieren werden.  
  
## Registrieren Befehle mit Visual Studio  
 Wenn der Befehl ist in einem Menü angezeigt werden, müssen Sie Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage und verwenden Sie als Wert den Namen des Menüs oder zugehörige Ressourcen\-ID.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Darüber hinaus müssen Sie den Befehl mit Registrieren der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Sie erhalten diesen Dienst mithilfe der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode, wenn das VSPackage abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## Implementieren von Befehlen  
 Es gibt verschiedene Arten, um Befehle zu implementieren. Sie ggf. einen statischen Befehl, die einen Befehl immer die gleiche Weise und im gleichen Menü angezeigt wird, erstellen Sie den Befehl mit <xref:System.ComponentModel.Design.MenuCommand> wie in den Beispielen im vorherigen Abschnitt gezeigt. Um einen statischen Befehl zu erstellen, müssen Sie einen Ereignishandler bereitstellen, der für die Ausführung des Befehls verantwortlich ist. Da der Befehl immer aktiviert und sichtbar ist, müssen Sie keinen seinen Status zu Visual Studio bereitstellen. Wenn Sie den Status eines Befehls je nach Umständen ändern möchten, können Sie den Befehl erstellen, als eine Instanz der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \-Klasse und in seinem Konstruktor bereitstellen, einen Ereignishandler zum Ausführen des Befehls und einen Handler Status Abfragen, Visual Studio zu benachrichtigen, wenn der Status des Befehls ändert. Sie können auch implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> als Teil einer Command\-Klasse oder implementieren kann <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Wenn Sie einen Befehl als Teil eines Projekts bereitstellen. Die beiden Schnittstellen und die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Klasse alle Methoden, die Visual Studio ändert den Status eines Befehls zu benachrichtigen und anderen Methoden, die Ausführung des Befehls zu haben.  
  
 Wenn ein Befehl an den Dienst Befehl hinzugefügt wird, wird es einem eine Kette von Befehlen. Wenn Sie die Status\-Benachrichtigung und die Ausführung von Methoden für den Befehl implementieren, achten Sie darauf, nur für diesen speziellen Befehl bereitzustellen und in allen anderen Fällen bei der anderen Befehle in der Kette zu übergeben. Wenn Sie nicht mit dem Befehl übergeben \(in der Regel durch das Zurückgeben von <xref:Microsoft.VisualStudio.OLE.Interop.Constants>\), Visual Studio möglicherweise nicht mehr ordnungsgemäß funktionieren.  
  
## Status von Abfragemethoden  
 Wenn Sie entweder implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \-Methode oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> \-Methode und die GUID des Befehls, der mit dem Befehl angehört und die ID des Befehls. Richtlinien Sie die folgenden:  
  
-   Wenn die GUID nicht erkannt wird, muss die Implementierung der beiden Methoden zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
-   Wenn die Implementierung der beiden Methoden erkennt die GUID, jedoch mit dem Befehl tatsächlich nicht implementiert hat, sollte die Methode zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
-   Wenn die Implementierung der beiden Methoden die GUID und den Befehl erkennt, und klicken Sie dann die Methode sollte der Befehl Kennzeichenfeld jedes Befehls festgelegt \(in der `prgCmds` Parameter\) mit den folgenden Flags:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl unterstützt wird.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl nicht sichtbar sein soll.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl auf umschaltet und scheinbar überprüft wurden.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl aktiviert ist.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl ausgeblendet werden soll, wenn sie in einem Kontextmenü angezeigt wird.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl ist ein Domänencontroller im Menü und ist nicht aktiviert, aber die Dropdown\-Menü\-Liste ist nicht leer und ist weiterhin verfügbar. \(Dieses Flag wird nur selten verwendet\).  
  
-   Wenn der Befehl definiert wurde, in der VSCT\-Datei mit dem `TextChanges` kennzeichnen, legen Sie die folgenden Parameter:  
  
    -   Festlegen der `rgwz` Bestandteil der `pCmdText` Parameter, um den neuen Text des Befehls.  
  
    -   Legen Sie die `cwActual` Bestandteil der `pCmdText` Parameter, um die Größe der Befehlszeichenfolge.  
  
 Stellen Sie außerdem sicher, dass der aktuelle Kontext keiner Automatisierungsfunktion, es sei denn, der Befehl dient speziell Automatisierungsfunktionen behandeln.  
  
 Um anzugeben, dass Sie einen bestimmten Befehl unterstützen, zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Für alle anderen Befehle zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Im folgenden Beispiel wird die Abfragestatus Methode zunächst sichergestellt, dass Kontext keine Automatisierungsfunktion ist, dann den richtigen Befehlssatz GUID und Befehls\-ID. findet Der Befehl selbst festgelegt ist, aktiviert und unterstützt werden. Es werden keine weiteren Befehle unterstützt.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## Execution\-Methode  
 Implementierung der Execute\-Methode ähnelt die Implementierung der Methode mit dem Abfrage\-Status. Vergewissern Sie sich, dass der Kontext eine Automatisierungsfunktion ist. Prüfen Sie, ob die GUID und die Befehls\-ID. Wenn die GUID oder Befehls\-ID wird nicht erkannt, zurück <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Behandeln Sie den Befehl ausführen und zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> Wenn die Ausführung erfolgreich ist. Der Befehl ist verantwortlich für die Erkennung und Benachrichtigung. Daher geben einen Fehlercode zurück, wenn die Ausführung ein Fehler auftritt. Im folgende Beispiel wird veranschaulicht, wie die Execution\-Methode implementiert werden soll.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)