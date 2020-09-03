---
title: Befehls Implementierung | Microsoft-Dokumentation
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
ms.openlocfilehash: a208fabd3d205793763698cde0f6fe367c7bb8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195059"
---
# <a name="command-implementation"></a>Befehlsimplementierung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zum Implementieren eines Befehls in einem VSPackage müssen Sie die folgenden Aufgaben ausführen:  
  
1. Richten Sie in der vsct-Datei eine Befehlsgruppe ein, und fügen Sie dann den Befehl hinzu. Weitere Informationen finden Sie unter [Visual Studio Command Table (. Vsct-Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
  
2. Registrieren Sie den Befehl bei Visual Studio.  
  
3. Implementieren Sie den-Befehl.  
  
   In den folgenden Abschnitten wird erläutert, wie Befehle registriert und implementiert werden.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrieren von Befehlen mit Visual Studio  
 Wenn der Befehl in einem Menü angezeigt werden soll, müssen Sie dem <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage hinzufügen und als Wert entweder den Namen des Menüs oder die zugehörige Ressourcen-ID verwenden.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Außerdem müssen Sie den Befehl beim Registrieren <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . Sie können diesen Dienst mithilfe der-Methode erhalten, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Wenn das VSPackage von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Package> .  
  
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
 Es gibt eine Reihe von Möglichkeiten, Befehle zu implementieren. Wenn Sie einen statischen Menübefehl verwenden möchten, bei dem es sich um einen Befehl handelt, der immer auf dieselbe Weise und im gleichen Menü angezeigt wird, erstellen Sie den Befehl mithilfe von, <xref:System.ComponentModel.Design.MenuCommand> wie in den Beispielen im vorherigen Abschnitt gezeigt. Zum Erstellen eines statischen Befehls müssen Sie einen Ereignishandler bereitstellen, der für die Ausführung des Befehls zuständig ist. Da der Befehl immer aktiviert und sichtbar ist, müssen Sie seinen Status nicht für Visual Studio angeben. Wenn Sie den Status eines Befehls in Abhängigkeit von bestimmten Bedingungen ändern möchten, können Sie den Befehl als Instanz der <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> -Klasse erstellen und in seinem Konstruktor einen Ereignishandler zum Ausführen des Befehls und einen Abfrage Status Handler zum Benachrichtigen von Visual Studio bereitstellen, wenn sich der Status des Befehls ändert. Sie können auch <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> als Teil einer Befehls Klasse oder implementieren, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Wenn Sie einen Befehl als Teil eines Projekts bereitstellen. Die beiden Schnittstellen und die- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Klasse verfügen über Methoden, die Visual Studio über eine Änderung des Status eines Befehls Benachrichtigen, sowie über andere Methoden, die die Ausführung des Befehls bereitstellen.  
  
 Wenn dem Befehls Dienst ein Befehl hinzugefügt wird, wird er zu einer Kette von Befehlen. Wenn Sie die Status-und Ausführungsmethoden für den Befehl implementieren, achten Sie darauf, nur für diesen bestimmten Befehl bereitzustellen und alle anderen Fälle an die anderen Befehle in der Kette zu übergeben. Wenn Sie den Befehl nicht übergeben (normalerweise durch Zurückgeben von <xref:Microsoft.VisualStudio.OLE.Interop.Constants> ), wird Visual Studio möglicherweise nicht mehr ordnungsgemäß ausgeführt.  
  
## <a name="query-status-methods"></a>Abfrage Status Methoden  
 Wenn Sie entweder die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode oder die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> Methode implementieren, überprüfen Sie, ob die GUID des Befehlssatzes, zu dem der Befehl gehört, und die ID des Befehls ist. Beachten Sie diese Vorgaben:  
  
- Wenn die GUID nicht erkannt wird, muss die Implementierung der beiden Methoden zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Wenn die Implementierung einer der beiden Methoden die GUID erkennt, aber den-Befehl nicht tatsächlich implementiert hat, sollte die-Methode zurückgeben <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
- Wenn die Implementierung einer der beiden Methoden sowohl die GUID als auch den Befehl erkennt, sollte die-Methode das Befehlsflags-Feld jedes Befehls (im- `prgCmds` Parameter) mithilfe der folgenden Flags festlegen:  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , wenn der Befehl unterstützt wird.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , wenn der Befehl nicht sichtbar sein soll.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , wenn der Befehl aktiviert ist und angezeigt wird.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , wenn der Befehl aktiviert ist.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , wenn der Befehl ausgeblendet werden soll, wenn er in einem Kontextmenü angezeigt wird.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Wenn der Befehl ein Menü Controller ist und nicht aktiviert ist, ist die Dropdown Menü Liste nicht leer und noch verfügbar. (Dieses Flag wird nur selten verwendet.)  
  
- Wenn der Befehl in der vsct-Datei mit dem-Flag definiert wurde `TextChanges` , legen Sie die folgenden Parameter fest:  
  
  - Legen Sie das- `rgwz` Element des- `pCmdText` Parameters auf den neuen Text des Befehls fest.  
  
  - Legen Sie das- `cwActual` Element des- `pCmdText` Parameters auf die Größe der Befehls Zeichenfolge fest.  
  
  Stellen Sie außerdem sicher, dass es sich beim aktuellen Kontext nicht um eine Automatisierungsfunktion handelt, es sei denn, der Befehl ist speziell für die Handhabung von Automatisierungsfunktionen vorgesehen  
  
  Um anzugeben, dass Sie einen bestimmten Befehl unterstützen, geben Sie zurück <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Geben Sie für alle anderen Befehle zurück <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
  Im folgenden Beispiel stellt die Query-Status-Methode zunächst sicher, dass es sich bei dem Kontext nicht um eine Automatisierungsfunktion handelt, und findet dann die korrekte Befehlssatz-GUID und Befehls-ID. Der Befehl selbst ist so festgelegt, dass er aktiviert und unterstützt wird. Weitere Befehle werden nicht unterstützt.  
  
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
  
## <a name="execution-methods"></a>Ausführungsmethoden  
 Die Implementierung der Execute-Methode ähnelt der Implementierung der Query-Status-Methode. Stellen Sie zunächst sicher, dass es sich bei dem Kontext nicht um eine Automatisierungsfunktion handelt. Testen Sie dann sowohl die GUID als auch die Befehls-ID. Wenn die GUID oder Befehls-ID nicht erkannt wird, geben Sie zurück <xref:Microsoft.VisualStudio.OLE.Interop.Constants> .  
  
 Um den Befehl zu verarbeiten, führen Sie ihn aus und geben zurück, <xref:Microsoft.VisualStudio.VSConstants.S_OK> Wenn die Ausführung erfolgreich ist. Der Befehl ist für die Fehlererkennung und-Benachrichtigung verantwortlich. Daher wird ein Fehlercode zurückgegeben, wenn die Ausführung fehlschlägt. Im folgenden Beispiel wird veranschaulicht, wie die Ausführungs Methode implementiert werden sollte.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
