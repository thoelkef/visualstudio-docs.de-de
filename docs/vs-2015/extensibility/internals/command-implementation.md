---
title: Befehl Implementierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cd48e7338823c94ad9a16f1b087daac6abe8f6e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957050"
---
# <a name="command-implementation"></a>Befehlsimplementierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um einen Befehl in einem VSPackage implementieren, müssen Sie die folgenden Aufgaben ausführen:  
  
1. In der VSCT-Datei eine Befehlsgruppe richten Sie ein, und fügen Sie den Befehl hinzu. Weitere Informationen finden Sie unter [Visual Studio Command Table (. VSCT) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)"  
  
2. Registrieren Sie den Befehl in Visual Studio.  
  
3. Implementieren Sie den Befehl.  
  
   In den folgenden Abschnitten wird erläutert, wie registrieren und Befehle implementieren.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrieren Befehle mit Visual Studio  
 Wenn der Befehl ist in einem Menü angezeigt werden, müssen Sie Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Ihre VSPackage, und verwenden Sie als Wert entweder der Name des Menüs oder zugehörige Ressourcen-ID.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Darüber hinaus müssen Sie den Befehl mit Registrieren der <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Sie können diesen Dienst abrufen, indem Sie mit der <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode, wenn das VSPackage abgeleitet wird <xref:Microsoft.VisualStudio.Shell.Package>.  
  
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
 Es gibt eine Reihe von Möglichkeiten, um Befehle zu implementieren. Wenn Sie möchten einen statischen Menü-Befehl, das einen Befehl, immer die gleiche Weise und im gleichen Menü angezeigt wird, erstellen Sie den Befehl mithilfe <xref:System.ComponentModel.Design.MenuCommand> wie in den Beispielen im vorherigen Abschnitt gezeigt. Um einen statischen Befehl zu erstellen, müssen Sie einen Ereignishandler bereitstellen, der für die Ausführung des Befehls zuständig ist. Da der Befehl immer aktiviert und sichtbar ist, müssen Sie nicht den Status für Visual Studio bereitstellen. Wenn Sie den Status eines Befehls basierend auf bestimmten Bedingungen ändern möchten, können Sie den Befehl erstellen, als eine Instanz der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Klasse, und geben Sie in seinem Konstruktor, einen Ereignishandler zum Ausführen des Befehls und einem Abfrage-Status-Handler, benachrichtigt Visual Studio, wenn sich der Status des Befehls ändert. Sie können auch implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> als Teil einer Command-Klasse oder implementieren kann <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Wenn Sie einen Befehl als Teil eines Projekts bereitstellen. Die beiden Schnittstellen und die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Klasse, die alle verfügen über Methoden, die Visual Studio über eine Änderung in den Status eines Befehls zu benachrichtigen und andere Methoden, die die Ausführung des Befehls bereitstellen.  
  
 Wenn der Befehlsdienst ein Befehl hinzugefügt wird, wird eine von einer Kette von Befehlen. Wenn Sie die Status-Benachrichtigung und die Ausführung von Methoden für den Befehl implementieren, müssen sicherstellen Sie, nur für diesen speziellen Befehl bereitzustellen und allen anderen Fällen, bei der anderen Befehle in der Kette zu übergeben. Wenn Sie nicht den Befehl übergeben (in der Regel durch das Zurückgeben von <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio möglicherweise nicht mehr ordnungsgemäß ausgeführt.  
  
## <a name="query-status-methods"></a>Status von Abfragemethoden  
 Wenn Sie entweder implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode oder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> -Methode, die Kontrollkästchen für die GUID des Befehls, der der Befehl angehört und die ID des Befehls. Befolgen Sie die nachstehenden Richtlinien:  
  
- Wenn die GUID nicht erkannt wird, muss Ihre Implementierung der beiden Methoden zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Wenn Ihre Implementierung der beiden Methoden erkennt die GUID, jedoch den Befehl tatsächlich nicht implementiert hat, sollte die Methode zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Wenn Ihre Implementierung der beiden Methoden, sowohl die GUID und der Befehl erkennt, und klicken Sie dann die Methode sollte das Feld Befehlsflags der jeden Befehl festgelegt (in der `prgCmds` Parameter) mithilfe der folgenden Flags:  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl unterstützt wird.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl nicht sichtbar sein soll.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl eingeschaltet ist, und es wird angezeigt, die überprüft wurden.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl aktiviert ist.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl ausgeblendet werden soll, wenn sie ein Kontextmenü angezeigt wird.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl ist ein Menücontroller und ist nicht aktiviert, aber die Dropdown-Menü-Liste ist nicht leer, und ist weiterhin verfügbar. (Dieses Flag wird nur selten verwendet).  
  
- Wenn der Befehl definiert wurde, in der VSCT-Datei mit den `TextChanges` kennzeichnen, legen Sie die folgenden Parameter:  
  
  -   Legen Sie die `rgwz` Element der `pCmdText` Parameter, um den neuen Text des Befehls.  
  
  -   Legen Sie die `cwActual` Element der `pCmdText` Parameter, um die Größe der Befehlszeichenfolge.  
  
  Stellen Sie außerdem sicher, dass der aktuelle Kontext keiner Automatisierungsfunktion, es sei denn, der Befehl dient speziell Automatisierungsfunktionen behandeln.  
  
  Um anzugeben, dass Sie einen bestimmten Befehl unterstützen, zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Für alle anderen Befehle zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
  Im folgenden Beispiel wird die Abfragestatus Methode zunächst sichergestellt, dass der Kontext kein Automatisierungsfunktion ist, und sucht nach den richtigen Befehlssatz GUID und Befehls-ID Der Befehl selbst festgelegt ist, aktiviert und unterstützt werden. Es werden keine weiteren Befehle unterstützt.  
  
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
 Implementierung der Execute-Methode ähnelt die Implementierung der Abfrage-Status-Methode. Stellen Sie zunächst sicher, dass der Kontext kein Automatisierungsfunktion ist. Testen Sie dann für die GUID und Befehls-ID. Wenn die GUID oder die Befehls-ID wurde nicht erkannt, zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Um den Befehl behandeln zu können, führen Sie es aus, und zurückgeben <xref:Microsoft.VisualStudio.VSConstants.S_OK> Wenn die Ausführung erfolgreich ist. Der Befehl ist für die fehlererkennung und die Benachrichtigung verantwortlich; aus diesem Grund geben Sie einen Fehlercode zurück, wenn die Ausführung ein Fehler auftritt. Im folgende Beispiel wird veranschaulicht, wie die Execution-Methode implementiert werden soll.  
  
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
