---
title: Befehl Implementierung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ed14a65e2839039a9f5c3075dd68498c948a4fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133322"
---
# <a name="command-implementation"></a>Implementierung des Befehls
Um einen Befehl in einem VSPackage implementieren, müssen Sie die folgenden Aufgaben ausführen:  
  
1.  In der VSCT-Datei eine Befehlsgruppe richten Sie ein, und fügen Sie den Befehl hinzu. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)"  
  
2.  Registrieren Sie den Befehl mit Visual Studio.  
  
3.  Implementieren des Befehls.  
  
 In den folgenden Abschnitten wird erläutert, wie die Registrierung und Befehle implementieren.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrieren Befehle mit Visual Studio  
 Wenn der Befehl ist in einem Menü angezeigt werden, müssen Sie Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> zu Ihrem VSPackage und verwenden Sie als Wert entweder den Namen des Menüs oder zugehörige Ressourcen-ID.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Darüber hinaus müssen Sie den Befehl mit Registrieren der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Sie können diesen Dienst abrufen, indem Sie mit der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode, wenn Ihr VSPackage abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Package>.  
  
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
  
## <a name="implementing-commands"></a>Implementieren von Befehlen  
 Es gibt zahlreiche Möglichkeiten, um Befehle zu implementieren. Erstellen Sie gegebenenfalls einen statischen Menübefehl, d. h. einen Befehl, der immer die gleiche Weise und für das gleiche Menü angezeigt wird, den Befehl mit <xref:System.ComponentModel.Design.MenuCommand> wie in den Beispielen im vorherigen Abschnitt gezeigt. Um einen statischen Befehl zu erstellen, müssen Sie einen Ereignishandler bereitstellen, der für die Ausführung des Befehls zuständig ist. Da der Befehl immer aktiviert und sichtbar ist, müssen Sie keinen seinen Status zu Visual Studio bereitstellen. Wenn Sie den Status eines Befehls abhängig von bestimmten Bedingungen ändern möchten, können Sie den Befehl erstellen, als eine Instanz von der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Klasse werden soll, und geben Sie in ihren Konstruktor ein Ereignishandler zum Ausführen des Befehls und einer Abfrage statushandlers benachrichtigt Visual Studio, wenn der Status des Befehls wechselt. Sie können auch implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> als Teil einer Command-Klasse oder implementieren kann <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Wenn Sie einen Befehl als Teil eines Projekts bereitstellen. Die beiden Schnittstellen und die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Klasse, die alle haben, Methoden, mit denen Visual Studio eine Änderung in den Status eines Befehls benachrichtigt, und andere Methoden, die die Ausführung des Befehls bereitstellen.  
  
 Wenn ein Befehl mit dem Befehl Dienst hinzugefügt wird, wird er zu einem eine Kette von Befehlen. Wenn Sie die Status Benachrichtigung und Ausführung von Methoden für den Befehl implementieren, achten Sie darauf, nur für diesen bestimmten Befehl bereitzustellen, und übergeben in allen anderen Fällen bei der anderen Befehle in der Kette. Wenn Sie ein Failover auf den Befehl übergeben werden, auf (in der Regel durch das Zurückgeben von <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio möglicherweise nicht mehr ordnungsgemäß ausgeführt.  
  
## <a name="query-status-methods"></a>Status von Abfragemethoden  
 Wenn Sie entweder implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode oder die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> -Methode, die Kontrollkästchen für die GUID des Befehls, der der Befehl angehört und die ID des Befehls. Befolgen Sie die nachstehenden Richtlinien:  
  
-   Wenn die GUID nicht erkannt wird, muss die Implementierung der beiden Methoden zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Wenn Ihre Implementierung der beiden Methoden erkennt die GUID, jedoch nicht den Befehl implementiert hat, sollte die Methode zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Wenn Ihre Implementierung der beiden Methoden die GUID und der Befehl erkennt, und klicken Sie dann die Methode sollte das Feld Befehlsflags jedes Befehls festgelegt (in der `prgCmds` Parameter) mithilfe der Folgendes <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Flags:  
  
    -   OLECMDF_SUPPORTED – Wenn der Befehl unterstützt wird.  
  
    -   OLECMDF_INVISIBLE – Wenn der Befehl nicht sichtbar sein soll.  
  
    -   OLECMDF_LATCHED – Wenn der Befehl eingeschaltet ist und angezeigt wird, überprüft wurden.  
  
    -   OLECMDF_ENABLED – Wenn der Befehl aktiviert ist.  
  
    -   OLECMDF_DEFHIDEONCTXTMENU – Wenn der Befehl ausgeblendet werden soll, wenn es auf ein Kontextmenü angezeigt wird.  
  
    -   OLECMDF_NINCHED - Wenn mit dem Befehl wird ein Menücontroller und ist nicht aktiviert, aber die Dropdown-Menü-Liste ist nicht leer und wird weiterhin zur Verfügung. (Dieses Kennzeichen werden nur selten verwendet).  
  
-   Wenn der Befehl definiert wurde, in der VSCT-Datei mit dem `TextChanges` kennzeichnen, legen Sie die folgenden Parameter:  
  
    -   Legen Sie die `rgwz` Element von der `pCmdText` Parameter auf den neuen Text des Befehls.  
  
    -   Legen Sie die `cwActual` Element von der `pCmdText` Parameters auf die Länge der Befehlszeichenfolge.  
  
 Stellen Sie außerdem sicher, dass der aktuelle Kontext kein Automatisierungsfunktion, es sei denn, der der Befehl speziell Automatisierungsfunktionen behandeln soll.  
  
 Um anzugeben, dass Sie einen bestimmten Befehl unterstützen, zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Für alle anderen Befehle zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Im folgenden Beispiel wird die Abfragestatus Methode zunächst sichergestellt, dass der Kontext keine Automatisierungsfunktion ist, und sucht nach den richtigen Befehlssatz GUID und Befehls-ID. Der Befehl selbst festgelegt ist, aktiviert und unterstützt werden. Andere Befehle werden unterstützt.  
  
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
  
## <a name="execution-methods"></a>Execution-Methode  
 Implementierung der Execute-Methode ähnelt der Implementierung der Abfragestatus Methode. Stellen Sie zunächst sicher, dass der Kontext ein Automatisierungsfunktion ist. Testen Sie die GUID und die Befehls-ID. Wenn die GUID oder Befehls-ID wird nicht erkannt, zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Um den Befehl zu behandeln, führen Sie sie aus, und zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> Wenn die Ausführung erfolgreich ist. Der Befehl ist verantwortlich für fehlererkennung und die Benachrichtigung. aus diesem Grund geben Sie einen Fehlercode zurück, wenn die Ausführung ein Fehler auftritt. Im folgende Beispiel wird veranschaulicht, wie die excecution-Methode implementiert werden soll.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)