---
title: Öffnen eines dynamischen Werkzeugfensters | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702265"
---
# <a name="open-a-dynamic-tool-window"></a>Öffnen eines dynamischen Werkzeugfensters
Toolfenster werden in der Regel über einen Befehl in einem Menü oder eine entsprechende Tastenkombination geöffnet. Manchmal benötigen Sie jedoch möglicherweise ein Toolfenster, das geöffnet wird, wenn ein bestimmter UI-Kontext angewendet wird, und geschlossen wird, wenn der UI-Kontext nicht mehr angewendet wird. Diese Arten von Toolfenstern werden als *dynamisch* oder *automatisch sichtbar*bezeichnet.

> [!NOTE]
> Eine Liste vordefinierter UI-Kontexte finden Sie unter <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.

 Wenn Sie beim Start ein dynamisches Toolfenster öffnen möchten und die Erstellung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> fehlschlägt, müssen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> die Schnittstelle implementieren und die Fehlerbedingungen in der Methode testen. Damit die Shell weiß, dass Sie über ein dynamisches Toolfenster verfügen, `SupportsDynamicToolOwner` das beim Start geöffnet werden soll, müssen Sie der Paketregistrierung den Wert (auf 1 festgelegt) hinzufügen. Dieser Wert ist nicht <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Teil des Standards , daher müssen Sie ein benutzerdefiniertes Attribut erstellen, um es hinzuzufügen. Weitere Informationen zu benutzerdefinierten Attributen finden Sie unter [Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Verwenden <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Sie diese Datei, um ein Toolfenster zu öffnen. Das Werkzeugfenster wird nach Bedarf erstellt.

> [!NOTE]
> Ein dynamisches Werkzeugfenster kann vom Benutzer geschlossen werden. Wenn Sie einen Menübefehl erstellen möchten, damit der Benutzer das Toolfenster erneut öffnen kann, sollte der Menübefehl in demselben UI-Kontext aktiviert werden, der das Toolfenster öffnet, und andernfalls deaktiviert werden.

## <a name="to-open-a-dynamic-tool-window"></a>So öffnen Sie ein dynamisches Werkzeugfenster

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **DynamicToolWindow,** und fügen Sie eine Vorlagenvorlage für das Toolfenster mit dem Namen *DynamicWindowPane.cs*hinzu. Weitere Informationen finden Sie unter [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

2. Suchen Sie in der *Datei DynamicWindowPanePackage.cs* die DynamicWindowPanePackage-Deklaration. Fügen <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Sie <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> die und die Attribute hinzu, um das Toolfenster zu registrieren.

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

     Die oben genannten Attribute registrieren das Toolfenster mit dem Namen DynamicWindowPane als vorübergehendes Fenster, das beim Schließen und Erneuten Öffnen von Visual Studio nicht beibehalten wird. DynamicWindowPane wird <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> immer dann geöffnet, wenn es angewendet wird, und andernfalls geschlossen.

3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden. Das Toolfenster sollte nicht angezeigt werden.

4. Öffnen Sie ein Projekt in der experimentellen Instanz. Das Werkzeugfenster sollte angezeigt werden.
