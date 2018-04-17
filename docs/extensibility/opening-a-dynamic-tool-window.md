---
title: Öffnen eine dynamische Toolfenster | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd3a4a8d85ed7d0f5884e7f11b8778eb3b420a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="opening-a-dynamic-tool-window"></a>Öffnen eine dynamische Toolfenster
Toolfenster werden in der Regel über einen Befehl in einem Menü oder eine entsprechende Tastenkombination geöffnet. In einigen Fällen kann jedoch ein Toolfenster erforderlich, das geöffnet wird, wenn eine bestimmte Benutzeroberflächenkontext gilt, und wird geschlossen, wenn der UI-Kontext nicht mehr gilt. Diese Typen von Toolfenstern heißen *dynamische* oder *automatisch sichtbar*.  
  
> [!NOTE]
>  Eine Liste der vordefinierten UI Kontexte, finden Sie unter <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Für die  
  
 Wenn Sie beim Start eine dynamische Toolfenster öffnen möchten und es ist möglich, für die Erstellung fehlschlägt, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> Schnittstelle, und Testen Sie die fehlerbedingungen in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> Methode. In der Reihenfolge für die Befehlsshell zu wissen, dass Sie eine dynamische Toolfenster verfügen, die beim Start geöffnet werden soll, fügen Sie der `SupportsDynamicToolOwner` Wert (1) an Ihrer Registrierung des Pakets. Dieser Wert ist nicht Teil des Standards <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, daher müssen Sie ein benutzerdefiniertes Attribut, um sie hinzuzufügen erstellen. Weitere Informationen zu benutzerdefinierten Attributen finden Sie unter [Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Verwendung <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> um ein Toolfenster zu öffnen. Das Toolfenster wird erstellt, je nach Bedarf.  
  
> [!NOTE]
>  Eine dynamische Toolfenster kann vom Benutzer geschlossen werden. Wenn Sie möchten einen Menübefehl zu erstellen, damit der Benutzer das Toolfenster öffnen kann, sollte der Menübefehl in demselben Kontext UI aktiviert werden, die die Toolfenster und deaktiviert, andernfalls wird geöffnet.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Um eine dynamische Toolfenster zu öffnen.  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **DynamicToolWindow** und fügen Sie eine Elementvorlage für Tool-Fenster mit dem Namen **DynamicWindowPane.cs**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Finden Sie in der Datei DynamicWindowPanePackage.cs die DynamicWindowPanePackage-Deklaration. Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> Attribute das Toolfenster registrieren.  
  
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
  
     Die oben genannten Attribute registrieren Sie das Toolfenster, die mit dem Namen DynamicWindowPane als vorübergehender Fenster, die nicht beibehalten wird, wenn Visual Studio geschlossen und erneut geöffnet wird. DynamicWindowPane wird geöffnet, wenn <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> gilt, und andernfalls geschlossen.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden. Das Toolfenster sollte nicht angezeigt werden.  
  
4.  Öffnen Sie ein Projekt in der experimentellen Instanz ein. Das Toolfenster sollte angezeigt werden.