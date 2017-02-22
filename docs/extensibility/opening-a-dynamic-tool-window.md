---
title: "&#214;ffnen ein dynamisches Tool-Fenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolfenster, dynamische"
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# &#214;ffnen ein dynamisches Tool-Fenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Toolfenster werden in der Regel über einen Befehl in einem Menü oder eine entsprechende Tastenkombination geöffnet. Manchmal kann es jedoch, ein Toolfenster erforderlich, das geöffnet wird, wenn einem bestimmten Benutzeroberflächenkontext gilt, wird geschlossen, wenn der UI\-Kontext nicht mehr gilt. Toolfenster wie diese heißen *dynamische* oder *Auto sichtbare*.  
  
> [!NOTE]
>  Eine Liste der vordefinierten Benutzeroberflächen\-Kontexte, finden Sie unter <xref:Microsoft.VisualStudio.VSConstants.UIContext>. Für die  
  
 Wenn ein dynamisches Tool\-Fenster beim Start geöffnet werden soll und es ist möglich, dass beim Erstellen, müssen Sie implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> Schnittstelle, und Testen Sie die Fehlerzustände in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> Methode. In der Reihenfolge für die Shell zu erkennen, dass ein dynamisches Tool\-Fenster, die beim Start geöffnet werden soll, fügen Sie der `SupportsDynamicToolOwner` Wert \(1\) Paket registrieren. Dieser Wert ist nicht Teil der standardmäßigen <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, daher müssen Sie ein benutzerdefiniertes Attribut, um es hinzuzufügen erstellen. Weitere Informationen zu benutzerdefinierten Attributen finden Sie unter [Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Verwendung <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> um ein Fenster zu öffnen. Das Toolfenster wird bei Bedarf erstellt.  
  
> [!NOTE]
>  Der Benutzer kann ein dynamisches Tool\-Fenster geschlossen werden. Sollten Sie einen Menübefehl zu erstellen, damit der Benutzer das Toolfenster öffnen kann, sollte der Menübefehl in demselben Kontext der Benutzeroberfläche aktiviert werden, die die Toolfenster und deaktiviert, andernfalls wird geöffnet.  
  
### Um ein dynamisches Tool\-Fenster öffnen  
  
1.  Erstellen Sie ein VSIX\-Projekt namens **DynamicToolWindow** und fügen Sie eine Elementvorlage der Tool\-Fenster mit dem Namen **DynamicWindowPane.cs**. Weitere Informationen finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Suchen Sie in der Datei DynamicWindowPanePackage.cs die DynamicWindowPanePackage Deklaration. Hinzufügen der <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute\-Attribute, um das Toolfenster zu registrieren.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)] [PackageRegistration(UseManagedResourcesOnly = true)] [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About [ProvideMenuResource("Menus.ctmenu", 1)] [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))] [Guid(DynamicWindowPanePackageGuids.PackageGuidString)] public sealed class DynamicWindowPanePackage : Package {. . .}  
    ```  
  
     Auf diese Weise registriert das Toolfenster namens DynamicWindowPane als vorübergehende Fenster, die nicht beibehalten wird, wenn Visual Studio geschlossen und erneut geöffnet wird. DynamicWindowPane wird geöffnet, wenn <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> angewendet wird, und andernfalls geschlossen.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden. Sie werden nur das Toolfenster angezeigt.  
  
4.  Öffnen Sie ein Projekt in der experimentellen Instanz ein. Sollte das Toolfenster angezeigt werden.