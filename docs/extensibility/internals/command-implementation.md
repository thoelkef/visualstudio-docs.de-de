---
title: Befehlsimplementierung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709580"
---
# <a name="command-implementation"></a>Befehlsimplementierung
Um einen Befehl in einem VSPackage zu implementieren, müssen Sie die folgenden Aufgaben ausführen:

1. Richten Sie in der *.vsct-Datei* eine Befehlsgruppe ein, und fügen Sie dann den Befehl hinzu. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellendateien (.vsct) .](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Registrieren Sie den Befehl bei Visual Studio.

3. Implementieren Sie den Befehl.

In den folgenden Abschnitten wird erläutert, wie Befehle registriert und implementiert werden.

## <a name="register-commands-with-visual-studio"></a>Registrieren von Befehlen bei Visual Studio
 Wenn Ihr Befehl in einem Menü angezeigt <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> werden soll, müssen Sie die zu Ihrem VSPackage hinzufügen und als Wert entweder den Namen des Menüs oder seine Ressourcen-ID verwenden.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Darüber hinaus müssen Sie den <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>Befehl bei registrieren. Sie können diesen Dienst <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> mithilfe der Methode abrufen, <xref:Microsoft.VisualStudio.Shell.Package>wenn Ihr VSPackage von abgeleitet ist.

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

## <a name="implement-commands"></a>Implementieren von Befehlen
 Es gibt eine Reihe von Möglichkeiten, Befehle zu implementieren. Wenn Sie einen statischen Menübefehl verwenden möchten, bei dem es sich um einen <xref:System.ComponentModel.Design.MenuCommand> Befehl handelt, der immer auf die gleiche Weise und im gleichen Menü angezeigt wird, erstellen Sie den Befehl, indem Sie ihn wie in den Beispielen im vorherigen Abschnitt gezeigt verwenden. Um einen statischen Befehl zu erstellen, müssen Sie einen Ereignishandler bereitstellen, der für die Ausführung des Befehls verantwortlich ist. Da der Befehl immer aktiviert und sichtbar ist, müssen Sie Visual Studio seinen Status nicht bereitstellen. Wenn Sie den Status eines Befehls abhängig von bestimmten Bedingungen ändern möchten, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> können Sie den Befehl als Instanz der Klasse erstellen `QueryStatus` und in ihrem Konstruktor einen Ereignishandler zum Ausführen des Befehls und einen Handler bereitstellen, um Visual Studio zu benachrichtigen, wenn sich der Status des Befehls ändert. Sie können <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> auch als Teil einer Befehlsklasse <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oder implementieren, wenn Sie einen Befehl als Teil eines Projekts bereitstellen. Die beiden Schnittstellen <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> und die Klasse verfügen alle über Methoden, die Visual Studio über eine Änderung des Status eines Befehls benachrichtigen, und andere Methoden, die die Ausführung des Befehls bereitstellen.

 Wenn dem Befehlsdienst ein Befehl hinzugefügt wird, wird er zu einer Befehlskette. Wenn Sie die Statusbenachrichtigungs- und Ausführungsmethoden für den Befehl implementieren, achten Sie darauf, nur für diesen bestimmten Befehl bereitzustellen und alle anderen Anfragen an die anderen Befehle in der Kette weiterzugeben. Wenn Sie den Befehl nicht weiterleiten <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>(in der Regel durch Rückgabe), funktioniert Visual Studio möglicherweise nicht mehr ordnungsgemäß.

## <a name="querystatus-methods"></a>QueryStatus-Methoden
 Wenn Sie entweder <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> die Methode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> oder die Methode implementieren, überprüfen Sie die GUID des Befehlssatzes, zu dem der Befehl gehört, und die ID des Befehls. Befolgen Sie die nachstehenden Richtlinien:

- Wenn die GUID nicht erkannt wird, muss <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>Ihre Implementierung einer der beiden Methoden zurückgegeben werden.

- Wenn Ihre Implementierung einer der beiden Methoden die GUID erkennt, aber <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>den Befehl nicht implementiert hat, sollte die Methode zurückgeben.

- Wenn Ihre Implementierung einer der beiden Methoden sowohl die GUID als auch den Befehl erkennt, `prgCmds` sollte die Methode <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> das Befehlsflagsfeld jedes Befehls (im Parameter) mithilfe der folgenden Flags festlegen:

  - `OLECMDF_SUPPORTED`: Der Befehl wird unterstützt.

  - `OLECMDF_INVISIBLE`: Der Befehl sollte nicht sichtbar sein.

  - `OLECMDF_LATCHED`: Der Befehl wird eingeschaltet und scheint aktiviert worden zu sein.

  - `OLECMDF_ENABLED`: Der Befehl ist aktiviert.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Der Befehl sollte ausgeblendet werden, wenn er in einem Kontextmenü angezeigt wird.

  - `OLECMDF_NINCHED`: Der Befehl ist ein Menücontroller und ist nicht aktiviert, aber seine Dropdown-Menüliste ist nicht leer und ist immer noch verfügbar. (Dieses Flag wird selten verwendet.)

- Wenn der Befehl in der *.vsct-Datei* mit dem `TextChanges` Flag definiert wurde, legen Sie die folgenden Parameter fest:

  - Legen `rgwz` Sie das `pCmdText` Element des Parameters auf den neuen Text des Befehls fest.

  - Legen `cwActual` Sie das `pCmdText` Element des Parameters auf die Größe der Befehlszeichenfolge fest.

Stellen Sie außerdem sicher, dass der aktuelle Kontext keine Automatisierungsfunktion ist, es sei denn, Ihr Befehl ist speziell für die Verarbeitung von Automatisierungsfunktionen vorgesehen.

Um anzugeben, dass Sie einen <xref:Microsoft.VisualStudio.VSConstants.S_OK>bestimmten Befehl unterstützen, geben Sie zurück. Geben Sie für <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>alle anderen Befehle zurück.

Im folgenden Beispiel `QueryStatus` stellt die Methode zunächst sicher, dass der Kontext keine Automatisierungsfunktion ist, und findet dann die richtige Befehlssatz-GUID und Befehls-ID. Der Befehl selbst ist so eingestellt, dass er aktiviert und unterstützt wird. Es werden keine weiteren Befehle unterstützt.

```csharp
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
 Die Implementierung `Exec` der Methode ähnelt `QueryStatus` der Implementierung der Methode. Stellen Sie zunächst sicher, dass der Kontext keine Automatisierungsfunktion ist. Testen Sie dann sowohl die GUID als auch die Befehls-ID. Wenn die GUID oder Befehls-ID nicht erkannt wird, geben Sie zurück. <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>

 Um den Befehl zu behandeln, führen Sie ihn aus, und geben Sie zurück, <xref:Microsoft.VisualStudio.VSConstants.S_OK> wenn die Ausführung erfolgreich ist. Ihr Befehl ist für die Fehlererkennung und -benachrichtigung verantwortlich. Geben Sie daher einen Fehlercode zurück, wenn die Ausführung fehlschlägt. Im folgenden Beispiel wird veranschaulicht, wie die Ausführungsmethode implementiert werden soll.

```csharp
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

- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
