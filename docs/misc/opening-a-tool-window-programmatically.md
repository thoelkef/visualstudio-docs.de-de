---
title: "Programmgesteuertes &#214;ffnen eines Toolfensters | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolfenster, programmgesteuertes Erstellen"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Programmgesteuertes &#214;ffnen eines Toolfensters
Toolfenster werden in der Regel geöffnet, indem Sie auf einen Befehl in einem Menü klicken oder eine entsprechende Tastenkombination drücken. Vielleicht müssen Sie ein Toolfenster aber auch programmgesteuert öffnen, wie dies beim Befehlshandler der Fall ist.  
  
 Um ein Toolfenster im verwalteten VSPackage zu öffnen, von dem es bereitgestellt wird, verwenden Sie <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>. Um ein Toolfenster in einem anderen VSPackage zu öffnen, verwenden Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>. In beiden Fällen wird das Toolfenster nach Bedarf erstellt.  
  
 Der folgende Code stammt aus dem C\#\-Beispiel "Reference.ToolWindow".  
  
### So öffnen Sie ein Toolfenster programmgesteuert  
  
1.  Erstellen Sie den Bereich und Rahmen des Toolfensters und das VSPackage, von dem sie implementiert werden. Weitere Informationen finden Sie unter [Hinzufügen eines Toolfensters](../extensibility/adding-a-tool-window.md).  
  
2.  Fügen Sie <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> dem VSPackage hinzu, von dem es bereitgestellt wird.  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     Dadurch wird das Toolfenster PersistedWindowPane so registriert, dass es als am **Projektmappen\-Explorer** angedocktes Fenster geöffnet wird. Weitere Informationen finden Sie unter [Registrieren ein Toolfenster](../extensibility/registering-a-tool-window.md).  
  
3.  Verwenden Sie <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>, um den Toolfensterbereich zu suchen oder zu erstellen, falls er noch nicht vorhanden ist.  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  Rufen Sie den Toolfensterrahmen aus dem Toolfensterbereich ab.  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  Zeigen Sie das Toolfenster an.  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```