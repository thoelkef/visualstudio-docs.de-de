---
title: "Verwalten der Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolbox [Visual Studio SDK], automatische Registerkartenauswahl"
  - "Toolbox [Visual Studio SDK], Verwalten"
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# Verwalten der Toolbox
Das [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ermöglicht einem VSPackage, z. B. einem Editor oder Designer, die Mitgliedschaft in und Darstellung der **Toolbox** zu verwalten.  
  
 Darüber hinaus kann die **Toolbox** selbst mittels Automatisierung verwaltet werden. Weitere Informationen zum Verwalten einer Toolbox mittels Automatisierung finden Sie unter [Gewusst wie: Steuern der Toolbox](../Topic/How%20to:%20Control%20the%20Toolbox.md).  
  
## Automatische Toolbox\-Registerkartenauswahl  
 Eine bestimmte Registerkarte oder Kategorie der **Toolbox** kann automatisch basierend auf dem aktuell aktiven Editor oder Designer aktiviert werden. Wenn z. B. ein Forms\-Designer aktiviert ist, soll möglicherweise die Registerkarte **Alle Windows Forms** ausgewählt sein.  
  
 Die Unterstützung ist begrenzt auf Editoren und Designer, die Folgendes erfordern:  
  
1.  Die Implementierung eines Factoryobjekts zum Bereitstellen von Instanzen des Editors oder Designers. Weitere Informationen zum Implementieren von einem Designer\- oder Editor\-Factoryobjekt finden Sie unter [Editor\-Factorys](../extensibility/editor-factories.md).  
  
2.  Die Registrierung der Toolbox\-Registerkarte, die automatisch aktiviert wird, wenn der Editor bzw. Designer angezeigt wird.  
  
## Steuern der Toolbox  
 Durch Erweiterung der Automatisierungsunterstützung stellt das [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] folgende Schnittstellen bereit, damit VSPackages die Verwaltung der **Toolbox** besser steuern können.  
  
|Schnittstelle|Beschreibung|  
|-------------------|------------------|  
|<xref:System.Drawing.Design.IToolboxService>|Ermöglicht Anwendungen, <xref:System.Drawing.Design.ToolboxItem>\-Objekte in der **Toolbox** zu verwalten, hinzuzufügen und zu entfernen. Ermöglicht zudem die Konfiguration der Darstellung und von **Toolbox**\-Kategorien.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Ermöglicht Anwendungen, Active\-basierte **Toolbox**\-Steuerelemente zu verwalten, hinzuzufügen und zu entfernen sowie Kategorien und Darstellung der **Toolbox** zu konfigurieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Erweitert die Funktionalität der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> durch die Bereitstellung umfassender Unterstützung für Persistenz und Lokalisierung.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Es gibt bei der Arbeit mit diesen Schnittstellen einige wichtige Punkte zu bedenken:  
  
-   <xref:System.Drawing.Design.IToolboxService> ist nur für VSPackages verfügbar, die auf dem Managed Package Framework basieren.  
  
-   Steuerelemente können der **Toolbox** mit <xref:System.Drawing.Design.IToolboxService> nicht direkt hinzugefügt werden.  
  
-   Ein VSPackage muss entweder <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> verwenden, um Steuerelemente hinzuzufügen, oder das Steuerelement in einen Wrapper\-Steuerelement hosten, das von <xref:System.Windows.Forms.AxHost> abgeleitet wird.  
  
     Visual Studio enthält das `Aximp.exe`\-Tool für die Automatisierung der Einbindung eines ActiveX\-Steuerelements in einem Steuerelement, das von <xref:System.Windows.Forms.AxHost> abgeleitet wird. Weitere Informationen finden Sie unter [Aximp.exe \(Windows Forms ActiveX Control Importer\)](../Topic/Aximp.exe%20\(Windows%20Forms%20ActiveX%20Control%20Importer\).md).  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> sind COM\-basierte Schnittstellen, die über die Interop\-Assemblys verfügbar sind.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> wird von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> abgeleitet und implementiert alle zugehörigen Methoden.  
  
     Objekte erhalten nur eine Instanz von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> wird nicht von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> abgeleitet und implementiert nicht die zugehörigen Methoden.  
  
     Objekte, die Funktionalität in beiden Schnittstellen erfordern, müssen Instanzen beider Schnittstellen von der Umgebung erhalten.  
  
-   Beim Arbeiten mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, werden Informationen über die kanonischen \(nicht lokalisierten\) Namen von Registerkarten von den Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> verarbeitet.  
  
-   Bei Verwendung von <xref:System.Drawing.Design.IToolboxService> entscheidet der implementierende Benutzer über die Verwaltung von lokalisierten Informationen, z. B. von Kategorienamen.  
  
 Verwenden Sie den Einstellungsmechanismus, um für Benutzer das Speichern von **Toolbox**\-Einstellungen zu ermöglichen, auf die von Benutzern über den Befehl **Import\- und Exporteinstellungen** im Menü **Extras** der IDE zugegriffen wird. Weitere Informationen zur Verwendung von Einstellungen finden Sie unter [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md).  
  
## Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)