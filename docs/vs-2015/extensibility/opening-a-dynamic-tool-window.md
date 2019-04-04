---
title: Öffnen eines dynamischen Toolfensters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 80d2666fc40fa561a0e2993ca50edd0dcf72dbc4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961758"
---
# <a name="opening-a-dynamic-tool-window"></a>Öffnen eines dynamischen Toolfensters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toolfenster werden in der Regel von einem Befehl in einem Menü oder eine entsprechende Tastenkombination geöffnet. In einigen Fällen kann jedoch ein Toolfenster erforderlich, das geöffnet wird, wenn ein bestimmten Benutzeroberflächenkontext gilt, und wird geschlossen, wenn der UI-Kontext nicht mehr gilt. Toolfenster, wie diese heißen *dynamische* oder *automatisch sichtbar*.  
  
> [!NOTE]
>  Eine Liste der vordefinierten benutzeroberflächenkontexte, finden Sie unter <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Für die  
  
 Wenn Sie ein dynamischen Toolfensters beim Start zu öffnen und es ist möglich, für die Erstellung fehlschlägt, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> Schnittstelle, und Testen Sie die fehlerbedingungen in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> Methode. In der Reihenfolge für die Shell zu wissen, dass Sie ein dynamisches Tool-Fenster verfügen, die beim Start geöffnet werden soll, müssen Sie Hinzufügen der `SupportsDynamicToolOwner` Wert (auf 1 festgelegt) Ihrer Registrierung des Pakets. Dieser Wert ist nicht Bestandteil des Standards <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, daher müssen Sie ein benutzerdefiniertes Attribut, um es hinzuzufügen, erstellen. Weitere Informationen zu benutzerdefinierten Attributen finden Sie unter [mithilfe eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Verwendung <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> um ein Toolfenster zu öffnen. Das Toolfenster wird erstellt, je nach Bedarf.  
  
> [!NOTE]
>  Ein dynamisches Tool-Fenster kann vom Benutzer geschlossen werden. Sollten Sie einen Menübefehl zu erstellen, damit der Benutzer das Toolfenster öffnen kann, sollte der Menübefehl in den gleichen UI-Kontext aktiviert werden, die die Toolfenster und deaktiviert, die andernfalls geöffnet wird.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Um ein dynamisches Tool-Fenster öffnen  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **DynamicToolWindow** und fügen Sie eine Elementvorlage der Tool-Fenster mit dem Namen **DynamicWindowPane.cs**. Weitere Informationen finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Finden Sie in der Datei DynamicWindowPanePackage.cs die DynamicWindowPanePackage-Deklaration. Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute-Attribute, um das Fenster zu registrieren.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Dadurch wird das Toolfenster, die mit dem Namen DynamicWindowPane als vorübergehende Fenster, die nicht beibehalten wird, wenn Visual Studio geschlossen und erneut geöffnet wird registriert. DynamicWindowPane wird geöffnet. wenn <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> gilt, und andernfalls geschlossen.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden. Das Fenster sollte nicht angezeigt werden.  
  
4.  Öffnen Sie ein Projekt in der experimentellen Instanz ein. Das Fenster sollte angezeigt werden.
