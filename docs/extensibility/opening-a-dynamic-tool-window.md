---
title: Öffnen eines dynamischen Tool Fensters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a06cea6d9de4271572457dc9fe6473b5c969b66
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903705"
---
# <a name="open-a-dynamic-tool-window"></a>Öffnen eines dynamischen Tool Fensters
Tool Fenster werden in der Regel über einen Befehl in einem Menü oder eine entsprechende Tastenkombination geöffnet. Manchmal benötigen Sie jedoch ein Tool Fenster, das geöffnet wird, wenn ein bestimmter UI-Kontext zutrifft, und wird geschlossen, wenn der UI-Kontext nicht mehr zutrifft. Diese Arten von Tool Fenstern werden als *dynamisch* oder *automatisch sichtbar*bezeichnet.

> [!NOTE]
> Eine Liste mit vordefinierten UI-Kontexten finden Sie unter <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> .

 Wenn Sie ein dynamisches Tool Fenster beim Start öffnen möchten und es möglich ist, dass die Erstellung fehlschlägt, müssen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> -Schnittstelle implementieren und die Fehlerbedingungen in der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> Methode testen. Damit die Shell weiß, dass Sie über ein dynamisches Tool Fenster verfügen, das beim Start geöffnet werden sollte, müssen Sie der `SupportsDynamicToolOwner` Paket Registrierung den Wert (1) hinzufügen. Dieser Wert gehört nicht zum Standard <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , daher müssen Sie ein benutzerdefiniertes Attribut erstellen, um es hinzuzufügen. Weitere Informationen zu benutzerdefinierten Attributen finden [Sie unter Verwenden eines benutzerdefinierten Registrierungs Attributs zum Registrieren einer Erweiterung](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Verwenden <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Sie, um ein Tool Fenster zu öffnen. Das Tool Fenster wird nach Bedarf erstellt.

> [!NOTE]
> Ein dynamisches Tool Fenster kann vom Benutzer geschlossen werden. Wenn Sie einen Menübefehl erstellen möchten, damit der Benutzer das Tool Fenster erneut öffnen kann, sollte der Menübefehl im gleichen UI-Kontext aktiviert werden, der das Tool Fenster öffnet, und andernfalls deaktiviert.

## <a name="to-open-a-dynamic-tool-window"></a>So öffnen Sie ein dynamisches Tool Fenster

1. Erstellen Sie ein VSIX-Projekt namens **dynamictoolwindow** , und fügen Sie eine Tool Fenster-Element Vorlage mit dem Namen *DynamicWindowPane.cs*hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).

2. Suchen Sie in der Datei *DynamicWindowPanePackage.cs* die dynamicwindowpanepackage-Deklaration. Fügen Sie <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> die <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> Attribute und zum Registrieren des Tool Fensters hinzu.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Die obigen Attribute registrieren das Tool Fenster mit dem Namen dynamicwindowpane als vorübergehendes Fenster, das nicht persistent ist, wenn Visual Studio geschlossen und erneut geöffnet wird. Dynamicwindowpane wird immer dann geöffnet <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> , wenn angewendet wird, und andernfalls geschlossen.

3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden. Das Tool Fenster sollte nicht angezeigt werden.

4. Öffnen Sie ein Projekt in der experimentellen Instanz. Das Tool Fenster sollte angezeigt werden.
